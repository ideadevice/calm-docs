# Application

### Command

`calm blueprint application`

The application command is used to manage your applications on Calm. This command has a set of subcommands that further extends its functionality:

* `list`

* `delete`

## Application List

### Command 

`calm application list`

This command lists the applications on Calm. 

### Optional Arguments

* `-h` or `--help` - outputs help for the command.

* `-q` or `--query` - lets you append a query in order to list a specific blueprint. The queries you can execute are the blueprint name and status. For example, 

    * `calm application list -q name=ABC`

    * `calm application list -q status=queued/in%20progress/failure/running/deleted`

## Application Delete

### Command

`calm application delete -a "Application Name"`

This command deletes the application that you’ve specified. 

