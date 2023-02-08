







# Toolset

## Platforms

The FMG toolbox uses ESRI and open source software to construct a custom toolbox for analysis and reporting of forestry inventory data.

-   ArcGIS Desktop -Desktop (ArcMap and ArcGIS Pro) are industry standard enterprise desktop GIS products for conducting geospatial analysis. The ArcGIS desktop applications contain an enormous number of commercial-off-the shelf (COTS) geospatial tools for performing sophisticated analyses and visualization.
-   ArcGIS toolbox - ArcGIS Desktop allows for the creation of sophisticated custom geospatial toolboxes to be built that combine ESRI's COTS geoprocessing tools with user created tools from several platforms (e.g., Python, R).
-   Python - ArcGIS provides a robust scripting interface to its GIS tools using the Python language. Custom geospatial toolboxes can combine ESRI's COTS geoprocessing tools with tools available within the diverse, mature, and ever-growing Python data science ecosystem.
-   R - ESRI's ArcGIS R-bridge product allows R tools to be called within the ArcGIS toolbox interface. This allows ArcGIS tools to take advantage of the mature ecosystem of R data science, statistical, visualization, and report generation packages

## ArcGIS Toolbox

The FMG toolbox contains two toolsets, the QA toolset and the Summary toolset. This ArcGIs toolbox is developed using custom Python scripts.

### QA Tools

#### `01-Prep QA Workspace`

**Purpose**- This tool creates a QA geodatabase for each input (Fixed, Prism, Age,Plot)

**Code-** This ArcGIS tool is built from the Python Script [Prep QA Workspace Tool](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/01_prep_qa_workspace.py)

<table>
<caption>(\#tab:unnamed-chunk-1)Prep QA Workspace Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Destination Folder </td>
   <td style="text-align:left;"> Folder in which output .gdb will be created </td>
   <td style="text-align:left;"> Folder </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plots </td>
   <td style="text-align:left;"> Fixed plots (shapefile or feature class) </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Prism Plots </td>
   <td style="text-align:left;"> Prism plots (shapefile or feature class) </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age Plots </td>
   <td style="text-align:left;"> Age plots (shapefile or feature class) </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot Centers </td>
   <td style="text-align:left;"> Plot center locations (shapefile or feature class) </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool1.png" alt="01 - Prep QA Workspace Tool dialogue." width="335" />
<p class="caption">(\#fig:unnamed-chunk-2)01 - Prep QA Workspace Tool dialogue.</p>
</div>

#### `02-Check Required Fields [Plot Center]`

**Purpose-** Checks the plot center input for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Plot Center)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/02_check_required_fields_center.py)

<table>
<caption>(\#tab:unnamed-chunk-3)Check Required Fields [Plot Center] Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Plot Centers </td>
   <td style="text-align:left;"> Plot center locations (feature class) </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot Type Field </td>
   <td style="text-align:left;"> Name of field containing site type flags (age, walkthrough, etc) </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool2.png" alt="02 - Check Required Fields [Plot Center] Tool Dialogue." width="339" />
<p class="caption">(\#fig:unnamed-chunk-4)02 - Check Required Fields [Plot Center] Tool Dialogue.</p>
</div>

#### `03-Check Required Fields [Prism]`

**Purpose-** Checks prism plots for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Prism)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/03_check_required_fields_prism.py)

<table>
<caption>(\#tab:unnamed-chunk-5)Check Required Fields [Prism] Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Prism Plots </td>
   <td style="text-align:left;"> Prism plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Species Field </td>
   <td style="text-align:left;"> Name of tree species field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> DBH Field </td>
   <td style="text-align:left;"> Dialog Reference </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Canopy Class Field </td>
   <td style="text-align:left;"> Name of canopy class field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Health Field </td>
   <td style="text-align:left;"> Name of tree health field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Misc Field </td>
   <td style="text-align:left;"> Name of miscellanious notes field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> optional </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Crew Field </td>
   <td style="text-align:left;"> Name of crew field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Date Field </td>
   <td style="text-align:left;"> Name of date field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool3.png" alt="03 - Check Required Fields [Prism] Tool Dialogue." width="341" />
<p class="caption">(\#fig:unnamed-chunk-6)03 - Check Required Fields [Prism] Tool Dialogue.</p>
</div>

#### `04-Check Required Fields [Fixed]`

**Purpose-** Checks fixed plots for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Fixed)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/04_check_required_fields_fixed.py)

