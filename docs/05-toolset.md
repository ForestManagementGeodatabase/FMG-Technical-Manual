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


|Parameter          |Description                                        |Type          |Required |
|:------------------|:--------------------------------------------------|:-------------|:--------|
|Destination Folder |Folder in which output .gdb will be created        |Folder        |required |
|Fixed Plots        |Fixed plots (shapefile or feature class)           |Feature Class |required |
|Prism Plots        |Prism plots (shapefile or feature class)           |Feature Class |required |
|Age Plots          |Age plots (shapefile or feature class)             |Feature Class |required |
|Plot Centers       |Plot center locations (shapefile or feature class) |Feature Class |required |

<div class="figure">
<img src="images/QA_tool1.png" alt="01 - Prep QA Workspace Tool dialogue." width="335" />
<p class="caption">(\#fig:unnamed-chunk-1)01 - Prep QA Workspace Tool dialogue.</p>
</div>

#### `02-Check Required Fields [Plot Center]`

**Purpose-** Checks the plot center input for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Plot Center)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/02_check_required_fields_center.py)


|Parameter       |Type                                                             |Description                    |Required |
|:---------------|:----------------------------------------------------------------|:------------------------------|:--------|
|Plot Centers    |Plot center locations (feature class)                            |Feature Class or Feature Layer |required |
|Plot ID Field   |Name of plot ID field                                            |Field                          |required |
|Plot Type Field |Name of field containing site type flags (age, walkthrough, etc) |Field                          |required |

<div class="figure">
<img src="images/QA_tool2.png" alt="02 - Check Required Fields [Plot Center] Tool Dialogue." width="339" />
<p class="caption">(\#fig:unnamed-chunk-2)02 - Check Required Fields [Plot Center] Tool Dialogue.</p>
</div>

#### `03-Check Required Fields [Prism]`

**Purpose-** Checks prism plots for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Prism)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/03_check_required_fields_prism.py)


|Parameter    |Description                |Type                           |Required |
|:------------|:--------------------------|:------------------------------|:--------|
|fc_prism     |Prism plot feature class   |Feature Class or Feature Layer |required |
|plot_name    |Name of plot ID field      |Field                          |required |
|species_name |Name of tree species field |Field                          |required |
|dia_name     |Dialog Reference           |Field                          |required |
|class_name   |Name of canopy class field |Field                          |required |
|health_name  |Name of tree health field  |Field                          |required |
|misc_name    |Name of notes field        |Field                          |required |
|crew_name    |Name of crew field         |Field                          |required |
|date_name    |Name of date field         |Field                          |required |

<div class="figure">
<img src="images/QA_tool3.png" alt="03 - Check Required Fields [Prism] Tool Dialogue." width="341" />
<p class="caption">(\#fig:unnamed-chunk-3)03 - Check Required Fields [Prism] Tool Dialogue.</p>
</div>

#### `04-Check Required Fields [Fixed]`

**Purpose-** Checks fixed plots for presence of required fields and for missing values in those fields. This tool will rename provided fields as necessary to match the FMG schema.

**Code-** This ArcGIS tool is built from the Python Script [Check Required Fields (Fixed)](https://github.com/ForestManagementGeodatabase/FMG-toolbox/blob/main/fmgpy/qa/04_check_required_fields_fixed.py)


|Parameter                |Description                                                          |Type                           |Required |
|:------------------------|:--------------------------------------------------------------------|:------------------------------|:--------|
|Fixed Plots              |Fixed plot feature class                                             |Feature Class or Feature Layer |required |
|Plot ID Field            |Name of plot ID field                                                |Field                          |required |
|Canopy Closure Field     |Name of overstory closure field                                      |Field                          |required |
|Overstory Height Field   |Name of overstory height field                                       |Field                          |required |
|Understory Height Field  |Name of understory height range field                                |Field                          |required |
|Understory Cover Field   |Name of understory cover field                                       |Field                          |required |
|Understory Species Field |Name of understory species field (if multiple, choose the first one) |Field                          |required |
|Ground Species Field     |Name of ground species field (if multiple, choose the first one)     |Field                          |required |
|Misc Field               |Name of miscellanious notes field                                    |Field                          |optional |
|Crew Field               |Name of crew field                                                   |Field                          |required |
|Date Field               |Name of date field                                                   |Field                          |required |
|                         |                                                                     |                               |         |

<div class="figure">
<img src="images/QA_tool4.png" alt="04 - Check Required Fields [Fixed] Tool Dialogue." width="336" />
<p class="caption">(\#fig:unnamed-chunk-4)04 - Check Required Fields [Fixed] Tool Dialogue.</p>
</div>

### Summary Tools?? Scripts??? Hello?

## Reporting Tools
