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

<div id="bkmrk--1"></div><div id="bkmrk--2"></div>## Definition

<div id="bkmrk--3">  
</div>#### &lt;MapImage&gt;

<div id="bkmrk-xml-tag%3A-%3Cmapimage%3E">XML Tag: **&lt;MapImage&gt;**</div><div id="bkmrk-occurrence%3A-multiple">Occurrence: Multiple Allowed, Optional</div><div id="bkmrk-parent%3A-%3Cpage%3E">Parent: **&lt;Page&gt;**</div><div id="bkmrk-description%3A-include">Description: Include a map image on the page.</div>```xml
<MapImage imageScale="2" type="OGCWMS">
```

<div id="bkmrk--4"></div><div id="bkmrk-attributes%3A">Attributes:</div>- **imageScale** value to scale the image size by
- **type** one of **OGCWMS** or **ESRIREST** or **ESRIRESTMAPSERVER** or **INTRAMAPS**

<div id="bkmrk--5">  
</div><div id="bkmrk--6">  
</div>#### &lt;URI&gt;

<div id="bkmrk-xml-tag%3A-%3Curi%3E">XML Tag: **&lt;URI&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmapimage%3E">Parent: **&lt;MapImage&gt;**</div><div id="bkmrk-description%3A-uri-to-">Description: URI to the web service supplying the map image.</div><div id="bkmrk-usage%3A-1">Usage:</div><div id="bkmrk-ogcwms">**OGCWMS**</div>```xml
<URI useProxy="False"><![CDATA[https://data.linz.govt.nz/services;key=dd4308b96a1743a195b4e9044fb70313/wms?service=WMS&version=1.1.1&request=GetMap&layers=layer-50767&format=image/png&srs=EPSG:2193]]></URI>
```

<div id="bkmrk-exclude-these-parame">Exclude these parameters from the URI:</div>- &amp;bbox
- &amp;width
- &amp;height

<div id="bkmrk-usage%3A-2">Usage:</div><div id="bkmrk-esrirest-experimenta">**ESRIREST <span style="color: rgb(224, 62, 45);">*EXPERIMENTAL*</span>**</div><div id="bkmrk-use-esri-rest-images">use ESRI REST ImageServer service for map image (Export Image URL)</div>```xml
<URI useProxy="False"><![CDATA[https://hbmaps.hbrc.govt.nz/arcgis/rest/services/Imagery/Hastings_Urban_Imagery_20142015/ImageServer/exportImage?bboxSR=2193&imageSR=&time=&format=jpgpng&pixelType=U8&noData=&noDataInterpretation=esriNoDataMatchAny&interpolation=+RSP_BilinearInterpolation&compression=&compressionQuality=&bandIds=&mosaicRule=&renderingRule=&f=image]]></URI>
```

<div id="bkmrk-exclude-these-parame-1">Exclude these parameters from the URI:</div>- &amp;bbox
- &amp;size

<div id="bkmrk-usage%3A-3">Usage:</div><div id="bkmrk-esrirestmapserver-ex">**ESRIRESTMAPSERVER** <span style="color: rgb(224, 62, 45);">***EXPERIMENTAL***</span></div><div id="bkmrk-use-esri-rest-mapser">Use ESRI REST MapServer service for map image (Export Map URL)</div><div id="bkmrk--7">  
</div><div id="bkmrk-usage%3A-4">Usage:</div><div id="bkmrk-intramaps">**INTRAMAPS**</div>```xml
<URI useProxy="False"><![CDATA[https://mapping.hdc.govt.nz/IntraMaps80/SpatialEngineWSEmbeddedMaps/getmap.ashx?Project=PropertyMaps&Module=Property&layer=Property%20Data&includeData=false&mapkeys=@datbasekey]]></URI>
```

<div id="bkmrk-exclude-these-parame-2">Exclude these parameters from the URI:</div>- &amp;width
- &amp;height
- &amp;zoom
- &amp;x
- &amp;y

<div id="bkmrk-useproxy-not-impleme"></div><div id="bkmrk--9">  
</div><div id="bkmrk-parameters%3A-%40feature">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--10">  
</div><div id="bkmrk--11">  
</div><div id="bkmrk--12"></div>