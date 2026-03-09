# Page - Report Pages - Data Tables

### Example XML

Use WFS Web Service to return data for a table

```xml
  <DataTables>
    <OGCWFSDataTable caption="Interests - Current" nodata="No Information available" description="Further information is available at https://data.linz.govt.nz/table/51695-nz-title-memorials-list-including-mortgages-leases-easements/">
<URI colwidths="53,27,20"><![CDATA[https://data.linz.govt.nz/services;key=key/wfs?service=WFS&version=1.0.0&request=GetFeature&typeNames=table-51695&propertyName=memorial_text,instrument_lodged_datetime,instrument_type&cql_filter=current=true%20AND%20title_no=@featurekey]]></URI>
        </OGCWFSDataTable>
    <OGCWFSDataTable caption="Interests - Historic" nodata="No Information available" description="Further information is available at https://data.linz.govt.nz/table/51695-nz-title-memorials-list-including-mortgages-leases-easements/">
<URI colwidths="53,27,20"><![CDATA[https://data.linz.govt.nz/services;key=key/wfs?service=WFS&version=1.0.0&request=GetFeature&typeNames=table-51695&propertyName=memorial_text,instrument_lodged_datetime,instrument_type&cql_filter=current=false%20AND%20title_no=@featurekey]]></URI>
        </OGCWFSDataTable>
    <OGCWFSDataTable caption="Registered Owners" nodata="No Information available" description="An owner is a person or corporation holding a share in a Title estate.&#xA;Further information is available at https://data.linz.govt.nz/table/51564-nz-property-titles-owners-list/">
<URI colwidths="14,14,14,19,19,20"><![CDATA[https://data.linz.govt.nz/services;key=key/wfs?service=WFS&version=1.0.0&request=GetFeature&typeNames=table-51564&propertyName=status,estate_share,owner_type,prime_surname,prime_other_names,corporate_name&cql_filter=title_no=@featurekey]]></URI>
        </OGCWFSDataTable>
  </DataTables>
```

Use SQL Statement to return data for a table

```xml
      <DataTables>
        <SQLDataTable caption="Land Information" nodata="No Information available" description="Data sourced from LINZ">
            <SQL connection="pgwdcgisodbc" colwidths="15,55,15,15">
<![CDATA[SELECT l.par_id as "Parcel ID", l.appellation AS "Appellation", l.area_m2 As "Area", l.land_no AS "Land No"
FROM property.land as l,
(SELECT geom FROM property.property WHERE prop_no = '@featurekey') as p
WHERE ST_Intersects(ST_Buffer(p.geom,-1),l.geom)
ORDER BY l.par_id]]>
            </SQL>
        </SQLDataTable>
        <SQLDataTable caption="Address Information" nodata="No Information available" description="Data sourced from LINZ">
            <SQL connection="pgwdcgisodbc" colwidths="15,85">
<![CDATA[SELECT a.address_id  as "Address ID", a.addr_full as "Address"
FROM property.address as a,
(SELECT geom FROM property.property WHERE prop_no = '@featurekey') as p
WHERE ST_Intersects(ST_Buffer(p.geom,-1),a.geom)
ORDER BY a.address_id]]>
            </SQL>
        </SQLDataTable>
        <SQLDataTable caption="Title Information" nodata="No Information available" description="Data sourced from LINZ">
            <SQL connection="pgwdcgisodbc" colwidths="15,15">
<![CDATA[SELECT t.title_no as "Title No", t.status as "Status", t.type as "Type", t.land_district as "Land District", to_char(t.issue_date::date, 'dd/mm/yyyy') as "Issue Date" FROM linz.nz_property_titles as t, (SELECT geom FROM property.property WHERE prop_no = '@featurekey') as p
WHERE ST_Intersects(ST_Buffer(p.geom,-1),t.wkb_geometry) order by t.issue_date]]>
            </SQL>
        </SQLDataTable>
      </DataTables>
```

<div id="bkmrk--1"></div><div id="bkmrk--2"></div><div id="bkmrk--3"></div><div id="bkmrk--4"></div><div id="bkmrk--5"></div><div id="bkmrk--6"></div><div id="bkmrk--7"></div>## Definition

<div id="bkmrk--8"></div><div id="bkmrk--9"></div>#### &lt;DataTables&gt;

<div id="bkmrk-xml-tag%3A-%3Cdatatables">XML Tag: **&lt;DataTables&gt;**</div><div id="bkmrk-occurrence%3A-once-onl">Occurrence: Once only, Optional</div><div id="bkmrk-parent%3A-%3Cpage%3E">Parent: **&lt;Page&gt;**</div><div id="bkmrk-description%3A-contain">Description: Container for Data Tables.</div><div id="bkmrk-%3Cdatatables%3E-1"></div><div id="bkmrk--10">  
</div><div id="bkmrk--11"></div>#### &lt;OGCWFSDataTable&gt;

