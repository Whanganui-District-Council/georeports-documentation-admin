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

---

### QGIS Settings

QGIS Layout templates (.qpt files) are used to XXXXX

#### &lt;QGIS&gt;

XML Tag: **&lt;QGIS&gt;**

Occurrence: Once only, Optional

Parent: **&lt;Settings&gt;**

Description: Container for QGIS related settings

---

#### &lt;QPTLayout&gt;

XML Tag: **&lt;QPTLayout&gt;**, Optional

Occurrence: Once only

Parent: **&lt;QGIS&gt;**

Description: Container for QGIS QPT Layout related settings

---

#### &lt;SQLConnections&gt;

XML Tag: **&lt;SQLConnections&gt;**

Occurrence: Once only, Optional

Parent: **&lt;QPTLayout&gt;**

Description: Container for QGIS QPT Layout SQL Connection related settings

---

#### &lt;Labels&gt;

XML Tag: **&lt;Labels&gt;**

Occurrence: Once only, Optional (Defaults to “Labels” if not present)

Parent: **&lt;SQLConnections&gt;**

Description: Name of the SQL Connection to use for SQL Generated Labels

```xml
<Labels>SQLLabels</Labels>
```

---

#### &lt;Images&gt;

XML Tag: **&lt;Images&gt;**

Occurrence: Once only, Optional (Defaults to “Images” if not present)

Parent: **&lt;SQLConnections&gt;**

Description: Name of the SQL Connection to use for SQL Generated Images

```xml
<Images>SQLImages</Images>
```

---

### Output Settings


#### &lt;Output&gt;

XML Tag: **&lt;Output&gt;**

Occurrence: Once only, Required

Parent: **&lt;Settings&gt;**

Description: Container for Output settings

---

#### &lt;PDF&gt;

XML Tag: **&lt;PDF&gt;**

Occurrence: Once only, Required

Parent: **&lt;Output&gt;**

Description: Container for PDF settings

---

#### &lt;Metadata&gt;

XML Tag: **&lt;Metadata&gt;**

Occurrence: Once only, Required

Parent: **&lt;PDF&gt;**

Description: Container for PDF Metadata settings

---

#### &lt;Title&gt;

XML Tag: **&lt;Title&gt;**

Occurrence: Once only, Required

Parent: **&lt;Metadata&gt;**

Description: Title Metadata for the PDF document produced

```xml
<Title>Default Report</Title>
```


Parameters:
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

---

#### &lt;Author&gt;

XML Tag: **&lt;Author&gt;**

Occurrence: Once only, Required

Parent: **&lt;Metadata&gt;**

Description: Author Metadata for the PDF document produced

```xml
<Author>Whanganui District Council</Author>
```

---

#### &lt;Subject&gt;

XML Tag: **&lt;Subject&gt;**

Occurrence: Once only, Required

Parent: **&lt;Metadata&gt;**

Description: Subject Metadata for the PDF document produced

```xml
<Subject>GeoReports PDF Document</Subject>
```


Parameters:
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

---

#### &lt;Keywords&gt;


XML Tag: **&lt;Keywords&gt;**

Occurrence: Once only, Required

Parent: **&lt;Metadata&gt;**

Description: Keywords Metadata for the PDF document produced

```xml
<Keywords>Map, Property, @featurekey, @databasekey, @referencekey</Keywords>
```


Parameters:
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL
