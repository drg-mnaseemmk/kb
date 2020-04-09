# Diagnostic and Procedure Code Maps

## Diagnosis code

* **Table name**: `entitydiagnosiscodemap`.
* You can query for a `healthbase_id` and get all linked Diagnosis code along with meta\_data.
* Or you can query for a diagnosis code and get all linked healthbase\_ids.
* Sample:

  ```text
  select * from entitydiagnosiscodemap where healthbase_id='ASC:01C0001000' limit 10;
  ```

## Procedure code

* **Table Name** : `entityprocedurecodemap`.
* You can query for healthbase\_id and get all linked procedure code with the type and meta\_data.
* You can query for a procedure code along with type\(HCPCS/ICD\) and get all linked healthbase\_id.
* Sample:

  ```text
  select * from entityprocedurecodemap where healthbase_id='ASC:01C0001008' limit 2;
  ```

