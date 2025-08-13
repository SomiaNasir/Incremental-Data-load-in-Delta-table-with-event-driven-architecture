# Incremental-Data-load-in-Delta-table-with-event-driven-architecture  

## Objectives:  
Setup an event driven pipeline using databricks and GCP. The files should be received at Google storage which will trigger the pipeline to process the data.  
  
## Architecture Diagram:  





## Setting up:  
This project was started with setting up GCP and databricks using the free tier version. Databricks is provided as a service in GCP and can be accessed from GCP console. A new workspace in databricks was created which also triggers the formation of a metastore in the same region.  
A metastore is the top-level container for data in Unity Catalog. Unity Catalog metastores register metadata about securable objects (such as tables, volumes, external locations, and shares) and the permissions that govern access to them. Each metastore exposes a three-level namespace (catalog.schema.table) by which data can be organized.  
  
<img width="1128" height="197" alt="image" src="https://github.com/user-attachments/assets/f3d47a7c-a90f-414b-8892-4fb770aa8719" />  

<img width="620" height="290" alt="image" src="https://github.com/user-attachments/assets/d2e21aab-e96b-4040-8525-50f07a28e71c" />

We can see the top 3 buckets setup by databricks in google cloud storage.  
<img width="1383" height="490" alt="image" src="https://github.com/user-attachments/assets/0d973afe-fc0b-48d1-90f8-a335005b7250" />

The last one 'for_incremental_load' is created by me to get the user input files which would land in source folder and be achived in archive folder.  

<img width="1742" height="618" alt="image" src="https://github.com/user-attachments/assets/6e9c13c7-a423-4cfc-b37b-3c031f099dee" />

  

I have described below briefly the purpuse of these buckets:  
1. Managed tables in a catalog are stored in the Unity Catalog managed storage bucket (databricks-uc-<metastore-id>), which Databricks creates for your UC metastore.  

2. External tables & volumes in a catalog are stored in custom GCS buckets you link to UC. These are not auto-created — you bring your own, set IAM, and register them in Unity Catalog.  

3. The two workspace buckets (databricks-<workspace-id> and databricks-<workspace-id>-system) are for operational and DBFS use — not for production data under Unity Catalog.  

Next up is registering 'for_incremental_load' bucket in databricks. Before adding this location as external location, we need to set up storage credentials first (catalog --> External Data --> Credentials). 
<img width="932" height="821" alt="image" src="https://github.com/user-attachments/assets/69d67969-144c-48e4-81d6-956a02433fd8" />  
After creating, it would pop up with service account email which needs to be added to the GCP IAM and granted storage permissions as follows:  
<img width="719" height="73" alt="image" src="https://github.com/user-attachments/assets/4f74b0d9-24ab-4315-b2a2-64c5a7495137" />  
Now, we can create external location in databricks (catalog --> External Data --> External Locations). Select the Credential just being set up in previous step.  
<img width="566" height="572" alt="image" src="https://github.com/user-attachments/assets/b7a49045-1868-4096-aa8c-f741054c03d5" />  
Then, a new catalog was created and in its default schema, a volume was created by selecting the external location set up in previous step and now we can see bucket's folder in databricks.  
<img width="1168" height="743" alt="image" src="https://github.com/user-attachments/assets/f221c0fd-7cd3-4412-b336-5b4e528ca33d" />









Create Volume:  
<img width="600" height="600" alt="image" src="https://github.com/user-attachments/assets/9e96b554-9803-4860-b40b-2c21ad977469" />

