## Policies and Permissions

**Policies** in Calm are a set of rules and guidelines that you can impose upon your blueprints and deployments. They help you govern over who gets to do what action using Calm. Calm currently provides the following set of policies:

* **Expiry**, lets you set an expiry for your deployment. You can choose from either;

    * **No Expiry**, where your blueprint is set to never expire. 

    * **Date Field**, where your blueprint is set to expire on a particular date. 

    * **Time Delta**, where your blueprint is set to expire by the end of a particular time period. 

* **Approvals**, lets you initiate an approval request for a blueprint that you create or delete. You can choose to set an approval for whenever a blueprint is created or before it is deleted. When configured, this policy sends out an approval request, to create or delete a blueprint, to the teams and users that you’ve chosen to approve the blueprint. You can also specify email addresses to which the approval request is to be sent. 

* **Notifications**, lets you notify a particular team whenever a blueprint is created or deleted. You can choose to send out a notification for whenever a blueprint is created or deleted. You can also specify email addresses to which you would like to send out such notifications. 

You can access and configure policies while building your blueprint by clicking on the **Policies** tab.  

**Permissions**, on the other hand, lets you decide which teams and users have access to each individual blueprint and budgets that are created using Calm. If no permissions are assigned while creating a blueprint, every team has access to that particular blueprint. If permissions are assigned to a particular team, every user in that team will have access to the blueprint. 