<div id="bkmrk-xml-tag%3A-%3Cogcwfsdata"><div id="bkmrk-xml-tag%3A-%3Csqldatatab">XML Tag: **&lt;OGCWFSDataTable&gt;**</div><div id="bkmrk-occurrence%3A-multiple">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cdatatables%3E">Parent: **&lt;DataTables&gt;**</div><div id="bkmrk-description%3A-data-ta">Description: Data table defined by OGC WFS Web Service.</div><div id="bkmrk-usage%3A-1">Usage:</div></div>```xml
<OGCWFSDataTable caption="Interests - Current" nodata="No Information available" description="Further information is available at https://data.linz.govt.nz/table/51695-nz-title-memorials-list-including-mortgages-leases-easements/">
```

<div id="bkmrk-attributes%3A-caption-"><div id="bkmrk-attributes%3A">Attributes:</div>- **caption** Caption text for the data table
- **nodata** Text to display if no data returned
- **description** Description text for the data table

</div>#### &lt;URI&gt;

<div id="bkmrk-xml-tag%3A-%3Curi%3E-occur"><div id="bkmrk-xml-tag%3A-%3Csql%3E">XML Tag: **&lt;URI&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-1">Occurrence: Once only</div><div id="bkmrk-parent%3A-%3Csqldatatabl">Parent: **&lt;OGCWFSDataTable&gt;**</div><div id="bkmrk-description%3A-sql-sta">Description: SQL statement returning data.</div><div id="bkmrk-usage%3A-2">Usage:</div></div>```xml
<URI colwidths="53,27,20">
<![CDATA[https://data.linz.govt.nz/services;key=key/wfs?service=WFS&version=1.0.0&request=GetFeature&typeNames=table-51695&propertyName=memorial_text,instrument_lodged_datetime,instrument_type&cql_filter=current=true%20AND%20title_no=@featurekey]]>
</URI>
```

<div id="bkmrk-attributes%3A-colwidth"><div id="bkmrk-attributes%3A-1">Attributes:</div>- **colwidths** comma delimited list of percentage values for column widths (must add up to 100, if not column widths will be sized equally)

<div id="bkmrk-parameters%3A-%40feature">Parameters: </div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--17"></div>  
</div><div id="bkmrk--12"></div><div id="bkmrk--13"></div><div id="bkmrk--14"></div>#### &lt;SQLDataTable&gt;

<div id="bkmrk-xml-tag%3A-%3Csqldatatab-1">XML Tag: **&lt;SQLDataTable&gt;**</div><div id="bkmrk-occurrence%3A-multiple-1">Occurrence: Multiple allowed, Optional</div><div id="bkmrk-parent%3A-%3Cdatatables%3E-1">Parent: **&lt;DataTables&gt;**</div><div id="bkmrk-description%3A-data-ta-1">Description: Data table defined by SQL Statement.</div><div id="bkmrk-usage%3A">Usage:</div>```xml
<SQLDataTable caption="LINZ Primary Land Parcel Information" nodata="No Information available" description="PostGIS Test">
```

<div id="bkmrk-attributes%3A-2">Attributes:</div>- **caption** Caption text for the data table
- **nodata** Text to display if no data returned
- **description** Description text for the data table

#### &lt;SQL&gt;

<div id="bkmrk-xml-tag%3A-%3Csql%3E-1">XML Tag: **&lt;SQL&gt;**</div><div id="bkmrk-occurrence%3A-once-onl-2">Occurrence: Once only</div><div id="bkmrk-parent%3A-%3Csqldatatabl-1">Parent: **&lt;SQLDataTable&gt;**</div><div id="bkmrk-description%3A-sql-sta-1">Description: SQL statement returning data.</div><div id="bkmrk-usage%3A-3">Usage:</div>```xml
<SQL connection="pgLINZodbc" colwidths="20,80">
<![CDATA[
SELECT id,appellation FROM lds.nz_primary_land_parcels WHERE id=@featurekey
]]>
</SQL>
```

<div id="bkmrk--16"></div><div id="bkmrk-attributes%3A-3">Attributes:</div>- **connection** Name of the SQL Connection to use (as defined in web.config)
- **colwidths** comma delimited list of percentage values for column widths (must add up to 100, if not column widths will be sized equally)

<div id="bkmrk-parameters%3A%C2%A0">Parameters: </div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk--18">  
</div><div id="bkmrk--19"></div>