# Page - Foreign Pages

A Foreign Page is a page retrieved from another PDF document.

### Example XML

Return a page from a local PDF file (absolute local path)  

```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignPages>
        <ForeignPage importpage="1">/data/georeports-data/docs/documentname.pdf</ForeignPage>
      </ForeignPages>
    </Page>
```

Return a page from a local PDF file (relative local path)

```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignPages>
        <ForeignPage importpage="1">docs/documentname.pdf</ForeignPage>
      </ForeignPages>
    </Page>
```

Return a page from a web PDF file

```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignPages>
        <ForeignPage type="web" importpage="1">https://domainname/path/documentname.pdf</ForeignPage>
      </ForeignPages>
    </Page>
```

Return pages from another GeoReport configuration

```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
    <ForeignPages>
        <ForeignPage type="internal" report="reportname" importpage="all">
            <Param name="featkey">@featurekey</Param>
        </ForeignPage>
    </ForeignPages>    
  </Page>
```

Return pages from a PDF location defined by SQL Statement (the location could be a local PDF document, a static web PDF document, or a dynamically produced web PDF document).

```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignSQLPages>
        <ForeignSQLPage>
          <SQL connection="pgwdcgisodbc">
<![CDATA[
SELECT
'https://domainname/path/application' || CHR(63) || 'paramname1=paramvalue1&featkey=' || @featurekey as doc,
'*' as docimportpages,
'web' AS doctype
]]>
          </SQL>
        </ForeignSQLPage>
      </ForeignSQLPages>
  </Page>
```

## Definitions


---
#### &lt;Page&gt;

XML Tag: **&lt;Page&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;Pages&gt;**

Description: Imports one or more pages from another PDF.


```xml
<Page type="Foreign">
```

Attributes:

- **type** The type of page to produce, “Foreign”.

---

#### &lt;PageGeneration&gt;



XML Tag: **&lt;PageGeneration&gt;**

Occurrence: Once only, Optional (default is true if not present)

Parent: **&lt;Page&gt;**

Description: Whether to include this page in generation of the PDF report.

Usage:

```xml
<PageGeneration include="true" />
```

Attributes:
- **include** true/false to include this page in generation of the PDF report

---

#### &lt;ForeignPages&gt;

XML Tag: **&lt;ForeignPages&gt;**

Occurrence: Once only, Optional

Parent: **&lt;Page&gt;**

Description: Container for Foreign Pages

---

#### &lt;ForeignPage&gt;

XML Tag: **&lt;ForeignPage&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;ForeignPages&gt;**

Description: Selects which page or pages to import from a PDF document.

Usage:

```xml
<ForeignPage importpage="1" type="local">docs\test.pdf</ForeignPage>
```


Usage for Internal:
```xml
<ForeignPage type="internal" report="reportname" importpage="all">
```

Attributes:
- **importpage** page number to import. Format: 1,2,6,8-9
- **type** optional, either local or web or internal (local is default if not present)
- **report** If type is Internal, the name of an existing report configuration file.

---

#### &lt;ForeignSQLPages&gt;

XML Tag: **&lt;ForeignSQLPages&gt;**

Occurrence: Once only, Optional

Parent: **&lt;Page&gt;**

Description: Container for Foreign Pages derived by SQL Statement

---

#### &lt;ForeignSQLPage&gt;

XML Tag: **&lt;ForeignSQLPage&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;ForeignSQLPages&gt;**

Description: Selects which page or pages to import from a PDF document.

---

#### &lt;SQL&gt;

XML Tag: **&lt;SQL&gt;**

Occurrence: Once only

Parent: **&lt;ForeignSQLPage&gt;**

Description: SQL statement returning document, importpage, type.

Usage:
```xml
<SQL connection=”connname”><![CDATA[select ‘documentname’,’1,2,6-8’,’web’ FROM tablename WHERE id=@featurekey]]></SQL>
```


Attributes:
- **connection** Name of the SQL Connection to use (as defined in web.config)


Parameters: 
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL
