# Settings

The **&lt;Settings&gt;** section of the config file contains settings that relate to the whole PDF Report rather than settings for an individual page in the report.

#### Example XML

```xml
<Settings>
    <QGIS>
      <QPTLayout>
        <SQLConnections>
          <Labels>pgwdcgisodbc</Labels>
          <Images>pgwdcgisodbc</Images>
        </SQLConnections>
      </QPTLayout>
    </QGIS>
    <Output>
      <PDF>
        <Metadata>
          <Title>Sample Report</Title>
          <Author>GeoReports</Author>
          <Subject>Sample Report PDF Document</Subject>
          <Keywords>Map, Property, @featurekey, @databasekey, @referencekey</Keywords>
        </Metadata>
      </PDF>
    </Output>
  </Settings>
```


## Definitions

### &lt;Settings&gt;

XML Tag: **&lt;Settings&gt;**  
Occurrence: Once only, Required  
Parent: **&lt;configuration&gt;**  
Description: Container for report settings

### QGIS Settings

QGIS Layout templates (.qpt files) are used to XXXXX

#### &lt;QGIS&gt;

<div id="bkmrk-xml-tag%3A-%3Cqgis%3E">XML Tag: **&lt;QGIS&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Csettings%3E">Parent: **&lt;Settings&gt;**</div><div id="bkmrk-description%3A-contain">Description: Container for QGIS related settings</div><div id="bkmrk-">  
</div>#### &lt;QPTLayout&gt;

<div id="bkmrk-xml-tag%3A-%3Cqptlayout%3E">XML Tag: **&lt;QPTLayout&gt;**, Optional</div><div id="bkmrk-occurrence%3A-once-onl-1">Occurrence: Once only</div><div id="bkmrk-parent%3A-%3Cqgis%3E">Parent: **&lt;QGIS&gt;**</div><div id="bkmrk-description%3A-contain-1">Description: Container for QGIS QPT Layout related settings</div><div id="bkmrk--1">  
</div>#### &lt;SQLConnections&gt;

<div id="bkmrk-xml-tag%3A-%3Csqlconnect">XML Tag: **&lt;SQLConnections&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-2">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cqptlayout%3E">Parent: **&lt;QPTLayout&gt;**</div><div id="bkmrk-description%3A-contain-2">Description: Container for QGIS QPT Layout SQL Connection related settings</div><div id="bkmrk--2">  
</div>#### &lt;Labels&gt;

<div id="bkmrk-xml-tag%3A-%3Clabels%3E">XML Tag: **&lt;Labels&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-3">Occurrence: Once only, Optional (Defaults to “Labels” if not present)</div><div id="bkmrk-parent%3A-%3Csqlconnecti">Parent: **&lt;SQLConnections&gt;**</div><div id="bkmrk-description%3A-name-of">Description: Name of the SQL Connection to use for SQL Generated Labels</div>```xml
<Labels>SQLLabels</Labels>
```

<div id="bkmrk--3">  
</div>#### &lt;Images&gt;

<div id="bkmrk-xml-tag%3A-%3Cimages%3E">XML Tag: **&lt;Images&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-4">Occurrence: Once only, Optional (Defaults to “Images” if not present)</div><div id="bkmrk-parent%3A-%3Csqlconnecti-1">Parent: **&lt;SQLConnections&gt;**</div><div id="bkmrk-description%3A-name-of-1">Description: Name of the SQL Connection to use for SQL Generated Images</div>```xml
<Images>SQLImages</Images>
```

<div id="bkmrk--5">  
</div><div id="bkmrk--6">  
</div>### Output Settings

<div id="bkmrk--7">  
</div>#### &lt;Output&gt;

<div id="bkmrk-xml-tag%3A-%3Coutput%3E">XML Tag: **&lt;Output&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-5">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Csettings%3E-1">Parent: **&lt;Settings&gt;**</div><div id="bkmrk-description%3A-contain-3">Description: Container for Output settings</div><div id="bkmrk--8">  
</div>#### &lt;PDF&gt;

<div id="bkmrk-xml-tag%3A-%3Cpdf%3E">XML Tag: **&lt;PDF&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-6">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Coutput%3E">Parent: **&lt;Output&gt;**</div><div id="bkmrk-description%3A-contain-4">Description: Container for PDF settings</div><div id="bkmrk--10"></div>#### &lt;Metadata&gt;

<div id="bkmrk-xml-tag%3A-%3Cmetadata%3E">XML Tag: **&lt;Metadata&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-7">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cpdf%3E">Parent: **&lt;PDF&gt;**</div><div id="bkmrk-description%3A-contain-5">Description: Container for PDF Metadata settings</div><div id="bkmrk--11">  
</div>#### &lt;Title&gt;

<div id="bkmrk-xml-tag%3A-%3Ctitle%3E">XML Tag: **&lt;Title&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-8">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmetadata%3E">Parent: **&lt;Metadata&gt;**</div><div id="bkmrk-description%3A-title-m">Description: Title Metadata for the PDF document produced</div>```xml
<Title>Default Report</Title>
```

<div id="bkmrk--4"></div><div id="bkmrk-parameters%3A-%40feature">Parameters: </div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

#### &lt;Author&gt;

<div id="bkmrk-xml-tag%3A-%3Cauthor%3E">XML Tag: **&lt;Author&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-9">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmetadata%3E-1">Parent: **&lt;Metadata&gt;**</div><div id="bkmrk-description%3A-author-">Description: Author Metadata for the PDF document produced</div>```xml
<Author>Whanganui District Council</Author>
```

<div id="bkmrk--16"></div>#### &lt;Subject&gt;

<div id="bkmrk-xml-tag%3A-%3Csubject%3E">XML Tag: **&lt;Subject&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-10">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmetadata%3E-2">Parent: **&lt;Metadata&gt;**</div><div id="bkmrk-description%3A-subject">Description: Subject Metadata for the PDF document produced</div>```xml
<Subject>GeoReports PDF Document</Subject>
```

<div id="bkmrk--9"></div><div id="bkmrk-parameters%3A-%40feature-1">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--19"></div>#### &lt;Keywords&gt;

<div id="bkmrk-xml-tag%3A-%3Ckeywords%3E">XML Tag: **&lt;Keywords&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-11">Occurrence: Once only, Required</div><div id="bkmrk-parent%3A-%3Cmetadata%3E-3">Parent: **&lt;Metadata&gt;**</div><div id="bkmrk-description%3A-keyword">Description: Keywords Metadata for the PDF document produced</div>```xml
<Keywords>Map, Property, @featurekey, @databasekey, @referencekey</Keywords>
```

<div id="bkmrk--12"></div><div id="bkmrk-parameters%3A-%40feature-2">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--22">  
</div>