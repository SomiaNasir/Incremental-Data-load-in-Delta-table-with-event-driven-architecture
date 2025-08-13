# Incremental-Data-load-in-Delta-table-with-event-driven-architecture  

Objectives:  
Setup an event driven pipeline using databricks and GCP. The files should be received at Google storage which will trigger the pipeline to process the data.  
  
Architecture Diagram:  





Setting up:  
This project was started with setting up GCP and databricks using the free tier version. Databricks is provided as a service in GCP and can be accessed from GCP console. A new workspace in databricks was created which also triggers the formation of a metastore in the same region.  
A metastore is the top-level container for data in Unity Catalog. Unity Catalog metastores register metadata about securable objects (such as tables, volumes, external locations, and shares) and the permissions that govern access to them. Each metastore exposes a three-level namespace (catalog.schema.table) by which data can be organized.  
  
<img width="1128" height="197" alt="image" src="https://github.com/user-attachments/assets/f3d47a7c-a90f-414b-8892-4fb770aa8719" />  

<img width="620" height="290" alt="image" src="https://github.com/user-attachments/assets/d2e21aab-e96b-4040-8525-50f07a28e71c" />




Create Volume:  
<img width="959" height="929" alt="image" src="https://github.com/user-attachments/assets/9e96b554-9803-4860-b40b-2c21ad977469" />

