# Presentations for FLOWSA Design

See USEEIO_team guidance here
https://github.com/WesIngwersen/USEEIO_team/tree/master/presentations

## Food MOU Symposium - April 1, 2021
```
pandoc FlowsaOverview.md WaterMethods.md FlowsaMethodologyGraphics.md --reference-doc ../../USEEIO_team/presentations/epa_template.pptx --from markdown --resource-path=../;../images/;../../USEEIO_team/presentations/;../../water_use_methods/ --to pptx --output flowsa_FoodMOUSym_20210401.pptx

```

## NCA Monthly Meeting - March 24, 2021
```
pandoc NCACover.md ../../USEEIO_Team/presentations/USEEIOOverview.md ../../USEEIO_Team/presentations/USEEIODataSources.md ../../USEEIO_Team/presentations/EnvironmentalDataScope.md Terms.md OldLimits.md flowsaTransitionSlide.md FlowsaOverview.md WaterMethods.md LandMethods.md FlowBySectorRequirements.md ../../USEEIO_Team/presentations/Disclaimer.md --reference-doc ../../USEEIO_team/presentations/epa_template.pptx --resource-path=../;../images/;../../USEEIO_team/presentations/;../../water_use_methods/ --from markdown --to pptx --output ModelingEnvFlows_NCA_20210324.pptx
```

Polishing notes in PPT
1. Add slide numbers
2. Send images (water/land graphics) to back and enlarge so height is 5.6
