# Blueprint

### Command

`calm blueprint`

The `blueprint` command is used to manage your Calm blueprints. This command has a set of subcommands that further extends its functionality:

* `list`

* `run`

* `delete`

* `download`

* `upload`

Optional Arguments

* `-h` or `--help` - outputs help for the command.

## Blueprint List

### Command

`calm blueprint list`

This command lists the blueprints that already exist on your Calm installation. 

### Optional Arguments

* `-h` or `--help` - outputs help for the command.

* `-q` or `--query` - lets you append a query in order to list a specific blueprint. The queries you can execute are the blueprint name and status. For example, 

    * `calm blueprint list -q name=ABC`

    * `calm blueprint list -q status=active/deactivated/draft`

## Blueprint Run

### Command

`calm blueprint run -b "Blueprint Name" -a “Application Name” -t “Team Name” --budget “Budget Name” --props “Blueprint Property Name=Value” “Resource Name:Resource Property Name=Value” --async`

This command runs the blueprint that you’ve chosen to run.

### Mandatory Arguments

* `-b` specifies the name of the blueprint you are running. 

* `-a`specifies the name that you’d like to give to the application that you spin up by running a blueprint. 

* `-t`specifies the name of the team on Calm that you belong to. 

### Optional Arguments

* `--budget` specifies the budget that has been assigned to your team. This should be used when the team that you’re a part of has a budget assigned to it. 

* `--props` is used to specify any runtime editable properties that you’ve configured in your blueprint. 

* `--async`

## Blueprint Delete

### Command

`calm blueprint delete -b "Blueprint Name"`

This command deletes the blueprint that you’ve specified. 

## Blueprint Download

### Command

`calm blueprint download -b "Blueprint Name"`

This command downloads the blueprint that you’ve specified.

## Blueprint Upload

### Command

`calm blueprint upload -b "Blueprint Name" -f “Blueprint File Name”`

This command uploads the blueprint that you’ve specified and saves it with the name that you’ve specified. 