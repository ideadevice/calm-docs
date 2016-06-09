# Macro Reference
A Macro is a special token that is expanded at run time by Calm. Macros can occur in scripts, templates, command line arguments, in email addresses, subject & body and usually any place that text can be entered. An example of a macro usage in a Run Shell task is:

`echo @@{vm_machine_ip}@@`
              
`@@{vm_machine_ip}@@` is a macro. All macros are of the format `@@{<name>}@@`. When Calm encounters a macro, it will replace the macro with the appropriate expansion. Macros are used to make scripts generic and are the basis of creating reusable workflows.

## Built-in Macros in Calm

Macro | Expands to 
------------ | ------------- 
`@@{calm_array_index}@@` | Calm array index |
`@@{calm_blueprint_name}@@` | The blueprint name
`@@{calm_deployment_name}@@` | The deployment name
`@@{calm_service_name}@@` | The service name
`@@{calm_team_name}@@` | The team name
`@@{calm_username}@@` | The username
`@@{calm_uuid}@@` | The UUID within a deployment
`@@{calm_array_vm_machine_ip}@@` | The list of IP addresses of all services in an array
`@@{calm_array_vm_machine_ip[index]}@@` | The individual IP of a service in an array
`@@{target_version}@@` | The target version in an upgrade policy
`@@{previous_version}@@` | The previous version to perform rollbacks
`@@{calm_RANDOM}@@`| A random number
`@@{calm_UNIQUE}@@` | Same as @@{calm_RANDOM}@@
`@@{calm_TODAY}@@` | The current timestamp
`@@{calm_NOW}@@` | The current timestamp
`@@{calm_TIME("<format>")}@@` | Current time in user specified format
`@@{calm_YEAR("yyyy")}@@` | Current year in YYYY format
`@@{calm_YEAR("yy")}@@` | Current year in YY format
`@@{calm_MONTH("mm")}@@` | Current month in MM format
`@@{calm_MONTH("short")}@@` | Current month short name
`@@{calm_MONTH("long")}@@` | Current month long name
`@@{calm_DAY("month")}@@` | Numeric day of the month
`@@{calm_DAY("year")}@@` | Numeric day of the year
`@@{calm_WEEKNUMBER}@@` | Numeric week of the year
`@@{calm_WEEKNUMBER("iso")}@@` | ISO Numeric week of the year
`@@{calm_WEEKDAY("number")}@@` | Numeric day of the week
`@@{calm_WEEKDAY("name_short")}@@` | Day of the week in short form
`@@{calm_WEEKDAY("name_long")}@@` | Day of the week in long form
`@@{calm_HOUR("am_pm")}@@` | AM or PM
`@@{calm_HOUR("12")}@@` | Numeric day in 12hr format
`@@{calm_HOUR("24")}@@` | Numeric day in 24hr format
`@@{calm_MINUTE}@@` | Numeric Minute
`@@{calm_SECOND}@@` | Numeric Second
`@@{calm_IS_WEEKDAY}@@` | Return '1' if the current day is a weekday (mon-fri)
`@@{calm_IS_LONG_WEEKDAY}@@` | Return '1' if the current day is a long weekday (mon-sat)
`@@{calm_IS_WITHIN("time1", "time2")}@@` | Return '1' if the current time is within the supplied time1 & time2 range

## Provider-specific Macros

### Amazon Web Services

Macro | Expands to 
-------- | ---------- 
`@@{public_ip_address}@@` | The public IP address of the service
`@@{private_ip_address}@@` | The private IP address of the service
`@@{reservation_id}@@` | The reservation ID
`@@{aws_instance_id}@@` | The AWS instance ID
`@@{private_dns_name}@@` | The private DNS name
`@@{public_dns_name}@@` | The public DNS name
`@@{vm_machine_ip}@@` | The VM machine IP
`@@{vm_zone}@@` | The VM zone

###	XenServer

Macro | Expands to 
-------- | ---------- 
`@@{vm_machine_ip}@@` | The VM machine IP

### Nutanix

Macro | Expands to 
-------- | ---------- 
`@@{vm_ip}@@` | The VM IP
`@@{vm_id}@@` | The VM ID

### Docker

Macro | Expands to 
-------- | ---------- 
`@@{docker_host}@@` | The Docker Host
`@@{docker_container_name}@@` | The Docker container name
`@@{docker_container_id}@@`| The container ID
`@@{docker_container_ip}@@` | The container IP

###vCenter

Macro | Expands to 
-------- | ---------- 
`@@{vm_machine_ip}@@` | The VM machine IP
`@@{datacenter}@@` | The datacenter
`@@{esxi_host}@@` | The ESXI host
`@@{vm_name}@@` | The VM Name
`@@{datastore}@@` | The datastore

### Openstack

Macro | Expands to 
-------- | ---------- 
`@@{instance_id}@@` | The instance ID
`@@{instance_name}@@` | The instance name
`@@{instance_fixed_ip}@@` | The instance fixed IP
`@@{instance_floating_ip}@@` | The instance floating IP
`@@{instance_zone}@@` | The instance zone