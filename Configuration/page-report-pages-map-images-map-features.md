# Page - Report Pages - Map Images - Map Features

Map Features are drawn over the top of the Map Image.



### Example XML

Using a OGC WFS web service to draw a Map Feature representing the geometry returned.

```xml
      <MapFeatures>
        <MapFeature type="OGCWFS">
        <URI><![CDATA[https://mapstore.whanganui.govt.nz/geoserver/geonode/wfs?service=WFS&version=1.0.0&request=GetFeature&typeName=geonode:property&srsName=EPSG:2193&cql_filter=prop_no=@featurekey]]></URI>


          <Brush alpha="1" red="100" green="100" blue="0"/>
          <Pen alpha="255" red="255" green="0" blue="0" width="2"/>


        </MapFeature>
      </MapFeatures>
```

Using a SQL Statement to draw a Map Feature representing the geometry returned.

```xml
        <MapFeatures>
            <MapFeature type="SQL">


                <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT geom from property.property WHERE prop_no = '@featurekey']]></SQL>


                <Brush alpha="1" red="100" green="100" blue="0"/>
                <Pen alpha="255" red="255" green="0" blue="0" width="2"/>


            </MapFeature>
        </MapFeatures>
```

Multiple Map Features
- SQL Statement to draw a Map Feature representing the geometry returned.
- Draw a Map Feature Image using the location returned by SQL Statement.
- Draw a Map Feature Ellipse (5x5 circle) using the location returned by SQL Statement.

```xml
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


## Definition

#### &lt;MapFeatures&gt;

XML Tag: **&lt;MapFeatures&gt;**

Occurrence: Once only, Optional

Parent: **&lt;MapImage&gt;**

Description: Container for Map Features.

---

#### &lt;MapFeature&gt;

XML Tag: **&lt;MapFeature&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;MapFeatures&gt;**

Description: Identify feature to draw on top of map image.

```xml
<MapFeature type="OGCWFS">
```

Attributes:
- type one of **OGCWFS** or **ESRIREST** or **SQL** or **ignore**

---

#### &lt;URI&gt;

XML Tag: **&lt;URI&gt;**

Occurrence: Once only, Required

Parent: **&lt;MapFeature&gt;**

Description: URI to the web service to identify feature to draw.

Usage:
**OGCWFS**
```xml
<URI useProxy="False"><![CDATA[https://data.linz.govt.nz/services;key=dd4308b96a1743a195b4e9044fb70313/wfs?service=WFS&version=2.0.0&request=GetFeature&typeNames=layer-50823&srsName=EPSG:2193&cql_filter=id=@featurekey]]></URI>
```


Usage:
**ESRIREST**
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

Parent: **&lt;MapFeature&gt;**

Description: SQL to identify feature to draw.

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

#### &lt;Brush&gt;

XML Tag: **&lt;Brush&gt;**

Occurrence: Once only, Optional

Parent: **&lt;MapFeature&gt;**

Description: default colours for brush.

```xml
<Brush alpha="200" red="0" green="100" blue="255"/>
```

Attributes:
- **alpha** Value 0 to 255 for colour alpha channel
- **red** Value 0 to 255 for colour red channel
- **green** Value 0 to 255 for colour green channel
- **blue** Value 0 to 255 for colour blue channel

---

#### &lt;Pen&gt;

XML Tag: **&lt;Pen&gt;**

Occurrence: Once only, Optional

Parent: **&lt;MapFeature&gt;**

Description: default colours for pen.

```xml
<Pen alpha="255" red="0" green="255" blue="0" width="2"/>
```

Attributes:
- **alpha** Value 0 to 255 for colour alpha channel
- **red** Value 0 to 255 for colour red channel
- **green** Value 0 to 255 for colour green channel
- **blue** Value 0 to 255 for colour blue channel
- **width** Value for pen width

---

#### &lt;Draw&gt;

XML Tag: **&lt;Draw&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;MapFeature&gt;**

Description: Settings to draw a feature on top of the map image.

Usage:
**Ellipse**
```xml
<Draw type="Ellipse" width="10" height="10" offsetX="0" offsetY="0">
```

Ellipse attributes:
- **type** Ellipse (draws a simple ellipse or circle)
- **width** width value in mm
- **height** height value in mm
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)


Usage:
**Rectangle**
```xml
<Draw type="Rectangle" width="40" height="20" offsetX="10" offsetY="-15">
```

Rectangle attributes:
- **type** Rectangle (draws a simple rectangle or square)
- **width** width value in mm
- **height** height value in mm
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)


Usage:
**Image**
```xml
<Draw type="Image" image="images/House-04.png" width="10" height="10" alpha="255" offsetX="0" offsetY="0"/>
```


Image attributes:
- **type** Image (draws an image)
- **image** filename and path to image (local system only)
- **width** width value in mm
- **height** height value in mm
- **alpha** Value 0 to 255 for colour alpha channel of the image
- **offsetX** offset along x in mm (negative values allowed)
- **offsetY** offset along y in mm (negative values allowed)


Usage:
**String**
```xml
<Draw type="String" text="Static Text&#xA;@0&#xA;@1&#xA;@featurekey" width="40" height="40" fontFamily="Arial" fontSize="12" fontStyle="Bold" red="0" green="0" blue="255" alignment="Center" offsetX="10" offsetY="-5"/>
```


String attributes:
- **type** String (draws text string)
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


Parameters:
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL
- **&amp;#xA;** Replaced with a Line Feed hex entity  
    (other hex entities can be used as well)
- **@0, @1… @n** Replaced with column value by index (0 indexed)
