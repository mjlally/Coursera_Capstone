# Coursera Capstone Project
## Car Collision Severity Forecast

### Introduction:

Weather conditions, road layout and high volumes of traffic can increase the risk of car accidents. This can result in death, injury, and financial loss for those directly involved in a collision, but also huge delays and inconvenience for those travelling behind a vehicle which ends up in a collision.

Can we avoid being caught up in or behind a collision due to conditions known to increase the risk of collisions? Can we use machine learning to forecast the risk of collisions on a given route based on existing conditions, and from this have the option to take a different route or travel at a different time? Even if we cannot avoid the route, would a forecast of collision probability encourage safer driving, or be used alongside variable speed limits to make conditions safer? In this project, available collision data will be explored with a view to using machine learning to forecast the probability of an accident given traffic (subject to finding available historical traffic data which overlaps times and locations of collisions data) and weather conditions for a given route.

Initially the SDOT Collision data will be used to explore the relationships between various features and collision severity, and see whether a good enough model can be made to reliably forecast collisions. Once this is done, other data sources will be explored and tested.

### Data
The SDOT Collision data is a record collision data including details of each collision along with data on road conditions etc.. There are missing values in some columns and not all data is useful for the forecast, for example, whether or not the driver of a car was under the influence of alcohol might not be useful input for the model, although given the increased likelihood of alcohol consumption at certain times of day, week, month, year, it would be unwise to drop this column without at least a brief exploratory data analysis.

The column headers and first five rows of the data set are shown below


```python
collisions_df.columns

```
    Index(['SEVERITYCODE', 'X', 'Y', 'OBJECTID', 'INCKEY', 'COLDETKEY', 'REPORTNO',
           'STATUS', 'ADDRTYPE', 'INTKEY', 'LOCATION', 'EXCEPTRSNCODE',
           'EXCEPTRSNDESC', 'SEVERITYCODE.1', 'SEVERITYDESC', 'COLLISIONTYPE',
           'PERSONCOUNT', 'PEDCOUNT', 'PEDCYLCOUNT', 'VEHCOUNT', 'INCDATE',
           'INCDTTM', 'JUNCTIONTYPE', 'SDOT_COLCODE', 'SDOT_COLDESC',
           'INATTENTIONIND', 'UNDERINFL', 'WEATHER', 'ROADCOND', 'LIGHTCOND',
           'PEDROWNOTGRNT', 'SDOTCOLNUM', 'SPEEDING', 'ST_COLCODE', 'ST_COLDESC',
           'SEGLANEKEY', 'CROSSWALKKEY', 'HITPARKEDCAR'],
          dtype='object')

```python

```python
collisions_df.head()

```
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SEVERITYCODE</th>
      <th>X</th>
      <th>Y</th>
      <th>OBJECTID</th>
      <th>INCKEY</th>
      <th>COLDETKEY</th>
      <th>REPORTNO</th>
      <th>STATUS</th>
      <th>ADDRTYPE</th>
      <th>INTKEY</th>
      <th>...</th>
      <th>ROADCOND</th>
      <th>LIGHTCOND</th>
      <th>PEDROWNOTGRNT</th>
      <th>SDOTCOLNUM</th>
      <th>SPEEDING</th>
      <th>ST_COLCODE</th>
      <th>ST_COLDESC</th>
      <th>SEGLANEKEY</th>
      <th>CROSSWALKKEY</th>
      <th>HITPARKEDCAR</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>-122.323148</td>
      <td>47.703140</td>
      <td>1</td>
      <td>1307</td>
      <td>1307</td>
      <td>3502005</td>
      <td>Matched</td>
      <td>Intersection</td>
      <td>37475.0</td>
      <td>...</td>
      <td>Wet</td>
      <td>Daylight</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10</td>
      <td>Entering at angle</td>
      <td>0</td>
      <td>0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>-122.347294</td>
      <td>47.647172</td>
      <td>2</td>
      <td>52200</td>
      <td>52200</td>
      <td>2607959</td>
      <td>Matched</td>
      <td>Block</td>
      <td>NaN</td>
      <td>...</td>
      <td>Wet</td>
      <td>Dark - Street Lights On</td>
      <td>NaN</td>
      <td>6354039.0</td>
      <td>NaN</td>
      <td>11</td>
      <td>From same direction - both going straight - bo...</td>
      <td>0</td>
      <td>0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>-122.334540</td>
      <td>47.607871</td>
      <td>3</td>
      <td>26700</td>
      <td>26700</td>
      <td>1482393</td>
      <td>Matched</td>
      <td>Block</td>
      <td>NaN</td>
      <td>...</td>
      <td>Dry</td>
      <td>Daylight</td>
      <td>NaN</td>
      <td>4323031.0</td>
      <td>NaN</td>
      <td>32</td>
      <td>One parked--one moving</td>
      <td>0</td>
      <td>0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>-122.334803</td>
      <td>47.604803</td>
      <td>4</td>
      <td>1144</td>
      <td>1144</td>
      <td>3503937</td>
      <td>Matched</td>
      <td>Block</td>
      <td>NaN</td>
      <td>...</td>
      <td>Dry</td>
      <td>Daylight</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23</td>
      <td>From same direction - all others</td>
      <td>0</td>
      <td>0</td>
      <td>N</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>-122.306426</td>
      <td>47.545739</td>
      <td>5</td>
      <td>17700</td>
      <td>17700</td>
      <td>1807429</td>
      <td>Matched</td>
      <td>Intersection</td>
      <td>34387.0</td>
      <td>...</td>
      <td>Wet</td>
      <td>Daylight</td>
      <td>NaN</td>
      <td>4028032.0</td>
      <td>NaN</td>
      <td>10</td>
      <td>Entering at angle</td>
      <td>0</td>
      <td>0</td>
      <td>N</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 38 columns</p>
</div>



An exploratory data analysis will be performed on the data to see which features might be most useful for the model, which can be dropped and which need further preparation before use. Folllowing this a number of machine learning algorithms will be used to model the collision risk and each algorithm evaluated and compared with the rest.