<table>
<caption>(\#tab:unnamed-chunk-7)Check Required Fields [Fixed] Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Fixed Plots </td>
   <td style="text-align:left;"> Fixed plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Canopy Closure Field </td>
   <td style="text-align:left;"> Name of overstory closure field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Overstory Height Field </td>
   <td style="text-align:left;"> Name of overstory height field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Understory Height Field </td>
   <td style="text-align:left;"> Name of understory height range field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Understory Cover Field </td>
   <td style="text-align:left;"> Name of understory cover field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Understory Species Field </td>
   <td style="text-align:left;"> Name of understory species field (if multiple, choose the first one) </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Ground Species Field </td>
   <td style="text-align:left;"> Name of ground species field (if multiple, choose the first one) </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Misc Field </td>
   <td style="text-align:left;"> Name of miscellanious notes field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> optional </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Crew Field </td>
   <td style="text-align:left;"> Name of crew field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Date Field </td>
   <td style="text-align:left;"> Name of date field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool4.png" alt="04 - Check Required Fields [Fixed] Tool Dialogue." width="336" />
<p class="caption">(\#fig:unnamed-chunk-8)04 - Check Required Fields [Fixed] Tool Dialogue.</p>
</div>

#### `05-Check Required Fields [Age]`

**Purpose-** Checks age plots for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Age)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/05_check_required_fields_age.py)

