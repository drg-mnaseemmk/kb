## 2018-11-12
# Enhanced web app with all active facilities
### NEW

- Under Healthsystem details page in web app , we show all active facilities owned/affiliated by them and also the practitioners affiliated with them
- Added ability to give feedback on specific data elements

### DATA ENHANCEMENTS
- Improved filtering for physicians classification and specialization

---


## 2018-09-03
# Detailed information for facilities, Healthsystems and ACOs in web app
### FEATURE

- Under Healthsystem details pages, we show all active facilities owned/affiliated by them and also the practitioners affiliated with them
- Health System profile metrics and profile information documents are added to frontend
- ACOs are added to frontend

### DATA ENHANCEMENTS
- Parent affiliations enhancements via algorithmic improvements

---

## 2018-06-08
# Search and filters in web app
### FEATURE

- Added filtering and search functionality to web app at app.gethealthbase.com

### DATA ENHANCEMENTS
- Detailed sub IDN structures for all health systems in the database


## 2018-03-21
# Web app with major facilities and practitioners
### NEW

- Released a frontend app (app.gethealthbase.com) which displays all major facilities, physicians with their affiliations

### DATA ENHANCEMENTS
- Improved parent roll ups of facilities and practitioners
- Enhancement to affiliation scoring algorithm

---


## 2017-12-19
# Geo locations
### NEW
All entity tables and `entitysummary` table now has geo location data. Following tables have two columns `geo_latitude` and `geo_longitude` which corresponds to the lat-long co-ordinates of the entity.

1. `entitysummary`
2. `aco`
3. `asc`
4. `healthsystem`
5. `hospital`
6. `practitioner`
7. `physiciangroup`
8. `businessentity`
9. `rogueentity`
10. `dialysisfacility`
11. `federallyqualifiedhealthcenter`
12. `homehealth`
13. `hospice`
14. `intermediatecarefacility`
15. `mentalhealthcenter`
16. `nursinghome`
17. `organprocurementorganization`
18. `outpatientphysicaltherapy`
19. `outpatientrehabfacility`
20. `portablexray`
21. `psychiatricresidentialtreatmentfacility`
22. `ruralhealthclinic`

---


## 2017-12-19
# Parent Affiliations
### NEW
This table lists how strongly a Healthcare Professional or Healthcare Organization is connected to a parent. This table includes only details on the final parent and not the intermediaries. Fields are -
`node_1_healthbase_id` - Child healthbase ID
`node_2_healthbase_id` - Final parent healthbase ID
`score` - A score out of 100, denoting the strength of the relationship

---
## 2017-12-18
# Diagnosis and Procedure Code for entities
### NEW

`entitydiagnosiscodemap` and `entityprocedurecodemap` tables added to either give a `healthbase_id` and get all linked diagnosis_codes and procedure_codes respectively as a result or to give a diagnosis_code/procedure_code and get a list of associated healthbase_ids as a result. Procedure code has an extra filter on procedure_code_type (HCPCS/ICD) available. `metadata` of claim counts and values are also present.

---
## 2017-11-08
# Referral relationships
### NEW
Referral relationships between HCOs and HCPs are added to healthbase - ```affiliationsreferral```. The table contains similar structure as affiliations advanced with claims related data in the ```metadata``` field.

Fields include:
- ```id```
- ```node_1_healthbase_id``` - Child healthbase id
- ```node_1_label``` - Child entity type
- ```node_1_id``` - Child id on entity table
- ```node_2_healthbase_id``` - Parent healthbase id
- ```node_2_label``` - Parent entity type
- ```node_2_id``` - Parent id on entity table
- ```metadata``` - Claim level meta-data related to the referral relationship

---
## 2017-10-31
# Improvements to Affiliations advanced
### FEATURE
Affiliations advanced table now has practitioner to entity scores available. Each score is on a scale of 0-100. 0 being low affinity and 100 being high affinity.
- ```score1``` column indicates the affinity of a practitioner to work at a specific hospital.
- ```score2``` column indicates the most affiliated practitioners to a specific entity (This column will be available in a future release)

