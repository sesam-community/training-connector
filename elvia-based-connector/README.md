# Elvia

A connector simulating IFS at Elvia. The http_endpoint simulates receiving data via kafka, but you will have to use CURL with the entity below (or use the functionality in the UI, but I have never tried that).

## Sample entity
```
{
  "actual_connection_type": "EQUIPMENT",
  "actual_connection_type_db": "EQUIPMENT",
  "actual_obj_conn_lu_name": "EQUIPMENT OBJECT",
  "actual_obj_conn_lu_name_db": "EquipmentObject",
  "actual_obj_conn_rowkey": "GGGGGGGGGGGGGGGGGGGGGGGG",
  "adjusted_duration": "FALSE",
  "allow_multiple_visits": "False",
  "allow_multiple_visits_db": "FALSE",
  "authorize_code": "ELVIA_ENTR",
  "c_app_confirmed": "FALSE",
  "c_app_proposed": "FALSE",
  "c_ext_ref_key_task": "elsmartgul-HHHHHHHHHHHHHHHHHHHHHH-999999",
  "cf$_el_additional_quali": "No",
  "cf$_el_code_d": "9999 - Flåklypa",
  "cf$_el_ref_mch_code": "99^00000000000000",
  "cf$_el_resource_req": "No",
  "cf$_el_template_role_descr": "HS<=80A DM 3-fase [Ny]",
  "cf$_el_total_count_step_done": 0,
  "changed_date": "2024-02-14T12:21:04Z",
  "company": "01",
  "contact": "Reodor Felgen - 99999999",
  "contact_phone_no": "99999999",
  "created_by": "ELVIA_ENTR",
  "created_date": "2024-02-14T11:22:14Z",
  "currency_code": "NOK",
  "cust_order_type": "SEO",
  "customer_no": "11111111111",
  "delivery_address": "H",
  "description": "HS<=80A DM 3-fase [Ny]",
  "duration": 1,
  "exclude_from_scheduling": "False",
  "exclude_from_scheduling_db": "FALSE",
  "generate_note": "FALSE",
  "job_id": 1,
  "long_description": "Sponset av oljesjeiken «Ben Redic Fy Fazan», som er på ferie i traktene, bygger de racerbilen «Il Tempo Gigante» til århundrets billøp: Flåklypa Grand Prix.",
  "maint_team_site": "01",
  "note_id": 123456,
  "objevents": "StartWork^Cancel^Prepare^",
  "objstate": "RELEASED",
  "objtype": "JtTask",
  "order_no": 10,
  "organization_id": "01",
  "organization_site": "01",
  "planned_finish": "2024-02-28T08:00:00Z",
  "planned_start": "2024-02-27T23:00:00Z",
  "pre_accounting_id": 9999999,
  "priority_id": "3",
  "reference_no": "HN123123-99",
  "reported_by": "ELVIA_ENTR",
  "reported_connection_type": "EQUIPMENT",
  "reported_connection_type_db": "EQUIPMENT",
  "reported_date": "2024-02-14T11:22:14Z",
  "reported_obj_conn_lu_name": "EQUIPMENT OBJECT",
  "reported_obj_conn_lu_name_db": "EquipmentObject",
  "reported_obj_conn_rowkey": "IIIIIIIIIIIIIIIIIIIIIIII",
  "site": "01",
  "source_connection_lu_name": "TASK TEMPLATE WORK LIST",
  "source_connection_lu_name_db": "TaskTemplateRole",
  "source_connection_rowkey": "JJJJJJJJJJJJJJJJJJJJ",
  "source_ref1": "VT-USA",
  "source_ref2": "1",
  "source_ref3": "1",
  "state": "Released",
  "task_seq": 90210,
  "wo_no": 10Q18N1996Z,
  "work_type_id": "01VT-USA1776",
  "_id": "90210"
}
```
## Steps
1. Succesfully recieve an entity
   - For extra challenge, remove _id from the source above. I think Kafka adds it for us, but other systems might not.
2. Create a downstream, collect pipe
3. Is there a good field to add $last-modified?
4. Add the collect template
5. Create a share pipe
   - We don't have anywhere to share to yet, but we can look at if the pipe is well formed compared to other, existing share pipes. Creating a system can also be a part of this. The other folder in this repository has a fairly well formed example.  