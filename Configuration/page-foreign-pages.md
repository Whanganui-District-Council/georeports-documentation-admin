# Page - Foreign Pages

A Foreign Page is a page retrieved from another PDF document.

### Example XML

<div id="bkmrk-">  
</div><div id="bkmrk-return-a-page-from-a">Return a page from a local PDF file (absolute local path)</div><div id="bkmrk--1">  
</div>```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignPages>
        <ForeignPage importpage="1">/data/georeports-data/docs/documentname.pdf</ForeignPage>
      </ForeignPages>
    </Page>
```

<div id="bkmrk--2"></div><div id="bkmrk-return-a-page-from-a-1">Return a page from a local PDF file (relative local path)</div><div id="bkmrk--3">  
</div>```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignPages>
        <ForeignPage importpage="1">docs/documentname.pdf</ForeignPage>
      </ForeignPages>
    </Page>
```

<div id="bkmrk--4"></div><div id="bkmrk-return-a-page-from-a-2">Return a page from a web PDF file</div><div id="bkmrk--5">  
</div>```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
      <ForeignPages>
        <ForeignPage type="web" importpage="1">https://domainname/path/documentname.pdf</ForeignPage>
      </ForeignPages>
    </Page>
```

<div id="bkmrk--6"></div><div id="bkmrk-return-pages-from-a-">Return pages from another GeoReport configuration</div><div id="bkmrk--7">  
</div>```xml
    <Page type="Foreign">
      <PageGeneration include="true" />
    <ForeignPages>
        <ForeignPage type="internal" report="reportname" importpage="all">
            <Param name="featkey">@featurekey</Param>
        </ForeignPage>
    </ForeignPages>    
  </Page>
```

<div id="bkmrk--8"></div><div id="bkmrk-return-pages-from-a--1">Return pages from a PDF location defined by SQL Statement (the location could be a local PDF document, a static web PDF document, or a dynamically produced web PDF document).</div><div id="bkmrk--9">  
</div>```xml
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

<div id="bkmrk-%E2%80%83"> </div>#### &lt;Page&gt;

<div id="bkmrk-xml-tag%3A-%3Cpage%3E">XML Tag: **&lt;Page&gt;**</div><div id="bkmrk-occurrence%3A-multiple">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cpages%3E">Parent: **&lt;Pages&gt;**</div><div id="bkmrk-description%3A-imports">Description: Imports one or more pages from another PDF.</div>```xml
<Page type="Foreign">
```

<div id="bkmrk--11"></div><div id="bkmrk-attributes%3A">Attributes:</div><div id="bkmrk-type-the-type-of-pag">- **type** The type of page to produce, “Foreign”.

</div><div id="bkmrk--12">  
</div>#### &lt;PageGeneration&gt;

<div id="bkmrk-xml-tag%3A-%3Cpagegenera">XML Tag: **&lt;PageGeneration&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Optional (default is true if not present)</div><div id="bkmrk-parent%3A-%3Cpage%3E">Parent: **&lt;Page&gt;**</div><div id="bkmrk-description%3A-whether">Description: Whether to include this page in generation of the PDF report.</div><div id="bkmrk-usage%3A-1">Usage:</div>```xml
<PageGeneration include="true" />
```

<div id="bkmrk--13"></div><div id="bkmrk-attributes%3A-1">Attributes:</div><div id="bkmrk-include-true%2Ffalse-t">- **include** true/false to include this page in generation of the PDF report

</div><div id="bkmrk--15">  
</div>#### &lt;ForeignPages&gt;

<div id="bkmrk-xml-tag%3A-%3Cforeignpag">XML Tag: **&lt;ForeignPages&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-1">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cpage%3E-1">Parent: **&lt;Page&gt;**</div><div id="bkmrk-description%3A-contain">Description: Container for Foreign Pages</div><div id="bkmrk--17"></div><div id="bkmrk--18">  
</div>#### &lt;ForeignPage&gt;

<div id="bkmrk-xml-tag%3A-%3Cforeignpag-1">XML Tag: **&lt;ForeignPage&gt;**</div><div id="bkmrk-occurrence%3A-multiple-1">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cforeignpage">Parent: **&lt;ForeignPages&gt;**</div><div id="bkmrk-description%3A-selects">Description: Selects which page or pages to import from a PDF document.</div><div id="bkmrk-usage%3A-3">Usage:</div>```xml
<ForeignPage importpage="1" type="local">docs\test.pdf</ForeignPage>
```

<div id="bkmrk-usage-for-internal%3A">Usage for Internal:</div>```xml
<ForeignPage type="internal" report="reportname" importpage="all">
```

<div id="bkmrk--14"></div><div id="bkmrk-attributes%3A-2">Attributes:</div>- **importpage** page number to import. Format: 1,2,6,8-9
- **type** optional, either local or web or internal (local is default if not present)
- **report** If type is Internal, the name of an existing report configuration file.

<div id="bkmrk--21">  
</div><div id="bkmrk--22">  
</div>#### &lt;ForeignSQLPages&gt;

<div id="bkmrk-xml-tag%3A-%3Cforeignsql">XML Tag: **&lt;ForeignSQLPages&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-2">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cpage%3E-2">Parent: **&lt;Page&gt;**</div><div id="bkmrk-description%3A-contain-1">Description: Container for Foreign Pages derived by SQL Statement</div><div id="bkmrk-%3Cforeignsqlpages%3E-1"></div><div id="bkmrk--23">  
</div><div id="bkmrk--24">  
</div>#### &lt;ForeignSQLPage&gt;

<div id="bkmrk-xml-tag%3A-%3Cforeignsql-1">XML Tag: **&lt;ForeignSQLPage&gt;**</div><div id="bkmrk-occurrence%3A-multiple-2">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cforeignsqlp">Parent: **&lt;ForeignSQLPages&gt;**</div><div id="bkmrk-description%3A-selects-1">Description: Selects which page or pages to import from a PDF document.</div><div id="bkmrk-%3Cforeignsqlpage%3E-1"></div>#### &lt;SQL&gt;

<div id="bkmrk-xml-tag%3A-%3Csql%3E">XML Tag: **&lt;SQL&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-3">Occurrence: Once only</div><div id="bkmrk-parent%3A-%3Cforeignsqlp-1">Parent: **&lt;ForeignSQLPage&gt;**</div><div id="bkmrk-description%3A-sql-sta">Description: SQL statement returning document, importpage, type.</div><div id="bkmrk-usage%3A-6">Usage:</div>```xml
<SQL connection=”connname”><![CDATA[select ‘documentname’,’1,2,6-8’,’web’ FROM tablename WHERE id=@featurekey]]></SQL>
```

<div id="bkmrk--16"></div><div id="bkmrk-attributes%3A-3">Attributes:</div><div id="bkmrk-connection-name-of-t">- **connection** Name of the SQL Connection to use (as defined in web.config)

</div><div id="bkmrk-parameters%3A-%40feature">Parameters: </div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--29">  
</div><div id="bkmrk--30"></div>