Field `primary_relationship` is now renamed to `relationship_type`.

This release also has more granular relationship_types. The current relationship_types are:

| Relationship Type  | What it means |
| ------------- | ------------- |
| ```AFFILIATED```  | Practitioner to PhysicianGroup affiliation  |
| ```IS_LINKED_TO```  | Entity parent affiliations |
| ```WORKS_AT``` | Working relationships for practitioners derived from Claims and other sources |
| ```BILLS_TO``` | Billing relationships derived from Claims |
| ```ACO_CONTRACTED``` | ACO contract relationships |
| ```OWNED_BY``` | Entity ownership relationship derived from regulatory filings |
| ```RELATED``` | Entity to entity relationship |
| ```SAME_AS``` | BusinessEntity with same ```org_pac_id``` as a PhysicianGroup |

---
## 2017-10-20
# News alerts (Pulse)
### NEW
Healthbase now tracks news alerts on various categories and link them to entities inside the system.

Following news types are available starting today:
- **Executive Change** - <a href="https://gethealthbase.com/schema/#executivechange" target="_blank">Schema</a>
- **Facility News** - <a href="https://gethealthbase.com/schema/#facilitynews" target="_blank">Schema</a>
- **Merger And Acquisition** - <a href="https://gethealthbase.com/schema/#mergerandacquisition" target="_blank">Schema</a>
- **Data Breach**  - <a href="https://gethealthbase.com/schema/#databreach" target="_blank">Schema</a>
- **Funding**  - <a href="https://gethealthbase.com/schema/#funding" target="_blank">Schema</a>
- **Bankruptcy**  - <a href="https://gethealthbase.com/schema/#bankruptcy" target="_blank">Schema</a>
- **Labour Issue** - <a href="https://gethealthbase.com/schema/#labourissue" target="_blank">Schema</a>
- **Product Installation** - <a href="https://gethealthbase.com/schema/#productinstallation" target="_blank">Schema</a>
- **Legal Regulatory** - <a href="https://gethealthbase.com/schema/#legalregulatory" target="_blank">Schema</a>

---
## 2017-09-29
# Advanced affiliations
### NEW
Dynamic affiliations derived from multiple sources with all the available scores is now available on `affiliationsadvanced` table.

The data fields in the `affiliationsadvanced` are available <a href="https://gethealthbase.com/schema/#affiliationsadvanced" target="_blank">here</a>.
This has a similar structure to the `affiliations` table but provides you more details on the type of relationship (`primary_relationship`) and all the related `metadata` around the relationships that is derived from various sources including claims and other regulatory filings.

Please note that there will be loops in the relationships as there are billing relationships between some entities that go in either direction.

Referral relationships will be added in an upcoming release.

---
## 2017-09-20
# Added `is_entity_active` flag
### NEW
A boolean flag named `is_active_entity` flag was added to `entitysummary` table and all other entity tables such as `aco`, `hospital`, `practitioner`, etc. This flag indicates the status (active/inactive) of an entity, based on various attributes including claims and other sources.


---
## 2017-09-15
# New cross system identifier for all entities
### NEW
A new field which guarantees unique identifier for all the entities inside healthbase called `healthbase_id` has been added to all the entity tables. This simplifies the queries such as the ones below:

```sql
SELECT * from affiliations where node_1_id = 123 and node_1_label = 'hospital';
```
TO
```sql
SELECT * from affiliations where node_1_id = 'HO:452789';
```

---
## 2017-09-12
# Added Entity summary table
### NEW
Added a new table `entitysummary` which has all the entities in the system. This table has a summary including:  

- `healtbase_id`
- `name`
- `state`
- `address_line_1`
- `address_line_2`

A flag `is_active_entity` will be added to the table in the next release.
