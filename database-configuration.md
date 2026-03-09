# Database Configuration

## Database Properties File

**/data/georeports-data/db\_config.properties**

Defines the database connection settings for each database connection name (e.g. pgwdcgisodbc)

```ini
pgwdcgisodbc.url=jdbc:postgresql://hostname:port/databasename
pgwdcgisodbc.user=username
pgwdcgisodbc.password=password
pgwdcgisodbc.driver=org.postgresql.Driver
pgwdcgisogr.url=host=hostname port=port dbname=databasename
pgwdcgisogr.user=username
pgwdcgisogr.password=password
pgwdcgisogr.driver=PG
```

##### Docker Compose

Use the docker compose **CONFIGURATION\_PATH** environment variable to set the correct path to the **db\_config.properties** file:

```yaml
  - CONFIGURATION_PATH=/data/georeports-data/
```

## Database Connections from Config Files

The following describes where you might find references to the connection names defined in **db\_config.properties** in your GeoReports Configuration files (.config).

The Config Files section describes these configuration settings in more detail.


##### Settings

The Settings section of each config file contains settings that relate to connecting to SQL Databases for producing labels and images from QGIS Layout Templates

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

##### Foreign Pages

Foreign SQL Pages use a connection name

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

##### Map Scale Feature

<div id="bkmrk-using-a-sql-statemen">Map Scale determination can use a SQL Statement to retrieve the feature geometry to use to calculate the scale</div><div id="bkmrk--4">  
</div>```xml
<ScaleFeature type="SQL" multiplier="1.1">
  <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT prop_no,ST_Envelope(geom) as geom from property.property WHERE prop_no = '@featurekey'
]]></SQL>
</ScaleFeature>
```

##### Map Features

Map Features can use a connection name

```xml
        <MapFeatures>
            <MapFeature type="SQL">

                <SQL connection="pgwdcgisogr" ogrDriver="PG:" table="tables=property.property" dialect=""><![CDATA[SELECT geom from property.property WHERE prop_no = '@featurekey']]></SQL>

                <Brush alpha="1" red="100" green="100" blue="0"/>
                <Pen alpha="255" red="255" green="0" blue="0" width="2"/>

            </MapFeature>
        </MapFeatures>
```

##### Data Tables

Data tables can also use a SQL Statement to return data for a table

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
      </DataTables>
```