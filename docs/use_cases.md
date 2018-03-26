All tables in Healthbase are connected through a `healthbase_id`. The `entitylookup` table has the crosswalk of `healthbase_id` and NPI or Medicare Provider ID.

## Find final parents for an HCO

**Usecase :** Identify the parent(s) details of HCO(s)  
**Input :** HCO NPIs or Medicare Provider ID (CCN)’s of interest  
**Output :** Parent of the HCO(s)  

* Use `entitylookup` table to find out the `healthbase_id` of the NPI/Provider ID.
   * Lookup by NPI
    ```
    SELECT healthbase_id FROM entitylookup WHERE identifier='npi' AND identifier_type='n'```
   * Lookup by Medicare Provider ID
    ```
    SELECT healthbase_id FROM entitylookup WHERE identifier='ProviderID' and identifier_type='p'```
   * We’ll get a `healthbase_id` based on the input and using this we can query affiliation tables.
   * The `parent_affiliations` table has the simplified form of affiliations between HCOs and HCPs with a score(0-100) which shows the strength of affiliation.
      * `node_1_healthbase_id` is child node.
      * `node_2_healthbase_id` is parent node.
   * Using the `healthbase_id` FROM the previous step, query parent_affiliations table with `node_1_healthbase_id` as input.
    ```
    SELECT * FROM parent_affiliations WHERE node_1_healthbase_id='healthbase_id'```
   * Depending on the number of claims made to or by the HCO, there could be multiple parents(node_2’s).
      * Node_2s with score > 80 are very strongly affiliated.
      * Node_2s with score between 40 and 80 are strongly affiliated.
      * Node_2s with score between 10 and 40 are weakly affiliated.
      * Node_2s with score < 10 are very weakly affiliated.
   * In most cases, we consider parent(s) which have score > 10.
   * If you are unable to find any node_2s for a node_1, it means that the HCO is operated independently and has no parent
   * Once the cut off is decided, we'll get a list of `node_2_healthbase_id`s which are the parent’s of the HCO.
   * We can use `entitysummary` table to get the details(name, address, type) of the HCO or its parents using the `healthbase_id`’s.



## Find final parents for an HCP

**Usecase** : Identify all HCOs that a HCP is affiliated with and all parents of those HCOs (directly or indirectly)  
**Input** : HCP NPIs of interest  
**Output** : HCO’s that HCP is affiliated with parents that HCO’s are part of.  

* Use `entitylookup` table to find out the `healthbase_id` of the NPI.
  ```
  SELECT healthbase_id FROM entitylookup WHERE identifier='npi' AND identifier_type='n'```
* We'll get a `healthbase_id` based on the input and using this we can query affiliation tables.
* Using the `healthbase_id` FROM the previous step, query parent_affiliations table with `node_1_healthbase_id` as input.
   ```
   SELECT * FROM parent_affiliations WHERE node_1_healthbase_id=’healthbase_id’```
* Depending on the number of claims made by the HCP, there could be multiple HCOs(node_2s).
   * Node_2s with score > 80 are very strongly affiliated.
   * Node_2s with score between 40 and 80 are strongly affiliated.
   * Node_2s with score between 10 and 40 are weakly affiliated.
   * Node_2s with score < 10 are very weakly affiliated which we can ignore in most cases.
   * Depending on the requirements, we can chose the cut off score.
* Once we have a list of HCOs a HCP is affiliated with, use the HCOs `healthbase_id`’s to query the same table to get the parents of the HCOs.

![Use case example (1&2)](/images/use_case_1_2.png)

## Identify all descendants of a final parent

**Usecase**: Identify all descendants of a parent  
**Input** : Name of parent  
**Output** : List of `healthbase_id`’s which are part of the parent.  

* Use `entitysummary` to find the `healthbase_id` of the health system.
   ```
   SELECT healthbase_id FROM entitysummary WHERE name LIKE 'health system'```
* We'll get a `healthbase_id` based on the input and using this we can query affiliation tables.
* Using the `healthbase_id` FROM the previous step, query parent_affiliations table with `node_2_healthbase_id` as input.
   ```
   SELECT * FROM parent_affiliations WHERE node_2_healthbase_id='healthbase_id'```
* Depending on the structure and influence of the health system, there could be multiple HCOs (node_1s)
   * Node_1s with score > 80 are very strongly affiliated.
   * Node_1s with score between 40 and 80 are strongly affiliated.
   * Node_1s with score between 10 and 40 are weakly affiliated.
   * Node_1s with score < 10 are very weakly affiliated which we can ignore in most cases.
   * Depending on the requirements, we can chose the cut off score.
* We'll have a list of HCOs which are affiliated to the health system.
* If we need HCPs also of the health system, then take these HCO `healthbase_id`’s and parent_affiliations table with node_2 = HCO's `healthbase_id`.
   ```
   SELECT * FROM parent_affiliations WHERE node_2_healthbase_id=’HCO healthbase_id’```
* We'll have a list of HCPs which are part of the HCOs

![Use case example 3](/images/use_case_3.png)