<table>
<caption>(\#tab:unnamed-chunk-9)Check Required Fields [Age] Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Age Plots </td>
   <td style="text-align:left;"> Age plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Species Field </td>
   <td style="text-align:left;"> Name of tree species field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> DBH Field </td>
   <td style="text-align:left;"> Name of tree diameter field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Height Field </td>
   <td style="text-align:left;"> Name of tree height field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Year of Origin Field </td>
   <td style="text-align:left;"> Name of tree year of origin field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Growth Rate Field </td>
   <td style="text-align:left;"> Name of tree growth rate field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Misc Field </td>
   <td style="text-align:left;"> Name of miscellanious notes field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> optional </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Crew Field </td>
   <td style="text-align:left;"> Name of crew field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Date Field </td>
   <td style="text-align:left;"> Name of date field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool5.png" alt="05 - Check Required Fields [Age] Tool Dialogue." width="340" />
<p class="caption">(\#fig:unnamed-chunk-10)05 - Check Required Fields [Age] Tool Dialogue.</p>
</div>

#### `06-Check Plot IDs`

**Purpose-** Check the validity of fixed/age/prism plot IDs against the IDs of the primary set of plot locations.

**Code-** This ArcGIS tool is built from the Python Script [Check Plot IDs](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/06_check_plot_ids.py)

<table>
<caption>(\#tab:unnamed-chunk-11)Check Plot IDs Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Plot Centers </td>
   <td style="text-align:left;"> Primary set of plot locations </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot Center ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Prism Plots </td>
   <td style="text-align:left;"> Prism plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Prism Plot ID Field </td>
   <td style="text-align:left;"> Prism plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plots </td>
   <td style="text-align:left;"> Fixed plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age Plots </td>
   <td style="text-align:left;"> Age plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool6.png" alt="06 - Check Plot IDs Tool Dialogue." width="341" />
<p class="caption">(\#fig:unnamed-chunk-12)06 - Check Plot IDs Tool Dialogue.</p>
</div>

#### `07-Check Fixed Offsets`

**Purpose-** Checks fixed plot IDs against the ID of the nearest plot center. If the nearest plot center has the same ID as the fixed plot ID, the fixed plot is considered to have the correct ID. If the nearest plot center has a different ID than the fixed plot, the fixed plot will be flagged and the ID should be checked manually.

**Code-** This ArcGIS tool is built from the Python Script [Check Fixed Offsets](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/07_check_fixed_offsets.py)

<table>
<caption>(\#tab:unnamed-chunk-13)Check Fixed Offsets Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Plot Centers </td>
   <td style="text-align:left;"> Primary set of plot locations </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot Center ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plots </td>
   <td style="text-align:left;"> Fixed plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool7.png" alt="07 - Check Fixed Offsets Tool Dialogue." width="344" />
<p class="caption">(\#fig:unnamed-chunk-14)07 - Check Fixed Offsets Tool Dialogue.</p>
</div>

#### `08-Verify Age Plots`

**Purpose-** Checks prescribed age plots against collected age plots. Returns the prescribed age plots with a flag field indicating if an age plot was collected.

**Code-** This ArcGIS tool is built from the Python Script [Verify Age Plots](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/08_verify_age_plots.py)

<table>
<caption>(\#tab:unnamed-chunk-15)Verify Age Plots Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Plot Centers </td>
   <td style="text-align:left;"> Primary set of plot locations </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot Center ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Flag Field </td>
   <td style="text-align:left;"> Name of field which flags plots for age tree collection </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age Plots </td>
   <td style="text-align:left;"> Age plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool8.png" alt="08 - Verify Age Plots Tool Dialogue." width="342" />
<p class="caption">(\#fig:unnamed-chunk-16)08 - Verify Age Plots Tool Dialogue.</p>
</div>

#### `09-Check Prism/Fixed Match`

**Purpose-** Checks to make sure there is a prism plot for every fixed plot and that there is a fixed plot for each prism plot. This is accomplished by comparing unique sets of plot IDs present for each feature class and populating fields indicating if this relationship holds true.    Also checks which fixed plot is closest to each prism plot. If the closest fixed plot does not have the same plot ID as the prism plot then the prism plot is flagged for review.

**Code-** This ArcGIS tool is built from the Python Script [Check Prism/Fixed Match](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/09_check_prism_fixed_match.py)

<table>
<caption>(\#tab:unnamed-chunk-17)Check Prism/Fixed Match Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Prism Plots </td>
   <td style="text-align:left;"> Prism plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot ID </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plots </td>
   <td style="text-align:left;"> Fixed plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Plot ID </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool9.png" alt="09 - Check Prism/Fixed Match Tool Dialogue." width="338" />
<p class="caption">(\#fig:unnamed-chunk-18)09 - Check Prism/Fixed Match Tool Dialogue.</p>
</div>

#### `10-Remove Duplicates`

**Purpose-** Checks for and removes duplicate geometry from prism, fixed, and age plots. Fixed plots are checked for duplicate plot IDs in addition to duplicate geometry.

**Code-** This ArcGIS tool is built from the Python Script [Remove Duplicates](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/10_remove_duplicates.py)

<table>
<caption>(\#tab:unnamed-chunk-19)Remove Duplicates Tool Parameters</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Parameter </th>
   <th style="text-align:left;"> Description </th>
   <th style="text-align:left;"> Type </th>
   <th style="text-align:left;"> Required </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Prism Plots </td>
   <td style="text-align:left;"> Prism plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plots </td>
   <td style="text-align:left;"> Fixed plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Fixed Plot ID Field </td>
   <td style="text-align:left;"> Name of plot ID field </td>
   <td style="text-align:left;"> Field </td>
   <td style="text-align:left;"> required </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Age Plots </td>
   <td style="text-align:left;"> Age plot feature class </td>
   <td style="text-align:left;"> Feature Class or Feature Layer </td>
   <td style="text-align:left;"> required </td>
  </tr>
</tbody>
</table>

<div class="figure">
<img src="images/QA_tool10.png" alt="10 - Remove Duplicates Tool Dialogue." width="339" />
<p class="caption">(\#fig:unnamed-chunk-20)10 - Remove Duplicates Tool Dialogue.</p>
</div>



### Summary Tools

## Reporting Tools
