# Affiliations - overview

An affiliation in Healthbase implies a relationship between entities, HCOs (Healthcare Organizations) and individuals, HCPs (Healthcare professionals). An affiliation can be one of following types -  


1. `WORKS_AT`: An HCP who works at an HCO
2. `AFFILIATED`: HCP to PhysicianGroup relationship
3. `IS_LINKED_TO`: Parent entity of an HCO/HCP
4. `ACO_CONTRACTED`: ACO contract relationships
5. `OWNED_BY`: HCO ownership relationship derived from regulatory filings. These in turn, can be one of -  
    1. `Owned`
    2. `Managed`
    3. `Leased`
    4. `Affiliated`
    5. `Partnership`
    6. `JV`


Tied to each relationship is also a score (from 1-100) that indicates how strong that relationship is. Healthbase calculate scores based on multiple factors. These include:


1. Ownership relationship between two entities (HCO or HCP). Ownership information is derived from multiple sources including regulatory filings, deep web crawls and other sources.
2. Real-world claims data: By analyzing patterns across millions of claims on a real-time basis, Healthbase dynamically predicts strengths between entities


Affiliations follow a hierarchical graph structure. As the figure below shows, relationships between HCOs and HCPs aren’t always simple. Healthbase captures the links along with the strength of these linkages. The algorithm also “rolls-up” every entity to a parent, based on certain criteria (e.g. ownership or clinical relationship)




![Afffiliation graph](/images/affiliation_graph.png)

If you flatten this out as links, it looks like the table below. Healthbase’s affiliations tables are based on this flattened link structure

node_1 | node_2 | score
-------|--------|------
a      |h       |30
b      |h       |90
c      |h       |30
d      |h       |30
a      |d       |20
c      |i       |50
e      |i       |90
f      |i       |30
g      |i       |30
h      |k       |100
h      |j       |100
i      |j       |100
j      |l       |100



Depending on your use-case, you can use one of 4 tables to examine relationships. Additionally, for our power users we also provide access to a graph database which allows you to run powerful queries which can fully exploit the richness of healthbase data.


### 1. Affiliations
This table is a comprehensive list of entity affiliation relationships leveraging fewer datasets including regulatory documents and other sources. Affiliations are listed with scores and relationship type        

1. HCP - Hospital/Physician Group
2. HCO - HCO


**Relationship types**: The following types of relationships are defined between entities:  

1. `WORKS_AT`: HCP to HCO working relationships  
2. `AFFILIATED`:  HCP to PhysicianGroup affiliation  
3. `IS_LINKED_TO`: Entity parent affiliations  
4. `ACO_CONTRACTED`: ACO contract relationships  
5. `OWNED_BY`: HCO ownership relationship derived from regulatory filings  
    1. `Owned`
    2. `Managed`
    3. `Leased`
    4. `Affiliated`
    5. `Partnership`
    6. `JV`


### 2. Affiliations Advanced
This table is a comprehensive list of all entity affiliation relationships leveraging multiple datasets including real-time claims, regulatory documents and much more. Affiliations listed with scores and relationship type  

1. HCP - HCO
2. HCO - HCO
3. HCO - HCP


**Relationship types**: The following types of relationships are defined between entities:  

1. `AFFILIATED`:  HCP to PhysicianGroup affiliation
2. `IS_LINKED_TO`: Entity parent affiliations
3. `WORKS_AT`:  Working relationships for HCP’s derived from claims and other sources
4. `BILLS_TO`: Billing relationships derived from claims
5. `ACO_CONTRACTED`: ACO contract relationships
6. `OWNED_BY`: HCO ownership relationship derived from regulatory filings
    1. `Owned`
    2. `Managed`
    3. `Leased`
    4. `Affiliated`
    5. `Partnership`
    6. `JV`
7. `RELATED`:  HCO ownership relationship.
8. `SAME_AS`: BusinessEntity with same org_pac_id as a PhysicianGroup


### 3. Parent Affiliations
This table lists how strongly an HCP or HCO is connected to a parent. This table includes only details on the final parent and not the intermediaries.


And HCP or HCO could be connected to multiple parents, with strength of the link indicated by the score.  

- HCO parent:  For an HCO, we derive the final parent with a score between 0-100, 100 being the strongest.
- HCP parent:
    1. Specify  `node_1_healthbase_id`= HCP ID
    2. Take the `node_2_healthbase_id` ids for that HCP which have a high score (>75)
    3. Take the resultant set of HCOs which are strongly affiliated to the HCP. Now query the table with `node_1_healthbase_id`= HCO ID and it will give a set of `node_2_healthbase_id`s which are the final parents.
