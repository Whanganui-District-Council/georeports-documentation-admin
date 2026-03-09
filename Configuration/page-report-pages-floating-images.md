# Page - Report Pages - Floating Images

### Example XML

Draw Legend Images from WMS Web Service

```xml
<FloatingImages>

  <FloatingImage type="URI" x="10" y="202" multiplier="0.6">

    <URI><![CDATA[https://data.whanganui.govt.nz/geoserver/wms?service=WMS&request=GetLegendGraphic&format=image%2Fpng&height=24&width=24&layer=geonode%3Aassetfinda_water&style=&version=1.3.0&SLD_VERSION=1.1.0&LEGEND_OPTIONS=forceLabels%3Aon%3BfontSize%3A12%3BfontAntiAliasing%3Atrue%3bforceTitles%3aoff&SCALE=4514]]></URI>

  </FloatingImage>
  
  <FloatingImage type="URI" x="80" y="202" multiplier="0.6">

    <URI><![CDATA[https://data.whanganui.govt.nz/geoserver/wms?service=WMS&request=GetLegendGraphic&format=image%2Fpng&height=24&width=24&layer=geonode%3Aassetfinda_stormwater&style=&version=1.3.0&SLD_VERSION=1.1.0&LEGEND_OPTIONS=forceLabels%3Aon%3BfontSize%3A12%3BfontAntiAliasing%3Atrue%3bforceTitles%3aoff&SCALE=4514]]></URI>

  </FloatingImage>

  <FloatingImage type="URI" x="150" y="202" multiplier="0.6">

    <URI><![CDATA[https://data.whanganui.govt.nz/geoserver/wms?service=WMS&request=GetLegendGraphic&format=image%2Fpng&height=24&width=24&layer=geonode%3Aassetfinda_wastewater&style=&version=1.3.0&SLD_VERSION=1.1.0&LEGEND_OPTIONS=forceLabels%3Aon%3BfontSize%3A12%3BfontAntiAliasing%3Atrue%3bforceTitles%3aoff&SCALE=4514]]></URI>

  </FloatingImage>

</FloatingImages>
```

## Definition

#### &lt;FloatingImages&gt;

XML Tag: **&lt;FloatingImages&gt;**  
Occurrence: Once only, Optional  
Parent: **&lt;Page&gt;**  
Description: Container for Floating Images.

####   
&lt;FloatingImage&gt;

XML Tag: **&lt;FloatingImage&gt;**  
Occurrence: Multiple Allowed, Optional  
Parent: **&lt;FloatingImages&gt;**  
Description: Include an image on the page determined by type, position and multiplier to scale image

Usage (URI):

```xml
<FloatingImage x="10" y="50" multiplier="0.5" type="URI">
```

Usage (FILE):

```xml
<FloatingImage x="10" y="50" multiplier="0.5" type="FILE" file="/path/filename.ext">
```

Attributes:

- **x** Position in mm across the page from the left-hand edge.
- **y** Position in mm down the page from the top edge.
- **multiplier** value to scale the image size by
- **type** one of FILE or URI
- **file** If type=”FILE”, the local path and filename to the image

####   
&lt;URI&gt;

XML Tag: **&lt;URI&gt;**  
Occurrence: Once only, Required  
Parent: **&lt;FloatingImage&gt;**  
Description: URI to the web service supplying the floating image.

Usage:

```xml
<URI><![CDATA[https://domain/path/image.png]]></URI>
```