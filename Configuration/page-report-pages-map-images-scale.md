# Page - Report Pages - Map Images - Scale

### Example XML

<div id="bkmrk-">  
</div><div id="bkmrk-using-a-ogc-wfs-web-">Using a OGC WFS web service to retrieve the feature geometry to use to calculate the scale</div><div id="bkmrk-%C2%A0-%C2%A0-%C2%A0-%C2%A0%C2%A0"> </div>```xml
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

<div id="bkmrk-%C2%A0-%C2%A0-%C2%A0-%C2%A0-%3Cscalefeatur"></div><div id="bkmrk--3">  
</div><div id="bkmrk-using-a-sql-statemen">Using a SQL Statement to retrieve the feature geometry to use to calculate the scale</div><div id="bkmrk--4">  
</div>```xml
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

<div id="bkmrk--5">  
</div>## Definition

<div id="bkmrk--7">  
</div>#### &lt;ScaleFeature&gt;

<div id="bkmrk-xml-tag%3A-%3Cscalefeatu">XML Tag: **&lt;ScaleFeature&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmapimage%3E">Parent: **&lt;MapImage&gt;**</div><div id="bkmrk-description%3A-identif">Description: Identify feature to base scale on.</div>```xml
<ScaleFeature type="OGCWFS" multiplier="2">
```

<div id="bkmrk--1"></div><div id="bkmrk-attributes%3A">Attributes:</div>- **multiplier** value to allow for adjusting feature scale
- **type** one of **OGCWFS** or **OGRGEOJSON** or **ESRIREST** or **SQL**

<div id="bkmrk--10">  
</div>#### &lt;URI&gt;

<div id="bkmrk-xml-tag%3A-%3Curi%3E">XML Tag: **&lt;URI&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-1">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cscalefeatur">Parent: **&lt;ScaleFeature&gt;**</div><div id="bkmrk-description%3A-uri-to-">Description: URI to the web service to identify feature to base scale on.</div><div id="bkmrk--11">  
</div><div id="bkmrk-usage%3A-1">Usage:</div><div id="bkmrk-ogcwfs">**OGCWFS**</div>```xml
<URI useProxy="False"><![CDATA[https://data.linz.govt.nz/services;key=dd4308b96a1743a195b4e9044fb70313/wfs?service=WFS&version=2.0.0&request=GetFeature&typeNames=layer-50823&srsName=EPSG:2193&cql_filter=id=@featurekey]]></URI>
```

<div id="bkmrk--2"></div><div id="bkmrk-usage%3A-2">Usage:</div><div id="bkmrk-esrirest-or-ogrgeojs">**ESRIREST** or **OGRGEOJSON**</div>```xml
<URI useProxy="False"><![CDATA[https://hbmaps.hbrc.govt.nz/arcgis/rest/services/WebMaps/PropertySpecial/MapServer/2/query?where=ParcelId%3D@featurekey&text=&objectIds=&time=&geometry=&geometryType=esriGeometryEnvelope&inSR=2193&spatialRel=esriSpatialRelIntersects&relationParam=&outFields=*&returnGeometry=true&returnTrueCurves=false&maxAllowableOffset=&geometryPrecision=&outSR=2193&returnIdsOnly=false&returnCountOnly=false&orderByFields=&groupByFieldsForStatistics=&outStatistics=&returnZ=false&returnM=false&gdbVersion=&returnDistinctValues=false&resultOffset=&resultRecordCount=&queryByDistance=&returnExtentsOnly=false&datumTransformation=&parameterValues=&rangeValues=&f=geojson]]></URI>
```

<div id="bkmrk--8"></div><div id="bkmrk-parameters%3A-%40feature">Parameters: </div><div id="bkmrk-%40featurekey-replaced">**@featurekey** Replaced with Feature key value from launch URL</div><div id="bkmrk-%40databasekey-replace">**@databasekey** Replaced with Database key value from launch URL</div><div id="bkmrk-%40referencekey-replac">**@referencekey** Replaced with Reference key value from launch URL</div><div id="bkmrk--15">  
</div><div id="bkmrk--16">  
</div><div id="bkmrk--17">  
</div>#### &lt;SQL&gt;

<div id="bkmrk-xml-tag%3A-%3Csql%3E">XML Tag: **&lt;SQL&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-2">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cscalefeatur-1">Parent: **&lt;ScaleFeature&gt;**</div><div id="bkmrk-description%3A-sql-to-">Description: SQL to identify feature to base scale on.</div><div id="bkmrk-usage%3A-3">Usage:</div>```xml
<SQL connection="LINZ" ogrDriver="MSSQL:" table="Tables=dbo.nz_primary_land_parcels" dialect="SQLITE"><![CDATA[SELECT id,ogr_geometry as 'GEOMETRY' FROM nz_primary_land_parcels WHERE id=@featurekey]]></SQL>
```

<div id="bkmrk--9"></div><div id="bkmrk-attributes%3A-1">Attributes:</div>- **connection** Name of the SQL Connection to use (as defined in web.config)
- **ogrDriver** GDAL OGR Driver prefix to use (e.g. “MSSQL:” or “PG:”)
- **table** Database table to connect to (e.g. “tables=schema.tablename”)
- **dialect** SQL dialect to use (leave blank for native database SQL dialect)

<div id="bkmrk-parameters%3A-%40feature-1">Parameters: </div><div id="bkmrk-%40featurekey-replaced-1">**@featurekey** Replaced with Feature key value from launch URL</div><div id="bkmrk-%40databasekey-replace-1">**@databasekey** Replaced with Database key value from launch URL</div><div id="bkmrk-%40referencekey-replac-1">**@referencekey** Replaced with Reference key value from launch URL</div><div id="bkmrk--20">  
</div><div id="bkmrk--21">  
</div><div id="bkmrk--23"></div>#### &lt;ScaleRanges&gt;

<div id="bkmrk-xml-tag%3A-%3Cscalerange">XML Tag: **&lt;ScaleRanges&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-3">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmapimage%3E-1">Parent: **&lt;MapImage&gt;**</div><div id="bkmrk-description%3A-contain">Description: Container for ScaleRange values.</div><div id="bkmrk--24"></div>#### &lt;ScaleRange&gt;

<div id="bkmrk-xml-tag%3A-%3Cscalerange-1">XML Tag: **&lt;ScaleRange&gt;**</div><div id="bkmrk-occurrence%3A-multiple">Occurrence: Multiple allowed, Required</div><div id="bkmrk-parent%3A-%3Cscaleranges">Parent: **&lt;ScaleRanges&gt;**</div><div id="bkmrk-description%3A-scale-r">Description: Scale range values defined by min and max values.</div><div id="bkmrk-usage%3A-5">Usage:</div>```xml
<ScaleRange min="0" max="2500">2500</ScaleRange>
<ScaleRange min="2500" max="3000">3000</ScaleRange>
<ScaleRange min="3000" max="5000">5000</ScaleRange>
```

<div id="bkmrk-attributes%3A-2">Attributes:</div>- **min** minimum feature scale value for this scale range
- **max** maximum feature scale value for this scale range

<div id="bkmrk--28"></div>