# Page - Report Pages - Map Images - Map Features

<div id="bkmrk-map-features-are-dra">Map Features are drawn over the top of the Map Image.</div><div id="bkmrk-">  
</div>### Example XML

<div id="bkmrk--1">  
</div><div id="bkmrk-using-a-ogc-wfs-web-">Using a OGC WFS web service to draw a Map Feature representing the geometry returned.</div><div id="bkmrk--2">  
</div>```xml
      <MapFeatures>
        <MapFeature type="OGCWFS">
        <URI><![CDATA[https://mapstore.whanganui.govt.nz/geoserver/geonode/wfs?service=WFS&version=1.0.0&request=GetFeature&typeName=geonode:property&srsName=EPSG:2193&cql_filter=prop_no=@featurekey]]></URI>


          <Brush alpha="1" red="100" green="100" blue="0"/>
          <Pen alpha="255" red="255" green="0" blue="0" width="2"/>


        </MapFeature>
      </MapFeatures>
```

<div id="bkmrk--5">  
</div><div id="bkmrk-using-a-sql-statemen">Using a SQL Statement to draw a Map Feature representing the geometry returned.</div><div id="bkmrk--6">  
</div>```xml
        <MapFeatures>
            <MapFeature type="SQL">


                <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT geom from property.property WHERE prop_no = '@featurekey']]></SQL>


                <Brush alpha="1" red="100" green="100" blue="0"/>
                <Pen alpha="255" red="255" green="0" blue="0" width="2"/>


            </MapFeature>
        </MapFeatures>
```

<div id="bkmrk-multiple-map-feature">Multiple Map Features</div><div id="bkmrk-%E2%80%A2-sql-statement-to-d">• SQL Statement to draw a Map Feature representing the geometry returned.</div><div id="bkmrk-%E2%80%A2-draw-a-map-feature">• Draw a Map Feature Image using the location returned by SQL Statement.</div><div id="bkmrk-%E2%80%A2-draw-a-map-feature-1">• Draw a Map Feature Ellipse (5x5 circle) using the location returned by SQL Statement.</div><div id="bkmrk--11">  
</div>```xml
        <MapFeatures>


            <MapFeature type="SQL">
                <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT geom from property.property WHERE prop_no = '@featurekey']]></SQL>
                <Brush alpha="1" red="100" green="100" blue="0"/>
                <Pen alpha="255" red="0" green="0" blue="0" width="2"/>
            </MapFeature>


            <MapFeature type="ignore">
                <Brush alpha="200" red="0" green="100" blue="255"/>
                <Pen alpha="255" red="0" green="255" blue="0" width="2"/>
                <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT fid, prop_no, ST_Centroid(ST_Envelope(geom)) FROM property.property WHERE prop_no='@featurekey']]></SQL>
                <Draw type="Image" image="/data/georeports-data/images/House-04.png" width="10" height="10" alpha="255" offsetX="0" offsetY="0"/>
            </MapFeature>


            <MapFeature type="ignore">
                <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT fid, prop_no, ST_Centroid(ST_Envelope(geom)) FROM property.property WHERE prop_no=@featurekey]]></SQL>
                <Brush alpha="200" red="0" green="100" blue="255"/>
                <Pen alpha="255" red="0" green="255" blue="0" width="2"/>
                <Draw type="Ellipse" width="5" height="5" offsetX="0" offsetY="0"/>
            </MapFeature>


        </MapFeatures>
```

<div id="bkmrk--16">  
</div><div id="bkmrk--17">  
</div>## Definition

<div id="bkmrk--19">  
</div>#### &lt;MapFeatures&gt;

<div id="bkmrk-xml-tag%3A-%3Cmapfeature">XML Tag: **&lt;MapFeatures&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cmapimage%3E">Parent: **&lt;MapImage&gt;**</div><div id="bkmrk-description%3A-contain">Description: Container for Map Features.</div><div id="bkmrk--20"></div><div id="bkmrk--21">  
</div>#### &lt;MapFeature&gt;

