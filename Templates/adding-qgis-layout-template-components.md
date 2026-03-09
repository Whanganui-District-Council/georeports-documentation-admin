# Adding QGIS Layout Template Components

To allow GeoReports to extract the correct components and their attributes from a QGIS Layout Template we add various components to the Layout and give each a specific Item Id that GeoReports recognises

[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/kOjimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/kOjimage.png)

## Map Image Placeholder

<div id="bkmrk-use-the-%C2%A0add-map-too">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/DTfimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/DTfimage.png) **Add Map** tool to add a new Map item to the page by drawing a rectangle on the layout canvas.</div><div id="bkmrk--1"></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/qMoimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/qMoimage.png)

<div id="bkmrk--3">  
</div><div id="bkmrk-in-the-item-properti">In the **Item Properties** for the Map, set the **Item ID** to </div>```ini
ppMap
```

[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/U3Himage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/U3Himage.png)

<div id="bkmrk-%C2%A0-2"> </div><div id="bkmrk-%E2%80%83"></div>## Data Tables Placeholder

<div id="bkmrk--5"></div><div id="bkmrk-use-the-%C2%A0add-label-t">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/TWhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/TWhimage.png) **Add Label** tool to add a label to the Layout</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/E47image.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/E47image.png)

<div id="bkmrk-in-the-item-properti-1">In the **Item Properties** for the Label, set the **Item ID** to </div>```ini
ppData
```

<div id="bkmrk--7"></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/umWimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/umWimage.png)

<div id="bkmrk--10"></div><div id="bkmrk-%E2%80%83-1"></div>## Data Table Styles

[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/w9zimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/w9zimage.png)

<div id="bkmrk-%C2%A0-3">GeoReports will automatically style reports for you, however if you wish to customise the tables fonts, border colors, background colors etc. the following placeholders can be added to the QGIS Layout Template and styled accordingly.</div><div id="bkmrk--12"></div><div id="bkmrk--13"></div><div id="bkmrk--14"></div>#### Data Table Title Style Placeholder

<div id="bkmrk--15"></div><div id="bkmrk-use-the-%C2%A0add-label-t-1">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/UO0image.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/UO0image.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--16">  
</div><div id="bkmrk-in-the-item-properti-2">In the **Item Properties** for the Label, set the **Item ID** to </div>```ini
ppDataTableTitleStyle
```

<div id="bkmrk--17"></div>#### Data Table Description Style Placeholder

<div id="bkmrk--18"></div><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--2">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/UO0image.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/UO0image.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--19">  
</div><div id="bkmrk-in-the-item-properti-3">In the **Item Properties** for the Label, set the **Item ID** to </div>```ini
ppDataTableDescriptionStyle
```

<div id="bkmrk--20"></div>#### Data Table Heading Style Placeholder

<div id="bkmrk--21"></div><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--3">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/UO0image.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/UO0image.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--23">  
</div><div id="bkmrk-in-the-item-properti-4">In the **Item Properties** for the Label, set the **Item ID** to </div>```ini
ppDataTableHeadingStyle
```

<div id="bkmrk--22"></div>#### Data Table Row Default Style Placeholder

<div id="bkmrk--24"></div><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--4">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/UO0image.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/UO0image.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--26">  
</div><div id="bkmrk-in-the-item-properti-5">In the **Item Properties** for the Label, set the **Item ID** to </div>```ini
ppDataTableRowDefaultStyle
```

<div id="bkmrk--25"></div>#### Data Table Row Alternate Style Placeholder

<div id="bkmrk--27"></div><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--5">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/UO0image.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/UO0image.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--30">  
</div><div id="bkmrk-in-the-item-properti-6">In the **Item Properties** for the Label, set the **Item ID** to </div>```ini
ppDataTableRowAlternateStyle
```

<div id="bkmrk--31">  
</div><div id="bkmrk--32">  
</div>#### Label properties from the Style Placeholders that GeoReports uses

<div id="bkmrk--33">  
</div><div id="bkmrk-font">**Font**</div><div id="bkmrk-font-style-%28regular%2C">**Font Style (Regular, Bold and Italic)**</div><div id="bkmrk-font-size">**Font Size**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/AnCimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/AnCimage.png)

