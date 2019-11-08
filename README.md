# Flow Sector Attribution (FLOWSA) Models -- Design Specs

FLOWSA models will be resource use, waste, emissions, and loss sector attibution models. Adopting the term from
life cycle assessment (LCA) and [StEWI](https://github.com/USEPA/standardizedinventories), resources, wastes,
 emissions and losses are generically called _flows_. They will use models currently embedded in the USEEIO model
satellite tables ([USEEIOv1.1-Satellite Tables](https://catalog.data.gov/dataset/useeiov1-1-satellite-tables)) as a starting point,
 but they will be made standalone models to overcome current [limitations](#limitations-of-existing-models-within-useeio-and-like-satellite-table-models) and be more widely available for additional uses and
 contributions from users. Generally, these models have been limited to flow from the environment to the sectors (resource input from biosphere)
   and from the sectors to the environment (emission to the biosphere). However, FLOWSA models will also be developed so that they can be extended
 to account for flows from one sector to another (within the technosphere).

The purpose of this repository is to provide common design specifications to guide the
development of these models.

# Terms
_flows_: represent the physical movement of material or energy as input or output to or between activities.
In LCA terms these are more strictly elementary flows or waste flows, although these LCA uses will not limit the scope of FLOWSA models.

_sectors_: generally these are economic sectors generating economic activity, but are extended
here to include households and institutional end users. Using the BEA definitions in input-output
tables, these can be either _industries_ or _commodities_.

_attribution_: The sectors through which activity uses, produces or recevies the flows (input or output).

# Limitations of existing models within USEEIO and like satellite table models

## Method-related
- EEIO models like USEEIO are based on sector definitions available at various levels of aggregation generally
 created by the statistical office that created the input-output tables. The [BEA industry accounts](https://www.bea.gov/resources/methodologies/industry-primer) and schema are used by USEEIO,
  which is a NAICS-based schema. However it is not a full authoritative [NAICS](https://www.census.gov/eos/www/naics/index.html) set, and it changes over time. USEEIO satellite table models
 generally attributed flows directly to BEA-2007 benchmark schema. These flows could be more accurately attributed
 to more detailed NAICS sectors at times (like the NAICS-6 level), or in other cases should be attributed to more (than BEA)
  aggregated sectors (like [NAICS-2](https://www.census.gov/cgi-bin/sssd/naics/naicsrch?chart=2017)).

- USEEIO satellite tables attributed all flows to _industries_, but at times a _commodity_ attribution could be more appropriate.

- USEEIOv1.1 did not include households or other final-users.

- The steps needed to create a standard satellite table for EEIO were embedded in the existing models. This implied they were duplicated in 10+ models.

## Platform-related
- The Excel model platform has performance limitations with their large sizes (at times up to 100 GB)

- They did not enable github-style collaboration

- Input data (which are significant) are not pulled in a fully transparent/reproducible manner

- Input data cannot be automatically updated

- Automated use of the models is limited (to extraction or use of extracted data)

- There can be overlap between flows across different models that must be handled, which was not easily identified or handled in these platforms.
