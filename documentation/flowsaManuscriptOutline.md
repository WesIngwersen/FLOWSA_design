# Title
FLOWSA: A python package attributing resource use, waste, emissions, and other flows to industries

# Authors
Catherine Birney (Office of Research and Development, Center for Environmental Solutions and Emergency Response, US Environmental Protection Agency, Cincinnati, Ohio, USA), Wesley Ingwersen (Office of Research and Development, Center for Environmental Solutions and Emergency Response, US Environmental Protection Agency, Atlanta, Georgia, USA), Ben Young (Eastern Research Group, Lexington, Massachusetts, USA), Mo Li (General Dynamics Information Technology, Falls Church, VA, USA), Melissa Conner (Global Quality Corp, Covington, Kentucky, USA), Jacob Specht (Global Quality Corp, Covington, Kentucky, USA)

# Abstract
FLOWSA is a python package that attributes resources, wastes, emissions, losses, and other movements of mass, energy, monetary or human resources – collectively called flows – to industries. Models can be developed to capture flows to and from the environment and industries, as well as transfers between industry sectors. Data on flow generation and use by activity are imported transparently from providers and modified to a standardized format, but are otherwise numerically unchanged in preparation for modeling. Multiple datasets are often used to drive an industry attribution model, along with crosswalks assigning reported activities to sectors. Users can develop flow totals by sector models by applying user specified rules to the activity flows data inputs. Modification to methodological, geographical, and temporal parameters will produce varying totals by sector model results, enabling comparison of the impact of user rules on sector attribution. The standardized data outputs from these models have been used as environmental data inputs into the latest version of the USEEIO model, a life cycle model of US goods and services in ~400 categories. This communication demonstrates FLOWSA’s capability by describing models for US industry use of water, land, and employment with varying methodologies. FLOWSA is publicly available on GitHub and many of the data outputs are available on the EPA Data Commons.

# Keywords
Life-cycle assessment, Environmental impact, Circular economy

# Introduction

### Scientific contribution statement
FLOWSA is a transparent and open-source environment that is convenient and easy to use. Creates standardized totals by sector outputs...


# Material and methods
Flowsa can be modified to run models for different years, resource inputs, and data sources. 

Flowsa attributes resource use, waste, emissions, and loss to North American Industrial Classification codes (NAICS). It produces standard tabular formats with sector attributions out of numerous data sources. Flowsa is publicly availble on github, enabling users access to the most up-to-date data. The data sources used to build the models discussed in this manuscript are available in the repository.
  - Flexible
  - Updateable
  - Method yamls with methodology instructions written by user

## Software and Availability
Flowsa is written in the Python programming language and is publicly-available on github, enabling users access to the most up-to-date data.. Python was chosen as it is freely available on all platforms and is used widely throughout the literature (cite examples). The benefits of using Python are that the code is easily updateable, easy to modify, and transparent, open-source, convienent, easy to use. Flowsa requires a number of pre-defined, existing packages available through the open-source nature of python.

## Model Outputs
*instert the flow diagram hosted on flowsa_design - update to include link to esupy

Flowsa generates two types of outputs:
1. Flow-By-Activity datasets: Import environmental (and other types of) data from publicly available datasets, formatting the data into a standardized table, a Flow-By-Activity dataset. Flow-By-Activity datasets are largely unchanged from the original data source, with the exception of formatting.
2. Flow-By-Sector datasets: Attribute resource use, waste, emissions, and loss to industries, in the form of North American Industrial Classification (NAICS) Codes, formatting the data into a standardized Flow-By-Sector table. These new datasets are generally created using multiple FlowByActivity datasets and a set of rules defined by the user. 

