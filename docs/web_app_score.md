# Scores
Affiliations in Healthbase indicate not just a relationship between HCOs (Healthcare Organizations) and HCPs (Healthcare professionals), but also the strength of this relationship.


This strength is indicated by a score between (1-100), with 1 being low and 100 being high.


The benefit of using a quantitative score to link entities are many.
* Detailed: Indicates not just affiliation but strength of affiliation
* Triangulated: Algorithmically combine signals from many sources into one easy to consume number
* Analytics read: Use the quantitative scores in your computations


Healthbase uses the following sources to compute a score:


1. Real-world claims that indicate nature of relationship and volume of claims
2. Public data that include regulatory filings, tax filings and focused web-crawls
3. CMS datasets including [Provider of Services](https://www.cms.gov/Research-Statistics-Data-and-Systems/Downloadable-Public-Use-Files/Provider-of-Services/) and other Medicare-derived data sets 


Data from disparate sources then get algorithmically weighted to arrive at a number between 1-100


## Interpreting a score
The affiliation listing page details the score between an entity and the facility or practitioner of interest. Note that the same entity would have a different score with different entities.


Score: 100: Typically an ownership relationship
Score: 99-76: Very strong affiliation
Score: 75-51: Strong affiliation
Score: <50: Moderate to low affiliation
