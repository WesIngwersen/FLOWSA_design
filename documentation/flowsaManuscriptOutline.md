# Title
FLOWSA: A python package attributing resource use, waste, emissions, and other flows to industries

# Authors
Catherine Birney (Office of Research and Development, Center for Environmental Solutions and Emergency Response, US Environmental Protection Agency, Cincinnati, Ohio, USA), Wesley Ingwersen (Office of Research and Development, Center for Environmental Solutions and Emergency Response, US Environmental Protection Agency, Atlanta, Georgia, USA), Ben Young (Eastern Research Group, Lexington, Massachusetts, USA), Mo Li (General Dynamics Information Technology, Falls Church, VA, USA), Melissa Conner (Global Quality Corp, Covington, Kentucky, USA), Jacob Specht (Global Quality Corp, Covington, Kentucky, USA)

# Abstract
FLOWSA is a python package that attributes resources, wastes, emissions, losses, and other movements of mass, energy, monetary or human resources – collectively called flows – to industries. Models can be developed to capture flows to and from the environment and industries, as well as transfers between industry sectors. Data on flow generation and use by activity are imported transparently from providers and modified to a standardized format, but are otherwise numerically unchanged in preparation for modeling. Multiple datasets are often used to drive an industry attribution model, along with crosswalks assigning reported activities to sectors. Users can develop flow totals by sector models by applying user specified rules to the activity flows data inputs. Modification to methodological, geographical, and temporal parameters will produce varying totals by sector model results, enabling comparison of the impact of user rules on sector attribution. The standardized data outputs from these models have been used as environmental data inputs into the latest version of the USEEIO model, a life cycle model of US goods and services in ~400 categories. This communication demonstrates FLOWSA’s capability by describing models for US industry use of water, land, and employment with varying methodologies. FLOWSA is publicly available on GitHub and many of the data outputs are available on the EPA Data Commons.

# Keywords

# Introduction

### Scientific contribution statement
FLOWSA is a transparent and open-source environment that is convenient and easy to use. Creates standardized totals by sector outputs...


# Material and methods

## Description of General Approach
Flowsa attributes resource use, waste, emissions, and loss to North American Industrial Classification codes (NAICS). It produces standard tabular formats with sector attributions out of numerous data sources. Flowsa is publicly availble on github, enabling users access to the most up-to-date data. The data sources used to build the models discussed in this manuscript are available in the repository.
  - Flexible
  - Updateable
  - Method yamls with methodology instructions written by user

### FlowByAcitivity
  - Imports data, with the exception of formatting, unmodified
  - formats to standardized output
  - flowbyactivity.py houses generalized functions for calling and parsing data
  - dataset specific functions maintained in seperate script

### FlowBySector

### Data Storage
  - local repository
  - remote repository

## Integration with other EPA tools
Flowsa is part of a larger family of tools. This flow diagram (insert...) depicts how the tools, which are written in a mix of languages. All code is available on github and together, work to output the industry results.

### Federal LCA Commons Elementary Flow List
The Federal LCA Commons Elementary Flow List, fedefl, a Python package, which creates standard flow names for data between the different packages.
  
### ESUPY

### Standardized Emission and Waste Inventories (StEWI)
The Standardized Emission and Waste Inventories (StEWI) is a series of four python packages which process emission and waste generation inventory data for U.S. facilities in standard formats for life cycle assessment (Citation).
The _stewi_ module parses publicly reported data from EPA datasets including the Toxic Release Inventory (TRI), National Emissions Inventory (NEI), Discharge Monitoring Reports (DMR), Resource and Conservation Recovery Act Bienneial Hazardous Waste Reports (RCRAInfo), and others, into standard Pandas dataframes.
Two additional modules, _facilitymatcher_ and _chemicalmatcher_, support the alignment of facility identifiers and chemical flow names across datasets. These modules ensure that flow data reported across multiple inventories are aligned with the same point source facility and conform to standardized flow nomenclature.
Data from these three modules are then compiled in _stewicombo_ to generate combined inventories by facility.
Inventories developed in both _stewi_ and _stewicombo_ are accessible in FLOWSA for use in generating FlowBySector datasets. Data are reformatted and aggregated and assigned to NAICS based on those reported in the _facilitymatcher_. Additional processing can be applied as needed to further process the data from StEWI, for example to limit the scope of the FBS.


## Specific Model Methodology

### National Water Withdrawal Totals By Industry
Four models generated and formatted in FLOWSA. The models estimate water withdrawal for either 2010 or 2015 by industry. Additionally, methodology for how direct water withdrawal is allocated to 6 digit NAICS is modified for industrial, mining, and crop irrigation by varying data sources.

### National Land Occupation Totals By Industry

### National Employment Totals By Industry

### National Criteria and Hazardous Air Pollutant Emissions By Industry (?)


# Results

## Available Datasets
### FlowByActivity
### FlowBySector

# Discussion

Flowsa is a new tool and was built to enable the move away from static csv satellite tables and instead buid dynamic, easily updateable tables for use in the generation of IO models.

The main takeaway is less about the specific results and more on the ability and flexibility of the package. Flowsa enables comparision of model output between different years using the same methods. Flows allows for convenenient and rapid exploration of water use LCA's. Flowsa also addresses the need for a dynamic method of creating satellite tables for use in USEEIO.

## Examples of use

### USEEIOR
Water, land, employment, and emission's data created in FLOWSA are used in USEEIOR's v2.0.

## Limitations
  - Data suppression

# Conclusions

# Appendices

# Acknowledgements