### Generating Flow-By-Activity Datasets
  - Imports data, with the exception of formatting, unmodified
  - formats to standardized output
  - flowbyactivity.py houses generalized functions for calling and parsing data
  - dataset specific functions maintained in seperate script
 Write "instructions" for how to find the original data source being imported (i.e. a webpage). Write the instructions in a yaml file in the flowbyactivitymethods folder. Write any functions needed to help pull, parse, and format the data in a single script with the same SourceName as that used in the flowbyactivitymethods yaml. Any functions written in this script should be called on in the method yaml. Generate the Flow-By-Activity datset by running flowbyactivity.py. This file houses the script that calls on the information in the flowbyactivitymethods yaml and the functions specific to a data source. Update the source catalog yaml with the information specific to the dataset.
 
 crosswalk

### Generating Flow-By-Sector Datasets
Write "instructions" for how to attribute environmental data in the Flow-By-Activity datasets to North American Industrial Classification (NAICS) Codes. Write out the instructions in a yaml file in the flowbysectormethods folder. Data in a Flow-By-Activity dataset are converted to NAICS based on the values in the 'FlowName' column. There are two options for identifying which 'FlowNames' to allocate in an activity set in the method yaml. The first method is to manually list out the FlowNames in the flowbysectormethods yaml. The second option is to create a csv with FlowNames and the activity set they belong to, saving the csv in the flowbysectoractivitysets folder.Add any functions required to help allocate a Flow-By-Activity dataset to NAICS in the same py file used to generate the Flow-By-Activity. These functions are optional, dependent on the data source. Generate the Flow-By-Sector dataset by running flowbyfunctions.py, the script that calls on the information and functions specified in the flowbysectormethods yaml.

### User defined components
** Differentiate between users and developers **
Users can modify the Flow-By-Activity and Flow-By-Sector methodologies to determine the impact on totals by sector modeling calculations. Flow-By-Activity crosswalks can be updated to reflect varying levels of aggregation or user-created activity to industry associations. Flow-By-Sector models can be modified to change the data sources used for activity to industry allocation. Users can modify geographic levels, temporal parameters, and industry aggregation. All of these changes are made to a single method file, allowing for a transparent means of testing. 

Flowsa requires user generated inputs, as defined in method yamls. Users will create their own crosswalks.

### Data Storage
Flow-By-Activity and Flow-By-Sector output files for each version of flowsa, as released on Github, are stored on Data Commons, an Amazon AWS s3 server. Data files are stored in parquet format, as this file type is smaller and faster to read than traditional file types, such as a csv. Storing files on a remote server enables use of these files by other tools, such as useeior, without requiring a user to have python installed.

Users working as developers will store all FlowByActivity and FlowBySector files in a local repository and have the option to download the remote files rather than recreating them. 


## Integration with other EPA tools
Flowsa is part of a larger family of tools that make up the Life Cycle Assessment (LCA) tool ecosystem. This flow diagram (insert...) depicts the relationship between the tools, which are written in a mix of languages. All code is available on github and together, work to output the industry results.

### Federal LCA Commons Elementary Flow List
The Federal LCA Commons Elementary Flow List, fedefl, a Python package, which creates standard flow names for data between the different packages.
  
### ESUPY
ESUPY is Python package that hosts common functions for use in Python tools within the LCA tool ecosystem. ESUPY does not produce unique outputs. 

### Standardized Emission and Waste Inventories (StEWI)
The Standardized Emission and Waste Inventories (StEWI) is a series of four python packages which process emission and waste generation inventory data for U.S. facilities in standard formats for life cycle assessment (Citation).
The _stewi_ module parses publicly reported data from EPA datasets including the Toxic Release Inventory (TRI), National Emissions Inventory (NEI), Discharge Monitoring Reports (DMR), Resource and Conservation Recovery Act Bienneial Hazardous Waste Reports (RCRAInfo), and others, into standard Pandas dataframes.
Two additional modules, _facilitymatcher_ and _chemicalmatcher_, support the alignment of facility identifiers and chemical flow names across datasets. These modules ensure that flow data reported across multiple inventories are aligned with the same point source facility and conform to standardized flow nomenclature.
Data from these three modules are then compiled in _stewicombo_ to generate combined inventories by facility.
Inventories developed in both _stewi_ and _stewicombo_ are accessible in FLOWSA for use in generating FlowBySector datasets. Data are reformatted and aggregated and assigned to NAICS based on those reported in the _facilitymatcher_. Additional processing can be applied as needed to further process the data from StEWI, for example to limit the scope of the FBS.


