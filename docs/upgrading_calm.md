#Upgrading Calm

Upgrading Calm to **v1.7.2** involves a few steps that require you to use a command line tool and to SSH into your Calm instance. 

!!! tip "Note"
    * Ensure that all Calm operations that have been initiated by your users such as flows, blueprint runs, etc., have finished running. 
    * Ask all Calm users to logout of Calm. 
    

!!! information "Optional Steps"
    You can take a MongoDB and PostgreSQL data dump by running the following commands:
	
````
sudo /usr/sbin/chroot /opt/calmio bash -l
supervisorctl stop all && echo && supervisorctl start db:*
mkdir -p dbdumpdata/cal
pg_dump -cd epsilon > dbdumpdata/epsilon.sql
mongodump --out dbdumpdata/cal 
````   
## Upgrade Instructions

To upgrade to the latest version of Calm, do the following:

* SSH into your Calm instance using a command line tool.

!!! tip "Note"
	Some users of Calm v1.7.1 AMIs may not be able to SSH into their Calm instance. This is a known issue. In case you come across this issue, please get in touch with us at [support@calm.io](mailto:support@calm.io) for a patch. 

* Enter the command: `epr`

!!! tip "Note"
	`epr` is a command alias used to login to the `chroot`of your Calm instance as a `root` user. This alias is added during the installation of Calm. In case you do not wish to add this alias to your `bashrc`, please use the command: `sudo /usr/sbin/chroot /opt/calmio bash -l`. To know how to add this command alias to your `~/.bashrc` read the [Post-install Steps](http://docs.calm.io/installing_calm/#post-install-steps) topic on the [Calm Installation Guide](http://docs.calm.io/installing_calm/).

* Check if `deb https://deb.calm.io/debs/ calmio main` is present in `/etc/apt/sources.list` using the command: `cat /etc/apt/sources.list`. If not present, add it to `/etc/apt/sources.list` using a terminal text editor of your choice. 

* Stop and restart Calm services by running the command: `service python-calm stop && service python-calm start`
* Upgrade Calm using the commands:
````
apt-get update && apt-get upgrade python-calm
````
* Exit `chroot` using the command `exit`.
* Stop and restart Calm services by running the command: `service python-calm stop && service python-calm start`

This completes the upgrade of Calm to **v1.7.2**. 

## Upgrading from Calm v1.7.0 to v1.7.2


In case you are upgrading from Calm **v1.7.0** to **v1.7.2**, follow the steps listed above and then proceed with the steps mentioned below:

* Login to `chroot` again using the command `epr`.
* Run the following migration script: `calmdb.py migrate --from=1.7.0 --to=1.7.1`

Once the upgrade is complete, you should receive an output that looks like this:
````
using config files ['/calm/conf/calm.ini', '/calm/conf/conf.d/agreement', '/calm/conf/conf.d/license']
2016-05-03 18:20:56,449 [DEBUG] retry:155: Converted retries value: 3 -> Retry(total=3, connect=None, read=None, redirect=None)
Doing Bulk delete on Consumption table with cost=0
Setting budget id on Consumption table
Deleting consumption rows which have empty budget_id
populating app-wise budget cost after cleanup
2016-05-03 18:20:57,263 [DEBUG] document:422: Setting Creation time now
[18:20:57] (python-calm) [/opt/calmio]
````
!!! tip "Note"
	Your output may differ depending on your configuration of Calm. In case you come across errors during migration, please get in touch with us at <mailto:support@calm.io>.
