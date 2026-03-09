# Page - Report Pages - Map Images - Scale

### Example XML

Using a OGC WFS web service to retrieve the feature geometry to use to calculate the scale

```xml
<ScaleFeature type="OGCWFS" multiplier="5">
  <URI><![CDATA[https://data.whanganui.govt.nz/geoserver/geonode/wfs?service=WFS&version=1.0.0&request=GetFeature&typeName=geonode:property&srsName=EPSG:2193&cql_filter=prop_no=@featurekey]]></URI>
</ScaleFeature>


<ScaleRanges>
  <ScaleRange min="0" max="25000">25000</ScaleRange>
  <ScaleRange min="25000" max="50000">50000</ScaleRange>
  <ScaleRange min="50000" max="100000">100000</ScaleRange>
  <ScaleRange min="100000" max="150000">150000</ScaleRange>
  <ScaleRange min="150000" max="200000">200000</ScaleRange>
  <ScaleRange min="200000" max="250000">250000</ScaleRange>
  <ScaleRange min="250000" max="500000">500000</ScaleRange>
  <ScaleRange min="500000" max="50000000">500000</ScaleRange>
</ScaleRanges>
```

Using a SQL Statement to retrieve the feature geometry to use to calculate the scale

```xml
<ScaleFeature type="SQL" multiplier="1.1">
  <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT prop_no,ST_Envelope(geom) as geom from property.property WHERE prop_no = '@featurekey'
]]></SQL>
</ScaleFeature>
<ScaleRanges>
  <ScaleRange min="0" max="500">500</ScaleRange>
  <ScaleRange min="500" max="1000">1000</ScaleRange>
  <ScaleRange min="1000" max="2000">2000</ScaleRange>
  <ScaleRange min="2000" max="2500">2500</ScaleRange>
  <ScaleRange min="2500" max="3000">3000</ScaleRange>
  <ScaleRange min="3000" max="5000">5000</ScaleRange>
  <ScaleRange min="5000" max="10000">10000</ScaleRange>
  <ScaleRange min="10000" max="20000">20000</ScaleRange>
  <ScaleRange min="20000" max="25000">25000</ScaleRange>
  <ScaleRange min="25000" max="50000">50000</ScaleRange>
  <ScaleRange min="50000" max="100000">100000</ScaleRange>
  <ScaleRange min="100000" max="150000">150000</ScaleRange>
  <ScaleRange min="150000" max="200000">200000</ScaleRange>
  <ScaleRange min="200000" max="250000">250000</ScaleRange>
  <ScaleRange min="250000" max="500000">500000</ScaleRange>
  <ScaleRange min="500000" max="50000000">500000</ScaleRange>
</ScaleRanges>
```

## Definition


#### &lt;ScaleFeature&gt;

XML Tag: **&lt;ScaleFeature&gt;**

Occurrence: Once only, Required

Parent: **&lt;MapImage&gt;**

Description: Identify feature to base scale on.

```xml
<ScaleFeature type="OGCWFS" multiplier="2">
```


Attributes:
- **multiplier** value to allow for adjusting feature scale
- **type** one of **OGCWFS** or **OGRGEOJSON** or **ESRIREST** or **SQL**

---

#### &lt;URI&gt;

XML Tag: **&lt;URI&gt;**

Occurrence: Once only, Required

Parent: **&lt;ScaleFeature&gt;**

Description: URI to the web service to identify feature to base scale on.

Usage:
**OGCWFS**
```xml
<URI useProxy="False"><![CDATA[https://data.linz.govt.nz/services;key=dd4308b96a1743a195b4e9044fb70313/wfs?service=WFS&version=2.0.0&request=GetFeature&typeNames=layer-50823&srsName=EPSG:2193&cql_filter=id=@featurekey]]></URI>
```


Usage:
**ESRIREST** or **OGRGEOJSON**
```xml
<URI useProxy="False"><![CDATA[https://hbmaps.hbrc.govt.nz/arcgis/rest/services/WebMaps/PropertySpecial/MapServer/2/query?where=ParcelId%3D@featurekey&text=&objectIds=&time=&geometry=&geometryType=esriGeometryEnvelope&inSR=2193&spatialRel=esriSpatialRelIntersects&relationParam=&outFields=*&returnGeometry=true&returnTrueCurves=false&maxAllowableOffset=&geometryPrecision=&outSR=2193&returnIdsOnly=false&returnCountOnly=false&orderByFields=&groupByFieldsForStatistics=&outStatistics=&returnZ=false&returnM=false&gdbVersion=&returnDistinctValues=false&resultOffset=&resultRecordCount=&queryByDistance=&returnExtentsOnly=false&datumTransformation=&parameterValues=&rangeValues=&f=geojson]]></URI>
```


Parameters: 
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

---

#### &lt;SQL&gt;

XML Tag: **&lt;SQL&gt;**

Occurrence: Once only, Required

Parent: **&lt;ScaleFeature&gt;**

Description: SQL to identify feature to base scale on.

Usage:
```xml
<SQL connection="LINZ" ogrDriver="MSSQL:" table="Tables=dbo.nz_primary_land_parcels" dialect="SQLITE"><![CDATA[SELECT id,ogr_geometry as 'GEOMETRY' FROM nz_primary_land_parcels WHERE id=@featurekey]]></SQL>
```

Attributes:
- **connection** Name of the SQL Connection to use (as defined in web.config)
- **ogrDriver** GDAL OGR Driver prefix to use (e.g. “MSSQL:” or “PG:”)
- **table** Database table to connect to (e.g. “tables=schema.tablename”)
- **dialect** SQL dialect to use (leave blank for native database SQL dialect)


Parameters: 
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

---

#### &lt;ScaleRanges&gt;

XML Tag: **&lt;ScaleRanges&gt;**

Occurrence: Once only, Required

Parent: **&lt;MapImage&gt;**

Description: Container for ScaleRange values.

---

#### &lt;ScaleRange&gt;

XML Tag: **&lt;ScaleRange&gt;**

Occurrence: Multiple allowed, Required

Parent: **&lt;ScaleRanges&gt;**

Description: Scale range values defined by min and max values.

Usage:

```xml
<ScaleRange min="0" max="2500">2500</ScaleRange>
<ScaleRange min="2500" max="3000">3000</ScaleRange>
<ScaleRange min="3000" max="5000">5000</ScaleRange>
```


Attributes:
- **min** minimum feature scale value for this scale range
- **max** maximum feature scale value for this scale range
