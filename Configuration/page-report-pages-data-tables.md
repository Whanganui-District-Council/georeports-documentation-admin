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

---

## Definition

#### &lt;DataTables&gt;

XML Tag: **&lt;DataTables&gt;**

Occurrence: Once only, Optional

Parent: **&lt;Page&gt;**

Description: Container for Data Tables.

---

#### &lt;OGCWFSDataTable&gt;

XML Tag: **&lt;OGCWFSDataTable&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;DataTables&gt;**

Description: Data table defined by OGC WFS Web Service.

Usage:
```xml
<OGCWFSDataTable caption="Interests - Current" nodata="No Information available" description="Further information is available at https://data.linz.govt.nz/table/51695-nz-title-memorials-list-including-mortgages-leases-easements/">
```

Attributes:
- **caption** Caption text for the data table
- **nodata** Text to display if no data returned
- **description** Description text for the data table

---

</div>#### &lt;URI&gt;

XML Tag: **&lt;URI&gt;**

Occurrence: Once only

Parent: **&lt;OGCWFSDataTable&gt;**

Description: SQL statement returning data.
Usage:

```xml
<URI colwidths="53,27,20">
<![CDATA[https://data.linz.govt.nz/services;key=key/wfs?service=WFS&version=1.0.0&request=GetFeature&typeNames=table-51695&propertyName=memorial_text,instrument_lodged_datetime,instrument_type&cql_filter=current=true%20AND%20title_no=@featurekey]]>
</URI>
```

Attributes:
- **colwidths** comma delimited list of percentage values for column widths (must add up to 100, if not column widths will be sized equally)

Parameters: 
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

---

#### &lt;SQLDataTable&gt;

XML Tag: **&lt;SQLDataTable&gt;**

Occurrence: Multiple allowed, Optional

Parent: **&lt;DataTables&gt;**

Description: Data table defined by SQL Statement.

Usage:

```xml
<SQLDataTable caption="LINZ Primary Land Parcel Information" nodata="No Information available" description="PostGIS Test">
```

Attributes:
- **caption** Caption text for the data table
- **nodata** Text to display if no data returned
- **description** Description text for the data table

---

#### &lt;SQL&gt;

XML Tag: **&lt;SQL&gt;**

Occurrence: Once only

Parent: **&lt;SQLDataTable&gt;**

Description: SQL statement returning data.

Usage:

```xml
<SQL connection="pgLINZodbc" colwidths="20,80">
<![CDATA[
SELECT id,appellation FROM lds.nz_primary_land_parcels WHERE id=@featurekey
]]>
</SQL>
```

Attributes:
- **connection** Name of the SQL Connection to use (as defined in web.config)
- **colwidths** comma delimited list of percentage values for column widths (must add up to 100, if not column widths will be sized equally)

Parameters: 
- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL
