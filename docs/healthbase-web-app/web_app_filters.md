# Filters


Healthbase's web app allows you to segment HCOs (Healthcare Organizations) and HCPs (Healthcare Professionals) based on firmographic and clinical characteristics. The behavior of filters in the web app varies based on the type of entities.

## Health system listing page
In the [health system listing](https://app.gethealthbase.com/explore/healthsystem/) page, you'll find the following filters:

![Filters](https://raw.githubusercontent.com/CompileInc/healthbase-knowledge-base/master/docs/images/HS_listing_filters.png)

1. **Final Parent**: This filter limits the listing to only the top-level or parent health systems. It does not display any of the intermediary health systems.
2. **Ownership**: A multiselect filter to identify health systems based on their ownership profile, i.e, not for profit, private (unlisted), private (listed) etc.
3. **Health System Presence by State**: This filter limits the listing to only those health systems that have a presence in the state(s) of interest. Note that the counts of facilities or practitioners shown in the listing denotes the affiliated entities in that region.
4. **Limit Therapeutic Area**:  This filter limits the listing to only those health systems have facilities and practitioners submitting claims in a particular ICD10 chapter in DRG propriety multichannel claims data. Note that the counts of facilities or practitioners shown in the listing denotes the number of entities submitting claims in that area.
5. **Practitioners**: Select health systems based on the number of affiliated practitioners.
6. **Facilities**: Select health systems based on the number of affiliated facilities.


The two filters, Health System Presence by State and Limit Therapeutic Area are special filters in that they apply the condition to the child entities of health systems. This allows segmentation of health systems based on characteristics of its affiliated facilities and practitioners.
The filter behavior is an **AND** functionality, i.e. as multiple filters are selected, each filter condition gets applied to the previous one.


## All other pages
For all other entities, the filter behavior is direct, i.e. selecting a particular filter applies the constraint directly on the entity.