<div id="bkmrk-font-color">**Font Color**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/j3timage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/j3timage.png)

<div id="bkmrk--34"></div><div id="bkmrk-background-color">**Background Color**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/TCiimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/TCiimage.png)

<div id="bkmrk-frame-color">**Frame color**</div><div id="bkmrk-frame-thickness">**Frame Thickness**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/AUSimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/AUSimage.png)

<div id="bkmrk--37">  
</div><div id="bkmrk--38">  
</div><div id="bkmrk--39">  
</div><div id="bkmrk-%E2%80%83-2"> </div>## Page Borders

<div id="bkmrk-use-the%C2%A0%C2%A0add-shape-t">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/VFCimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/VFCimage.png) **Add Shape** tool and choose [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/dFrimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/dFrimage.png) **Add Rectangle** then draw a rectangle on the layout canvas.</div><div id="bkmrk--40">  
</div><div id="bkmrk-no-item-id-is-requir">No **Item ID** is required.</div><div id="bkmrk--41">  
</div><div id="bkmrk--42">  
</div><div id="bkmrk--43"></div><div id="bkmrk--44"></div>## Page Images (Static)

<div id="bkmrk-use-the%C2%A0%C2%A0add-picture">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/ibRimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/ibRimage.png) **Add Picture** tool to add a new picture to the Layout by drawing a rectangle</div><div id="bkmrk--45">  
</div><div id="bkmrk-browse-for-the-image">Browse for the image in the **Main Properties** section, **Image source**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/OSximage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/OSximage.png)

<div id="bkmrk-%C2%A0-8"> To control the size of the image, use the **Frame thickness** value (GeoReports multiplies the image width and height by this value)</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/9lBimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/9lBimage.png)

<div id="bkmrk-in-the-item-properti-7">In the **Item Properties** for the Image, set the **Item ID** to </div>```ini
ppImage
```

<div id="bkmrk--48">  
</div><div id="bkmrk--49">  
</div><div id="bkmrk--50"></div>## Page Images (Dynamic via SQL)

<div id="bkmrk--51"></div><div id="bkmrk-use-the-%C2%A0add-label-t-2">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--52">  
</div><div id="bkmrk-in-the-item-properti-8">In the **Item Properties** tab for the label, change the text for the label to the **SQL statement** required to define the URL for the image…</div><div id="bkmrk--53">  
</div>```postgresql
SELECT imagename FROM schema.table WHERE id=@featurekey
```

<div id="bkmrk-parameters%3A">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk-only-the-first-colum">Only the first column of the first record is returned as the image.</div><div id="bkmrk--54"></div><div id="bkmrk-to-control-the-size--1">To control the size of the image, use the **Frame thickness** value (GeoReports multiplies the image width and height by this value)</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/sPGimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/sPGimage.png)

<div id="bkmrk-in-the-item-properti-9">In the **Item Properties** for the Image, set the **Item ID** to </div>```ini
ppImageSQL
```

<div id="bkmrk--56">  
</div><div id="bkmrk--57">  
</div>## Single Map Scale Label (for single map on page)

<div id="bkmrk--58"></div><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--7">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--59">  
</div><div id="bkmrk-modify-the-appearanc">Modify the Appearance properties:</div><div id="bkmrk-font-1">**Font**</div><div id="bkmrk-font-style-%28regular-">**Font Style (Regular or Bold)**</div><div id="bkmrk-font-size-1">**Font Size**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/hIUimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/hIUimage.png)

<div id="bkmrk-font-color-1">**Font Color**</div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/mEhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/mEhimage.png)

<div id="bkmrk-horizontal-alignment">**Horizontal Alignment**</div>![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/fYZimage.png)Note **Justify** is not currently supported

<div id="bkmrk-in-the-item-properti-10">In the **Item Properties** for the Image, set the **Item ID** to </div>```ini
ppScaleText
```

<div id="bkmrk--62">  
</div><div id="bkmrk--63">  
</div>## Page Original Sheet Size Label

