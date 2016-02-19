#Applications
You can use the Calm public API using the methods described in the following sections to list or search for your applications, run flows on them, abort running flows and delete applications on Calm.

##Application List
Lists all of your applications on Calm.
###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/public/api/1/default/applications`

###Response
STATUS | RESPONSE
---------|---------
`200` | An array that lists your applications on Calm is displayed.   
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Application Search
Searches for and lists your applications on Calm. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/applications/search`

###Query Parameters
* `application_name`: Enter the full name of the application that you’re searching for. You can also enter a keyword to list all the applications that contain that keyword in their name.

###Response
STATUS | RESPONSE
---------|---------
`200` | An array containing the application that you searched for, or containing the keywords that you entered, on Calm is generated. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Application Details
Searches for the application you've queried for and lists its details such as status, unique ID, created by, blueprint details and creation details. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/api/1/default/applications`

###Query Parameters
* `name`: Enter the full name of the application that you’re searching for. You can also enter a keyword to list all the applications that contain that keyword in their name.

###Response
STATUS | RESPONSE
---------|---------
`200` | An array containing the application that you searched for on Calm is generated. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Application Flow Run
Runs the specified flow on the specified application on Calm. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/applications/flows/run`

###Query Parameters
* `application_name`: The name of the application you want to run a flow on. 
* `flow_name`: The name of the flow that you’d like to run on the specified application. 

###Response
STATUS | RESPONSE
---------|---------
`200` | The specified flow is run on the application and displays an array with the flow run UID. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Application Flow Abort
Aborts a flow that's running on an application. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/applications/flows/abort`

###Query Parameters
* `application_name`: The name of the application you want to run a flow on. 
* `flow_name`: The name of the flow that you’d like to run on the specified application.

###Response
STATUS | RESPONSE
---------|---------
`200` | The specified flow being run is aborted from the specified application and displays an array with the flow run UID. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Application Delete
Deletes the specified application from Calm. 

###Request
METHOD | URI
------------ | -------------
`POST` | `http://calm_url/public/api/1/default/applications/delete`

###Query Parameters
* `application_name`: The name of the application you’d like to delete. 

###Response
STATUS | RESPONSE
---------|---------
`200` | The application that you've specified is deleted.  
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.

##Application Run Logs
View run logs for a specific application on Calm. 

###Request
METHOD | URI
------------ | -------------
`GET` | `http://calm_url/api/1/default/applications/{application_uid}/runlogs`


###Response

STATUS | RESPONSE
---------|---------
`200` | An array with the run logs for the application you've queried for is generated.   
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.