## Specific Model Methodology

To demonstarte the flexibility of flowsa, this manuscript covers methodology for attributing resource flows to industry for water, land, employment and ...?

### National Water Withdrawal Totals By Industry
In the US, industries are not required to report water withdrawals by any federal mandate, and therefore water withdrawals and use by industry must be estimated using other data sources that provide more aggregate water use estimates or by using non-water use data on industry activity that correlates with industry water use. Differences in industry-level direct water withdrawal are compared by varying datasets used and methods of attribution to industries.

Four models generated and formatted in FLOWSA. The models estimate water withdrawal for either 2010 or 2015 by industry. Additionally, methodology for how direct water withdrawal is allocated to 6 digit NAICS is modified for industrial, mining, and crop irrigation by varying data sources.

### National Land Occupation Totals By Industry
There is no single source for detailed land use in the US. The USDA ERS releases the Major Land Use report every X years, which covers XX land use categories. In flowsa, the MLU is the main land use data source, with the totla published value of land use remaining a constant. In addition to these XX categories, additional data sources are imported to further define US land use occupation. The EIA's Commercial Buildings Energy Consumption Survey (CBECS) and Manufcaturing Energy Consumption Survey (MECS) report land occupation by principal building activity. The BLS Public Land Survey (PLS) reports land use for mining activities. 

### National Employment Totals By Industry

### National Criteria and Hazardous Air Pollutant Emissions By Industry (?)


# Results

## Available Datasets
### FlowByActivity
### FlowBySector

# Discussion
Environmental researchers spend time importing and cleaning datasets. Flowsa is a platform that imports commonly used data sources and outputs the data in a stanard format that can be easily manipulated for research purposes. 

Flowsa is a new tool and was built to enable the move away from static csv satellite tables and instead buid dynamic, easily updateable tables for use in the generation of IO models.

The main takeaway is less about the specific results and more on the ability and flexibility of the package. Flowsa enables comparision of model output between different years using the same methods. Flows allows for convenenient and rapid exploration of water use LCA's. Flowsa also addresses the need for a dynamic method of creating satellite tables for use in USEEIO.

Flowsa allows for methodological variation impacts of direct resource use for up to XX industries. 

 All the data used and modeling performed is open source and available in the respective Github repositories for these tools.

Data quality assessment is further used to compare reliability, temporal, geographic and technological correlation with the model purpose, and the data collection completeness of the results, which can be useful for interpreting the direct and life cycle water withdrawal estimates derived from the various models. The combination of quantifying the impact of methodological variation and assessing data quality provides insight into the tradeoffs of the water attribution methods and life cycle models used. 


## Examples of use

### USEEIO

EPA researchers designed US Environmentally-Extended Input-Output (USEEIO) models. This family of models is a resource for estimating potential environmental and economic impacts associated with the production or consumption of goods and services in the United States.Together, these models link economic calculations, sustainability, and environmental decision-making. 

USEEIO uses the Bureau of Economic Analysis data on economic transactions between 405 industry sectors, as well as publicly available environmental data on water, energy, air pollution, nutrients, and toxics.

The USEEIO models are generated with useeior, an R package available on github. The model is available on a public repository. This existing tool to is used to build the national resource and environemental IO models. Environmental flow sector attribution outputs from flowsa are used in the generation of IO models in USEEIOR2.0. Direct environmetnal and resource impacts for water, land, and employment are created in flowsa and loaded to USEEIOR. Using an environmentally extended input-output (EEIO) model like USEEIO traces water use through US economic industries, by linking publicly available economic industry and environmental data (Yang et al., 2017). USEEIO calculates indirect, or embedded, resource use by using USEEIO model versions constructed to incorporate annual variation in US industry structure and output along with flowsa's direct resource use estimates.

## Limitations
  - Data suppression
  - Temporal expansion

# Conclusions

# Appendices

# Acknowledgements





