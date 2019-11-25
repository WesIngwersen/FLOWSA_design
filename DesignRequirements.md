# Functional requirements
- Provide a function to return a table for a group of flows by sector with and without allocation
- Use data sources with highest location (to county) and contextual resolution available
- Identify flows as elementary, technosphere, or waste flow types 
- Use FIPS for location, NAICS for sectors
- Allow attribution by commodity or industry
- Provide data reliability, geographical, technological and data collection and data quality scores
- Provide data source and allocation source metadata 

# Technical requirements
- Python 3x package, using `pandas` for data reshaping, `requests` for API calls, `pyarrow` for parquet data storage,
enable easy github install
- Transparent data acquisition, processing, simple API returning standard formats like [stewi](https://github.com/USEPA/standardizedinventories)
- Look to connect to or build off other open source code 
- Use common functions for data reshaping whenever possible
- Unit tests like [fedelemflowlist](https://github.com/USEPA/Federal-LCA-Commons-Elementary-Flow-List)
- Use [PEP 8](https://www.python.org/dev/peps/pep-0008/) as style guide 
- Comply with EPA LMMD SOPs 

## Potential resources
[census](https://github.com/datamade/census), a python wrapper for Census API

[usfertilizer](https://cran.r-project.org/web/packages/usfertilizer/index.html), Compiled and cleaned the county-level estimates of fertilizer, nitrogen and phosphorus from USGS
 

