FLOWSA: A python package attributing resource use, waste, emissions, and other flows to industries

Catherine Birney<sup>1</sup>, Wesley Ingwersen<sup>2</sup>, Ben Young<sup>3</sup>, Mo Li<sup>4</sup>, Melissa Conner<sup>5</sup>, Jacob Specht<sup>5</sup>

<sup>1</sup>Office of Research and Development, Center for Environmental Solutions and Emergency Response,
US Environmental Protection Agency, Cincinnati, Ohio, USA \
<sup>2</sup>Office of Research and Development, Center for Environmental Solutions and Emergency Response,
US Environmental Protection Agency, Atlanta, Georgia, USA \
<sup>3</sup>Eastern Research Group, Lexington, Massachusetts, USA \
<sup>4</sup>General Dynamics Information Technology, Falls Church, VA, USA \
<sup>5</sup>Global Quality Corp, Covington, Kentucky, USA


FLOWSA is a python package that attributes resources, wastes, emissions, losses, and other movements of mass, energy, monetary or human resources -- collectively called flows -- to industries. Models can be developed to capture flows to and from the environment and industries, as well as transfers between industry sectors. Data on flow generation and use by activity are imported transparently from providers and modified to a standardized format, but are otherwise numerically unchanged in preparation for modeling. Multiple datasets are often used to drive an industry attribution model, along with crosswalks assigning reported activities to sectors. Users can develop flow totals by sector models by applying user specified rules to the activity flows data inputs. Modification to methodological, geographical, and temporal parameters will produce varying totals by sector model results, enabling comparison of the impact of user rules on sector attribution. The standardized data outputs from these models have been used as environmental data inputs into the latest version of the USEEIO model, a life cycle model of US goods and services in ~400 categories. This communication demonstrates FLOWSA's capability by describing models for US industry use of water, land, and employment with varying methodologies. FLOWSA is publicly available on GitHub and many of the data outputs are available on the EPA Data Commons.
