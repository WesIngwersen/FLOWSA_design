# Methodology



## Flow-By-Sector Derivation

Flow-by-sector datasets can be derived from the flow-by-activity datasets through the application of a flow-by-sector method. The method defines the flow class, sector definition, and geographic aggregation of the desired flow-by-sector output. Each method also defines sets of flow-by-activity datasets of two types to be used to create the flow-by-sector datasets: 1) those with the flows of the given class to be used as primary flow information, and 2) allocation datasets. Allocation datasets are defined for use with a subset of the activities in a flows dataset that require allocation and a generic allocation method is specified. For each of these datasets, the method defines sector definition, geographic aggregation, and flow names to be used.  

### Flow-By-Sector 


The steps for applying the method are defined as follows:

1. Load the fba datasets and clean, dropping qualitative notes for each record.
2. Filter the flows to include those at the specified level of geographic aggregation.
3. If fba datasets are more geographically disaggregated than the target dataset, aggregate them to the target geographic level. 
4. Add the sectors to fba datasets using the activity-to-sector crosswalks.
5. If the sectors are not the same as those defined for the target output, convert the sectors using a sector crosswalk.
6. Temporarily merge the applicable flows of the given class with the allocation flows based on sectors, and apply the specified allocation method by allocating flow amounts to sectors based on values in the allocation datasets.

### Flow Checks

A number of checks are performed during the procedure

1. Geographical summation. This check determines whether flow totals acrss more disaggregated levels of geographic aggregation within the dataset (e.g. county) add up to equal and associated more aggregated levels, like (e.g. state).  

Checks by procedural step
|Check|Step(s) When Applied|
|---|---|
|Geographical summation|2|


### Allocation methods

A number of different allocation methods are defined that can be applied to any combination of related flows of interest and associated allocation flows.






 






