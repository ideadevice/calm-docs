# Introduction

The Calm Command Line Interface (CLI) is an alternative way of using the Calm DevOps Platform. Although the CLI does not provide you all the features and functionality that its GUI does, you can use it to perform a certain set of basic tasks with your blueprints and applications. 

The Calm CLI needs to be installed separately. Once installed, the Calm CLI can be accessed by using the `calm` command. For more about installing the Calm CLI, read [Installing the Calm CLI](#installing-calm-cli). 

Running the `calm` command alone will give you a single-sentence synopsis of the usage of the command along with all the available subcommands. Running `calm -h` or `calm --help` outputs detailed help for the `calm` command including a list of subcommands and their usage. Appending `-h` or `--help` at the end of any Calm command will output help for that particular command. 

# Installing the Calm CLI
The installer for the Calm CLI is hosted in our public GitHub repository. You can clone this repository to the machine on which you'd like the CLI to be installed and run the installer. 

To install the CLI, do the following:

* Clone the repository `https://github.com/ideadevice/calm-public-lib.git` to the machine you'd like to install the CLI on. 
* Navigate to the directory where you've cloned the repository. 
* Open the directory named `Calm-CLI`.
* Run the command `pip install calmio*`

This installs the Calm CLI on your machine. The Calm CLI will now be accessible using the `calm` command. 

# Subcommands

The `calm` command has the following three subcommands:

* `test-login` does a test login to your Calm installation. 

* `blueprint` lets you work with your blueprints.

* `application` lets you work with the applications that you’ve spun up using Calm. 

To view in depth information about Calm's subcommands and their usage, view the appropriate subsection in the document navigation menu.  

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

