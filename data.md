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

