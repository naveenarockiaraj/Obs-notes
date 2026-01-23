Intergrated gooddata in legacy RA application to help admins access analytics dashboard. 

There are 3 dashboards and the navbar design should be provided.
Authorization is not handled currently but it can be handled in Gooddata platform.



Approach :1
we inserting the workspaceid, dashbordid through the .env and we expose the api form .env

Approach : 2
we run script  to store the equalent  workspaceid and dashbordId for the organizations, throug that we can expose the api 

if we using the script to feed the workspace id and dashbord id, we do it manually or from where we get those ids 



(for now we are in single tenet org if it goes for multi tenet   )


download_csv_endpoint_and_permission_for_apis_based_on_connection_type

gooddata_analytics_dashboard_permission_endpoint 