<div id="bkmrk--64"></div><div id="bkmrk-use-the-%C2%A0add-label-t-3"><div id="bkmrk-use-the-%C2%A0add-label-t-4">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--65">  
</div><div id="bkmrk-modify-the-appearanc-1">Modify the Appearance properties:</div><div id="bkmrk-font-2">**Font**</div><div id="bkmrk-font-style-%28regular--1">**Font Style (Regular or Bold)**</div><div id="bkmrk-font-size-2">**Font Size**</div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/hIUimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/hIUimage.png)

<div id="bkmrk-font-color-2"><div id="bkmrk-font-color-3">**Font Color**</div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/mEhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/mEhimage.png)

<div id="bkmrk-horizontal-alignment-1"><div id="bkmrk-horizontal-alignment-2">**Horizontal Alignment**</div></div>![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/fYZimage.png)Note **Justify** is not currently supported

<div id="bkmrk-in-the%C2%A0item-properti"><div id="bkmrk-in-the%C2%A0item-properti-1">In the **Item Properties** for the Image, set the **Item ID** to </div></div>```ini
ppPageSize
```

<div id="bkmrk-use-the%C2%A0-%C2%A0add-label--8"><div id="bkmrk--68"></div></div><div id="bkmrk--69">  
</div><div id="bkmrk--70">  
</div>## Page Printed Date Label

<div id="bkmrk--71"></div><div id="bkmrk-use-the-%C2%A0add-label-t-5"><div id="bkmrk-use-the-%C2%A0add-label-t-6"><div id="bkmrk-use-the-%C2%A0add-label-t-7">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--72">  
</div><div id="bkmrk-modify-the-appearanc-2">Modify the Appearance properties:</div><div id="bkmrk-font-3">**Font**</div><div id="bkmrk-font-style-%28regular--2">**Font Style (Regular or Bold)**</div><div id="bkmrk-font-size-3">**Font Size**</div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/hIUimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/hIUimage.png)

<div id="bkmrk-font-color-4"><div id="bkmrk-font-color-5"><div id="bkmrk-font-color-6">**Font Color**</div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/mEhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/mEhimage.png)

<div id="bkmrk-horizontal-alignment-3"><div id="bkmrk-horizontal-alignment-4"><div id="bkmrk-horizontal-alignment-5">**Horizontal Alignment**</div></div></div>![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/fYZimage.png)Note **Justify** is not currently supported

<div id="bkmrk-in-the%C2%A0item-properti-2"><div id="bkmrk-in-the%C2%A0item-properti-3"><div id="bkmrk-in-the%C2%A0item-properti-4">In the **Item Properties** for the Image, set the **Item ID** to </div></div></div>```ini
ppCurrentDate
```

<div id="bkmrk--75">  
</div><div id="bkmrk--76">  
</div><div id="bkmrk--77"></div>## Page Labels (Static)

<div id="bkmrk--78"></div><div id="bkmrk-use-the-%C2%A0add-label-t-8"><div id="bkmrk-use-the-%C2%A0add-label-t-9"><div id="bkmrk-use-the-%C2%A0add-label-t-10">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div></div></div><div id="bkmrk--79"></div>In the **Item Properties** tab for the label, change the text for the label to the text to be returned

```ini
This is some static text
```

<div id="bkmrk-modify-the-appearanc-3"><div id="bkmrk-modify-the-appearanc-4"><div id="bkmrk-modify-the-appearanc-5">Modify the Appearance properties:</div><div id="bkmrk-font-4">**Font**</div><div id="bkmrk-font-style-%28regular--3">**Font Style (Regular or Bold)**</div><div id="bkmrk-font-size-4">**Font Size**</div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/hIUimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/hIUimage.png)

<div id="bkmrk-font-color-7"><div id="bkmrk-font-color-8"><div id="bkmrk-font-color-9">**Font Color**</div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/mEhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/mEhimage.png)

<div id="bkmrk-horizontal-alignment-6"><div id="bkmrk-horizontal-alignment-7"><div id="bkmrk-horizontal-alignment-8">**Horizontal Alignment**</div></div></div>![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/fYZimage.png)Note **Justify** is not currently supported

<div id="bkmrk-in-the%C2%A0item-properti-5"><div id="bkmrk-in-the%C2%A0item-properti-6"><div id="bkmrk-in-the%C2%A0item-properti-7">In the **Item Properties** for the Image, set the **Item ID** to </div></div></div>```ini
ppLabel
```

