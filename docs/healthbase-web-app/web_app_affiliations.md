# Affiliations

An affiliation in Healthbase implies a relationship between entities. These could be between HCOs \(Healthcare Organizations\) and individuals, HCPs \(Healthcare professionals\) or HCOs to HCOs. Tied to each relationship is also a score \(between 1-100\) that indicates the strength of that relationship.

Affiliation relationship is derived from the following sources:

* Real-world claims data
* Regulatory filings
* Tax filings
* Deep web crawls 
* + many more

Affiliations follow a hierarchical graph structure. As the figure below shows, relationships between HCOs and HCPs aren't always simple. Healthbase captures the links along with the strength of these linkages.

![Hierarchy](https://raw.githubusercontent.com/CompileInc/healthbase-knowledge-base/master/docs/images/Hierarchy.png)

The algorithm also “rolls-up” every entity to a parent, based on certain criteria \(e.g. ownership or clinical relationship\)

## Affiliations for health systems

Under the [health systems detail](https://app.gethealthbase.com/explore/detail/HS:E416011702/) page, the affiliations listed are for all the “child’ entities for that health system. These include facilities and practitioners. Both parent and intermediary health systems listing the child entities for affiliations. Note that child affiliations “flow down”, i.e. an intermediary health system will only list affiliations that are its children.

## Affiliations for all other entities

For [all other entities](https://app.gethealthbase.com/explore/detail/H:521302/), the affiliation listing details immediate affiliations, i.e. within a single degree connection.

## Health system hierarchy

Healthbase profiles health systems at a very detailed level. Instead of just linking all facilities and practitioners to a parent, Healthbase maps out the true ownership or clinical network for a health system, with sub health systems along the path.

