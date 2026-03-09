# Page - Report Pages - Map Images

### Example XML

- Use a WMS Web Service to retrieve the map image
- Use a WFS Web Service to retrieve the feature geometry to use to calculate the scale
- Use a WFS Web Service to retrieve the feature geometry to draw over the map image to highlight the map feature

```xml
<MapImage imageScale="2" type="OGCWMS">
        <URI><![CDATA[https://data.whanganui.govt.nz/geoserver/geonode/wms?service=WMS&version=1.1.0&request=GetMap&layers=geonode:rots_overview_map&styles=&srs=EPSG:2193&format=image%2Fpng]]></URI>


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


          <MapFeatures>
            <MapFeature type="OGCWFS">
                <URI><![CDATA[https://data.whanganui.govt.nz/geoserver/geonode/wfs?service=WFS&version=1.0.0&request=GetFeature&typeName=geonode:property&srsName=EPSG:2193&cql_filter=prop_no=@featurekey]]></URI>
                <Brush alpha="1" red="100" green="100" blue="0"/>
                <Pen alpha="255" red="255" green="0" blue="0" width="2"/>
            </MapFeature>
          </MapFeatures>


</MapImage>
```

## Definition

#### &lt;MapImage&gt;

XML Tag: **&lt;MapImage&gt;**

Occurrence: Multiple Allowed, Optional

Parent: **&lt;Page&gt;**

Description: Include a map image on the page.

```xml
<MapImage imageScale="2" type="OGCWMS">
```

Attributes:
- **imageScale** value to scale the image size by
- **type** one of **OGCWMS** or **ESRIREST** or **ESRIRESTMAPSERVER** or **INTRAMAPS**

---

#### &lt;URI&gt;

XML Tag: **&lt;URI&gt;**

Occurrence: Once only, Required

Parent: **&lt;MapImage&gt;**

Description: URI to the web service supplying the map image.

Usage:
**OGCWMS**
```xml
<URI useProxy="False"><![CDATA[https://data.linz.govt.nz/services;key=dd4308b96a1743a195b4e9044fb70313/wms?service=WMS&version=1.1.1&request=GetMap&layers=layer-50767&format=image/png&srs=EPSG:2193]]></URI>
```

Exclude these parameters from the URI:
- &amp;bbox
- &amp;width
- &amp;height

Usage:

**ESRIREST <span style="color: rgb(224, 62, 45);">*EXPERIMENTAL*</span>**

use ESRI REST ImageServer service for map image (Export Image URL)
```xml
<URI useProxy="False"><![CDATA[https://hbmaps.hbrc.govt.nz/arcgis/rest/services/Imagery/Hastings_Urban_Imagery_20142015/ImageServer/exportImage?bboxSR=2193&imageSR=&time=&format=jpgpng&pixelType=U8&noData=&noDataInterpretation=esriNoDataMatchAny&interpolation=+RSP_BilinearInterpolation&compression=&compressionQuality=&bandIds=&mosaicRule=&renderingRule=&f=image]]></URI>
```


Exclude these parameters from the URI:
- &amp;bbox
- &amp;size


Usage:

**ESRIRESTMAPSERVER** <span style="color: rgb(224, 62, 45);">***EXPERIMENTAL***</span>

Use ESRI REST MapServer service for map image (Export Map URL)

Usage:

**INTRAMAPS**

```xml
<URI useProxy="False"><![CDATA[https://mapping.hdc.govt.nz/IntraMaps80/SpatialEngineWSEmbeddedMaps/getmap.ashx?Project=PropertyMaps&Module=Property&layer=Property%20Data&includeData=false&mapkeys=@datbasekey]]></URI>
```


Exclude these parameters from the URI:
- &amp;width
- &amp;height
- &amp;zoom
- &amp;x
- &amp;y


Parameters:
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL
