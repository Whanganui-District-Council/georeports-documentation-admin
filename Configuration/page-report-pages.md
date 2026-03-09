# Page - Report Pages

## Definition

#### &lt;Page&gt;

XML Tag: **&lt;Page&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;Pages&gt;**

Description: Pages containing map images and/or data tables

```xml
<Page type="Report" title="Property @featurekey&#xa;Locality Map" name="Property Map" template="templates/sampleA4PortraitMap.qpt">
```


Attributes:
- **type** the type of page to produce, “Report”.
- **title** text displayed as a title label on the page (**&amp;#xa;** is an HTML entity reference that represents a line feed (LF) character).


    Parameters: 
    - **@featurekey** Replaced with Feature key value from launch URL
    - **@databasekey** Replaced with Database key value from launch URL
    - **@referencekey** Replaced with Reference key value from launch URL

- **name** name of the page
- **template** relative file path and filename of QGIS template

---

#### &lt;PageGeneration&gt;

XML Tag: **&lt;PageGeneration&gt;**

Occurrence: Once only, Optional (default is true if not present)

Parent: **&lt;Page&gt;**

Description: Whether to include this page in generation of the PDF report.

```xml
<PageGeneration include="true" />
```

Attributes:
- **include** true/false to include this page in generation of the PDF report