<div id="bkmrk--82">  
</div><div id="bkmrk--83">  
</div><div id="bkmrk--84"></div>## Page Labels (Dynamic via SQL)

<div id="bkmrk--85"></div><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--11"><div id="bkmrk-use-the-%C2%A0add-label-t-11">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--86"></div></div><div id="bkmrk--87">  
</div><div id="bkmrk-in-the-item-properti-15">In the **Item Properties** tab for the label, change the text for the label to the **SQL statement** required to define the text to be returned…</div><div id="bkmrk--88">  
</div>```postgresql
SELECT text FROM schema.table WHERE id=@featurekey
```

<div id="bkmrk-parameters%3A-1">Parameters:</div>- **@featurekey** Replaced with Feature key value from launch URL
- **@databasekey** Replaced with Database key value from launch URL
- **@referencekey** Replaced with Reference key value from launch URL

<div id="bkmrk-only-the-first-colum-1">Only the first column of the first record is returned as the text.</div><div id="bkmrk-for-the-sql-statemen-1"></div><div id="bkmrk-modify-the-appearanc-6"><div><div id="bkmrk-modify-the-appearanc-7"><div id="bkmrk-modify-the-appearanc-8">Modify the Appearance properties:</div><div id="bkmrk-font-5">**Font**</div><div id="bkmrk-font-style-%28regular--4">**Font Style (Regular or Bold)**</div><div id="bkmrk-font-size-5">**Font Size**</div></div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/hIUimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/hIUimage.png)

<div id="bkmrk-font-color-10"><div><div id="bkmrk-font-color-11"><div id="bkmrk-font-color-12">**Font Color**</div></div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/mEhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/mEhimage.png)

<div id="bkmrk-horizontal-alignment-9"><div><div id="bkmrk-horizontal-alignment-10"><div id="bkmrk-horizontal-alignment-11">**Horizontal Alignment**</div></div></div></div>![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/fYZimage.png)Note **Justify** is not currently supported

<div id="bkmrk-in-the%C2%A0item-properti-8"><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--10"><div id="bkmrk-in-the%C2%A0item-properti-9"><div id="bkmrk-in-the%C2%A0item-properti-10">In the **Item Properties** for the Image, set the **Item ID** to </div></div></div></div>```ini
ppLabelSQL
```

<div id="bkmrk--91">  
</div><div id="bkmrk--92">  
</div>## Page Title Label

<div id="bkmrk--93"></div><div id="bkmrk-use-the-%C2%A0add-label-t-12"><div><div id="bkmrk-use-the-%C2%A0add-label-t-13"><div id="bkmrk-use-the-%C2%A0add-label-t-14">Use the [![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/K5eimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/K5eimage.png) **Add Label** tool to add a label to the Layout</div><div id="bkmrk--94">  
</div><div id="bkmrk-modify-the-appearanc-9">Modify the Appearance properties:</div><div id="bkmrk-font-6">**Font**</div><div id="bkmrk-font-style-%28regular--5">**Font Style (Regular or Bold)**</div><div id="bkmrk-font-size-6">**Font Size**</div></div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/hIUimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/hIUimage.png)

<div id="bkmrk-font-color-13"><div><div id="bkmrk-font-color-14"><div id="bkmrk-font-color-15">**Font Color**</div></div></div></div>[![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/mEhimage.png)](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/mEhimage.png)

<div id="bkmrk-horizontal-alignment-12"><div><div id="bkmrk-horizontal-alignment-13"><div id="bkmrk-horizontal-alignment-14">**Horizontal Alignment**</div></div></div></div>![image.png](https://maps.whanganui.govt.nz/gis-technical-manual/uploads/images/gallery/2026-03/scaled-1680-/fYZimage.png)Note **Justify** is not currently supported

<div id="bkmrk-in-the%C2%A0item-properti-11"><div id="bkmrk-use-the%C2%A0-%C2%A0add-label--9"><div id="bkmrk-in-the%C2%A0item-properti-12"><div id="bkmrk-in-the%C2%A0item-properti-13">In the **Item Properties** for the Image, set the **Item ID** to </div></div></div></div>```ini
ppTitle
```

<div id="bkmrk--97">  
</div><div id="bkmrk--98"></div>