#Introduction
The Calm REST API v1 lets you interact with your Calm installation and work with your blueprints and applications on Calm. Using the Calm API, you can search for your blueprints, run them and delete blueprints that you no longer require. You can also search for applications, run flows on them and delete applications whenever you’d like to retire them. The Calm API also lets you run a few administrator queries such as audits, viewing users and teams and viewing budgets that you've configured on Calm. 

##Interaction
You can interact with the Calm API using one of the following modes:

* Using the command line utility cURL. 
* Using a RESTful addon for your web browser.

!!! tip "Suggestions"
    * Google Chrome: Install the Postman RESTful Client as an addon for Chrome. 
    * Mozilla Firefox: Install the RESTClient as an addon for Firefox. 
    * Safari: Install the Paw REST client on your Mac. 

##Authentication
The Calm API uses Basic Authentication to check whether you’re authorized to use the Calm API. If using cURL, you can embed your Calm credentials in the header of the API request by using the `-u` flag. If you’re using your web browser with a RESTful client addon, you can specify your Calm credentials in the **Authorization** section on the client. 

##Parameters
Parameters may be submitted in the query string for `GET` requests. For `POST` requests, parameters must be submitted in the query string, but should be submitted in the `POST` body as a **JSON** array while setting `Content-Type: application/json`. For example, in order to search for a blueprint, the `POST` request should follow the format `POST http://calm_url/public/api/1/default/blueprints/search` with `{"blueprint_name":"mysearchkeyword"}` in the body formatted as JSON.

##Data Return
All API calls return data in JSON format by default. 

