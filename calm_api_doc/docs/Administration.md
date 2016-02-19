#Administration
You can use the Calm public API using the methods described in the following sections to list or search for your users and teams, conduct audits and view your budgets on Calm. 
##View Users
Lists your users on Calm based on your query. 
###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/users`

###Query Parameters
* `username`: To query for a user by username. 
* `role`: To query for users by their role.
* `uid`: To query for a user by their unique ID. 
* `state`: To query for users by their status. 
* `fullname`: To query for a user by their full name. 
* `email`:  To query for a user by their email ID. 

###Response
STATUS | RESPONSE
---------|---------
`200` | An array with the details of the user you queried for is displayed.  
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##View Teams
Lists the team your querying for on Calm along with the unique IDs of the users that are a part of the team, the unique ID, the associated budget IDs and the description. 


###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/teams`

###Query Parameters
* `name`: To query for a team by the team name. 
* `uid`: To query for a team by its unique ID. 

###Response
STATUS | RESPONSE
---------|---------
`200` | An array with the details of the team you've queried for is generated.  
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Auditing
Lists the audit events that you've queried for. 

###Request

METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/audits`

###Query Parameters
* `user_id`: To audit operations carried out by a particular user. 
* `team_id`: To audit operations carried out by a particular team.
* `budget_id`: To audit operations carried out against the specified budget.
* `application_id`: To audit operations carried out on a particular application. 
* `object_type`: To audit operations carried out on objects such as blueprints and services. Use `blueprint` and `service`, to query for blueprints and services, respectively.
* `event_type`: To query for specific events such as run, create, restart, delete, stop and start.

###Response
STATUS | RESPONSE
---------|---------
`200` | An array with the details of the audit event that you've queried for is generated and displayed. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##View Budgets
Lists the budgets that you've defined for your teams in Calm, along with their details, based on your query. 

###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/budgets`

###Query Parameters
* `created_by_user_id`: To query budgets by the user ID of the user who created it. 
* `amount`: To query budgets by the amount specified for the budget. 
* `team`: To query by the unique ID of the team that the budget has been assigned to. 
* `name`: To query for budgets by their name. 

###Response

STATUS | RESPONSE
---------|---------
`200` | An array with the details of the budget(s) that you've queried for is generated and displayed. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.
