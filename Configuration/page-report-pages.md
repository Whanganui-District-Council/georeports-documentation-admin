# Page - Report Pages

<div id="bkmrk-"></div><div id="bkmrk--1"></div>## Definition

#### &lt;Page&gt;

<div id="bkmrk-xml-tag%3A-%3Cpage%3E">XML Tag: **&lt;Page&gt;**</div><div id="bkmrk-occurrence%3A-multiple">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cpages%3E">Parent: **&lt;Pages&gt;**</div><div id="bkmrk-description%3A-pages-c">Description: Pages containing map images and/or data tables</div>```xml
<Page type="Report" title="Property @featurekey&#xa;Locality Map" name="Property Map" template="templates/sampleA4PortraitMap.qpt">
```

<div id="bkmrk--3"></div><div id="bkmrk-attributes%3A">Attributes:</div><div id="bkmrk-type-the-type-of-pag">- **type** the type of page to produce, “Report”.
- **title** text displayed as a title label on the page (&amp;#xa; is an HTML entity reference that represents a line feed (LF) character.

</div><div id="bkmrk-parameters%3A-%40feature" style="padding-left: 40px;">Parameters: </div>- - **@featurekey** Replaced with Feature key value from launch URL
    - **@databasekey** Replaced with Database key value from launch URL
    - **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk-name-name-of-the-pag">- **name** name of the page
- **template** relative file path and filename of QGIS template

</div><div id="bkmrk--6"></div><div id="bkmrk--8"></div>#### &lt;PageGeneration&gt;

<div id="bkmrk-xml-tag%3A-%3Cpagegenera">XML Tag: **&lt;PageGeneration&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Optional (default is true if not present)</div><div id="bkmrk-parent%3A-%3Cpage%3E">Parent: **&lt;Page&gt;**</div><div id="bkmrk-description%3A-whether">Description: Whether to include this page in generation of the PDF report.</div>```xml
<PageGeneration include="true" />
```

<div id="bkmrk--4"></div><div id="bkmrk-attributes%3A-1">Attributes:</div><div id="bkmrk-include-true%2Ffalse-t">- **include** true/false to include this page in generation of the PDF report

</div><div id="bkmrk--10">  
</div><div id="bkmrk--11">  
</div><div id="bkmrk--12"></div>