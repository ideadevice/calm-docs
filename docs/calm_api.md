#Introduction
The Calm REST API v1 lets you interact with your Calm installation and work with your blueprints and applications on Calm. Using the Calm API, you can search for your blueprints, run them and delete blueprints that you no longer require. You can also search for applications, run flows on them and delete applications whenever you’d like to retire them. 

##Interaction
You can interact with the Calm API using one of the following modes:

* Using the command line utility cURL. 
* Using a RESTful addon for your web browser:
 Suggestions
Google Chrome: Install the Postman RESTful Client as an addon for Chrome. 
Mozilla Firefox: Install the RESTClient as an addon for Firefox. 
Safari: Install the Paw REST client on your Mac. 

##Authentication
The Calm API uses Basic Authentication to check whether you’re authorized to use the Calm API. If using cURL, you can embed your Calm credentials in the header of the API request by using the `-u` flag. If you’re using your web browser with a RESTful client addon, you can specify your Calm credentials in the **Authorization** section on the client. 

##Parameters
For `GET` requests, parameters may be submitted in the query string. For `POST` requests, parameters must be submitted in the query string, but should be submitted in the `POST` body as a JSON array while setting `Content-Type: application/json`. For example, in order to search for a blueprint, the `POST` request should follow the format
`POST http://CALM_URL/public/api/1/default/blueprints/search` with `{"blueprint_name":"mysearchkeyword"}` in the body formatted as JSON.

##Data Return
All API calls return data in JSON format by default. 

#Blueprints
You can use the Calm API using the methods described in the following sections to list, search for, run and delete blueprints on Calm.

##Blueprints List
Lists all of your blueprints on Calm. 

###Request
METHOD | URI
------------ | -------------
`GET`| `http://CALM_URL/public/api/1/default/blueprints`

###Response

STATUS | RESPONSE
---------|---------
`200`| An array that lists your blueprints on Calm is displayed.
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
`POST`| `http://CALM_URL/public/api/1/default/blueprints/search`

###Query Parameters
* `blueprint_name`: Enter the full name of the blueprint that you’re searching for. You can also enter a keyword to list all the blueprints that contain that keyword in their name.

###Response

STATUS | RESPONSE
---------|---------
`200`| An array that contains the blueprint details is displayed. In case of a keyword search, an array containing a list of blueprints whose name contains the specified keyword is displayed. 
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
`POST`| `http://CALM_URL/public/api/1/default/blueprints/run`

###Query Parameters
* `blueprint_name`: The name of the blueprint that you’d like to run. 
* `application_name`: The name that you’d like to give to the application that is spun off from the blueprint. 
* `team_name`: The name of the team under which you’d like to create the application.
* `budget_name`: The name of the budget that has been assigned to the team. 
* `properties`: The runtime editable properties that needs to be passed to the API.

###Response

STATUS | RESPONSE
---------|---------
`200`| The blueprint that you’ve specified is executed and an array containing the UID of the application that was spun off is displayed. 
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
`POST`| `http://CALM_URL/public/api/1/default/blueprints/delete`

###Query Parameters
* `blueprint_name`: The name of the blueprint that you’d like to delete.

###Response
STATUS | RESPONSE
---------|---------
`200`| The blueprint that you’ve specified is deleted and an array with a confirmation is displayed. 
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.


#Applications
You can use the Calm public API using the methods described in the following sections to list or search for your applications, run flows on them, abort running flows and delete applications on Calm.

##Application List
Lists all of your applications on Calm.
###Request
METHOD | URI
------------ | -------------
`GET`| `http://CALM_URL/public/api/1/default/applications`

###Response
STATUS | RESPONSE
---------|---------
`200`| An array that lists your applications on Calm is displayed.   
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
`POST`| `http://CALM_URL/public/api/1/default/applications/search`

###Query Parameters
* `application_name`: Enter the full name of the application that you’re searching for. You can also enter a keyword to list all the applications that contain that keyword in their name.

###Response
STATUS | RESPONSE
---------|---------
`200`| An array containing the application that you searched for, or containing the keywords that you entered, on Calm is generated. 
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
`POST`| `http://CALM_URL/public/api/1/default/applications/flows/run`

###Query Parameters
* `application_name`: The name of the application you want to run a flow on. 
* `flow_name`: The name of the flow that you’d like to run on the specified application. 

###Response
STATUS | RESPONSE
---------|---------
`200`| The specified flow is run on the application and displays an array with the flow run UID. 
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
`POST`| `http://CALM_URL/public/api/1/default/applications/flows/abort`

###Query Parameters
* `application_name`: The name of the application you want to run a flow on. 
* `flow_name`: The name of the flow that you’d like to run on the specified application.

###Response
STATUS | RESPONSE
---------|---------
`200`| The specified flow being run is aborted from the specified application and displays an array with the flow run UID. 
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
`POST`| `http://CALM_URL/public/api/1/default/applications/delete`

###Query Parameters
* `application_name`: The name of the application you’d like to delete. 

###Response
STATUS | RESPONSE
---------|---------
`200`| The application that you've specified is deleted.  
`400` | Bad request
`401` | Unauthorised. Use valid credentials and try again. 
`403` | Forbidden.
`404` | Not found. 
`500` | Internal server error.
