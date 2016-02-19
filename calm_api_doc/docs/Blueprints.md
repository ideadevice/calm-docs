#Blueprints
You can use the Calm API using the methods described in the following sections to list, search for, run and delete blueprints on Calm.

##Blueprints List
Lists all of your blueprints on Calm. 

###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/public/api/1/default/blueprints`

###Response

STATUS | RESPONSE
---------|---------
`200` | An array that lists your blueprints on Calm is displayed.
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Blueprints Search
Searches for and lists your Calm blueprints.

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/blueprints/search`

###Query Parameters
* `blueprint_name`: Enter the full name of the blueprint that you’re searching for. You can also enter a keyword to list all the blueprints that contain that keyword in their name.

###Response

STATUS | RESPONSE
---------|---------
`200` | An array that contains the blueprint details is displayed. In case of a keyword search, an array containing a list of blueprints whose name contains the specified keyword is displayed. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Blueprint Run
Runs the blueprint that you’ve specified. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/blueprints/run`

###Query Parameters
* `blueprint_name`: The name of the blueprint that you’d like to run. 
* `application_name`: The name that you’d like to give to the application that is spun off from the blueprint. 
* `team_name`: The name of the team under which you’d like to create the application.
* `budget_name`: The name of the budget that has been assigned to the team. 
* `properties`: The runtime editable properties that needs to be passed to the API.

###Response

STATUS | RESPONSE
---------|---------
`200` | The blueprint that you’ve specified is executed and an array containing the UID of the application that was spun off is displayed. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Blueprint Delete
Deletes the blueprint that you've specified from Calm. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/blueprints/delete`

###Query Parameters
* `blueprint_name`: The name of the blueprint that you’d like to delete.

###Response
STATUS | RESPONSE
---------|---------
`200` | The blueprint that you’ve specified is deleted and an array with a confirmation is displayed. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##List Blueprint ID
Lists the unique ID of the blueprint that you're querying for. 

###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/blueprints`

###Query Parameters
* `name`: The name of the blueprint whose unique ID you're querying for. 
* `status`: Either ACTIVE, DEACTIVATED or DRAFT, in case you're querying for a blueprint by its status. 
* `created_by_user_id`: To query for blueprints by the unique ID of the user who created the blueprint. 

###Response
STATUS | RESPONSE
---------|---------
`200` | The blueprint(s) that you’ve queried for is listed in an array along with the unique ID and blueprint details. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Blueprint Download
Downloads the blueprint that you've specified. 

###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/download/blueprints/{blueprint_uid}`

###Response
STATUS | RESPONSE
---------|---------
`200` | Downloads the blueprint that you've specified as a JSON file while using a web browser. While using a RESTful addon or cURL, it displays an array with the blueprint JSON.  
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Blueprint Upload
Uploads a blueprint JSON file to your Calm instance. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/api/1/default/upload/blueprints`

###Query Parameters
* `blueprint_name`: The name that you'd like to give to the blueprint being uploaded.  
* `upload_file`: The path of the blueprint file that you'd like to upload. 
 

###Response
STATUS | RESPONSE
---------|---------
`200` | Uploads the blueprint file that you've specified under the name that you've given it to your Calm instance. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.
