##Diagnosis Code and Procedure Code Maps


####1. Diagnosis code ::
  * Table name : EntityDiagnosisCodeMap.
  * You can query for a healthbase_id and get all linked Diagnosis code along with meta_data. 
  * Or you can query for a diagnosis code and get all linked healthbase_ids.
  * Sample : select * from entitydiagnosiscodemap where healthbase_id='ASC:01C0001000' limit 10;


####2. Procedure code ::
  * Table Name : EntityProcedureCodeMap.
  * You can query for healthbase_id and get all linked procedure code with the type and meta_data.
  * You can query for a procedure code along with type(HCPCS/ICD) and get all linked healthbase_id.
  * Sample: select * from entityprocedurecodemap where healthbase_id='ASC:01C0001008' limit 2;