<div id="bkmrk-xml-tag%3A-%3Cmapfeature-1">XML Tag: **&lt;MapFeature&gt;**</div><div id="bkmrk-occurrence%3A-multiple">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cmapfeatures">Parent: **&lt;MapFeatures&gt;**</div><div id="bkmrk-description%3A-identif">Description: Identify feature to draw on top of map image.</div>```xml
<MapFeature type="OGCWFS">
```

<div id="bkmrk--3"></div><div id="bkmrk-attributes%3A">Attributes:</div><div id="bkmrk-type-one-of-ogcwfs-o">- type one of **OGCWFS** or **ESRIREST** or **SQL** or **ignore**

</div><div id="bkmrk--23">  
</div><div id="bkmrk--24">  
</div>#### &lt;URI&gt;

<div id="bkmrk-xml-tag%3A-%3Curi%3E">XML Tag: **&lt;URI&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-1">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmapfeature%3E">Parent: **&lt;MapFeature&gt;**</div><div id="bkmrk-description%3A-uri-to-">Description: URI to the web service to identify feature to draw.</div><div id="bkmrk-usage%3A-2">Usage:</div><div id="bkmrk-ogcwfs">**OGCWFS**</div>```xml
<URI useProxy="False"><![CDATA[https://data.linz.govt.nz/services;key=dd4308b96a1743a195b4e9044fb70313/wfs?service=WFS&version=2.0.0&request=GetFeature&typeNames=layer-50823&srsName=EPSG:2193&cql_filter=id=@featurekey]]></URI>
```

<div id="bkmrk--4"></div><div id="bkmrk-usage%3A-3">Usage:</div><div id="bkmrk-esrirest">**ESRIREST**</div>```xml
<URI useProxy="False"><![CDATA[https://hbmaps.hbrc.govt.nz/arcgis/rest/services/WebMaps/PropertySpecial/MapServer/2/query?where=ParcelId%3D@featurekey&text=&objectIds=&time=&geometry=&geometryType=esriGeometryEnvelope&inSR=2193&spatialRel=esriSpatialRelIntersects&relationParam=&outFields=*&returnGeometry=true&returnTrueCurves=false&maxAllowableOffset=&geometryPrecision=&outSR=2193&returnIdsOnly=false&returnCountOnly=false&orderByFields=&groupByFieldsForStatistics=&outStatistics=&returnZ=false&returnM=false&gdbVersion=&returnDistinctValues=false&resultOffset=&resultRecordCount=&queryByDistance=&returnExtentsOnly=false&datumTransformation=&parameterValues=&rangeValues=&f=geojson]]></URI>
```

<div id="bkmrk--7"></div><div id="bkmrk-parameters%3A-%40feature">Parameters: </div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--29">  
</div><div id="bkmrk--30">  
</div>#### &lt;SQL&gt;

<div id="bkmrk-xml-tag%3A-%3Csql%3E">XML Tag: **&lt;SQL&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-2">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmapfeature%3E-1">Parent: **&lt;MapFeature&gt;**</div><div id="bkmrk-description%3A-sql-to-">Description: SQL to identify feature to draw.</div><div id="bkmrk-usage%3A-4">Usage:</div>```xml
<SQL connection="LINZ" ogrDriver="MSSQL:" table="Tables=dbo.nz_primary_land_parcels" dialect="SQLITE"><![CDATA[SELECT id,ogr_geometry as 'GEOMETRY' FROM nz_primary_land_parcels WHERE id=@featurekey]]></SQL>
```

<div id="bkmrk--8"></div><div id="bkmrk-attributes%3A-1">Attributes:</div>- **connection** Name of the SQL Connection to use (as defined in web.config)
- **ogrDriver** GDAL OGR Driver prefix to use (e.g. “MSSQL:” or “PG:”)
- **table** Database table to connect to (e.g. “tables=schema.tablename”)
- **dialect** SQL dialect to use (leave blank for native database SQL dialect)

<div id="bkmrk-parameters%3A-%40feature-1">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--33">  
</div><div id="bkmrk--35"></div>#### &lt;Brush&gt;

<div id="bkmrk-xml-tag%3A-%3Cbrush%3E">XML Tag: **&lt;Brush&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-3">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cmapfeature%3E-2">Parent: **&lt;MapFeature&gt;**</div><div id="bkmrk-description%3A-default">Description: default colours for brush.</div>```xml
<Brush alpha="200" red="0" green="100" blue="255"/>
```

<div id="bkmrk--9"></div><div id="bkmrk-attributes%3A-2">Attributes:</div>- **alpha** Value 0 to 255 for colour alpha channel
- **red** Value 0 to 255 for colour red channel
- **green** Value 0 to 255 for colour green channel
- **blue** Value 0 to 255 for colour blue channel

<div id="bkmrk--37">  
</div>#### &lt;Pen&gt;

<div id="bkmrk-xml-tag%3A-%3Cpen%3E">XML Tag: **&lt;Pen&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-4">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cmapfeature%3E-3">Parent: **&lt;MapFeature&gt;**</div><div id="bkmrk-description%3A-default-1">Description: default colours for pen.</div>```xml
<Pen alpha="255" red="0" green="255" blue="0" width="2"/>
```

<div id="bkmrk--10"></div><div id="bkmrk-attributes%3A-3">Attributes:</div>- **alpha** Value 0 to 255 for colour alpha channel
- **red** Value 0 to 255 for colour red channel
- **green** Value 0 to 255 for colour green channel
- **blue** Value 0 to 255 for colour blue channel
- **width** Value for pen width

<div id="bkmrk--40">  
</div>#### &lt;Draw&gt;

<div id="bkmrk-xml-tag%3A-%3Cdraw%3E">XML Tag: **&lt;Draw&gt;**</div><div id="bkmrk-occurrence%3A-multiple-1">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cmapfeature%3E-4">Parent: **&lt;MapFeature&gt;**</div><div id="bkmrk-description%3A-setting">Description: Settings to draw a feature on top of the map image.</div><div id="bkmrk-usage%3A-7">Usage:</div><div id="bkmrk-ellipse">**Ellipse**</div>```xml
<Draw type="Ellipse" width="10" height="10" offsetX="0" offsetY="0">
```

<div id="bkmrk-ellipse-attributes%3A">Ellipse attributes:</div>- **type** Ellipse (draws a simple ellipse or circle)
- **width** width value in mm
- **height** height value in mm
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)

<div id="bkmrk-usage%3A-8">Usage:</div><div id="bkmrk-rectangle">**Rectangle**</div>```xml
<Draw type="Rectangle" width="40" height="20" offsetX="10" offsetY="-15">
```

<div id="bkmrk-rectangle-attributes">Rectangle attributes:</div>- **type** Rectangle (draws a simple rectangle or square)
- **width** width value in mm
- **height** height value in mm
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)

<div id="bkmrk-usage%3A-9">Usage:</div><div id="bkmrk-image">**Image**</div>```xml
<Draw type="Image" image="images/House-04.png" width="10" height="10" alpha="255" offsetX="0" offsetY="0"/>
```

<div id="bkmrk-image-attributes%3A">Image attributes:</div>- **type** Image (draws an image)
- **image** filename and path to image (local system only)
- **width** width value in mm
- **height** height value in mm
- **alpha** Value 0 to 255 for colour alpha channel of the image
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)

<div id="bkmrk-usage%3A-10">Usage:</div><div id="bkmrk-string">**String**</div>```xml
<Draw type="String" text="Static Text&#xA;@0&#xA;@1&#xA;@featurekey" width="40" height="40" fontFamily="Arial" fontSize="12" fontStyle="Bold" red="0" green="0" blue="255" alignment="Center" offsetX="10" offsetY="-5"/>
```

<div id="bkmrk-string-attributes%3A">String attributes:</div>- **type** String (draws text string)
- **text** text string to draw (See parameters below for possible replacements)
- **width** width value in mm
- **height** height value in mm
- **fontFamily** name of the font to be used (must exist on server)
- **fontSize** font size in pts
- **fontStyle** one of Regular (default), Bold, Italic, or BoldItalic
- **red** Value 0 to 255 for colour red channel
- **green** Value 0 to 255 for colour green channel
- **blue** Value 0 to 255 for colour blue channel
- **alignment** one of Center (default), Left, or Right
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)

<div id="bkmrk-parameters%3A-%40feature-2">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL
- **&amp;#xA;** Replaced with a Line Feed hex entity  
    (other hex entities can be used as well)
- **@0, @1… @n** Replaced with column value by index (0 indexed)

<div id="bkmrk--47">  
</div><div id="bkmrk--48">  
</div><div id="bkmrk--49">  
</div><div id="bkmrk--50"></div>