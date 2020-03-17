# Index Exchange API Redundancy case study 

### This section will discuss a very high level of some redundancy cases I experienced working on API's at index exchange

I worked on developing Microservices at Index exchange. This involved building different API's and stitching them together. We ran into cases where we faced condition checking redundancy. For instance, when we were passing header tokens among API's.

# Problems we faced

1. We had middleware validating header tokens, did we also need to validate them in our route handler?

2. Did other API's receiving the header tokens also need to validate them? (web to data API)

3. How does this affect our unit, service, and integration testing?