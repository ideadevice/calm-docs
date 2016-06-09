# Prerequisites for Installing Calm

In order to seamlessly install and use Calm, you need to ensure that the requirements outlined in the following subsections are fulfilled.

## System Requirements

### Processor

64-bit, 2-core processor

### Memory

A minimum of 8 GB RAM. 

### Disk Space

A minimum of 20 GB of available disk space. More disk space may be needed for extended log archiving over time. 

### Operating Systems

* RHEL 6.x or later

* CentOS 6.x or later

* Debian 7.x or later

* Ubuntu 14.04 LTS 

## Port Requirements

* Port 22 for Linux systems.

* Ports 80 and 443. 

* Ports 4241, 4243 and 2812 for Calm internal service communications. 

Since Calm makes use of a lot of ports to communicate with our backend servers, it is advisable to not run anything else on the machine on which you install Calm.

## Credentials

You should have access to valid credentials for valid users on all managed nodes. 

## Email Integration

It is desirable for your Calm server to have the ability to send and receive emails in order to make the most of Calm’s Notification feature. You can integrate your existing email server with your Calm server and have it serve the emails being sent from Calm. To know more about email integration view Integrating Your Email Server. 

# Before We Begin

Before you begin installing Calm, you must complete the following checks. These checks pertain to RHEL 6.x; you might have to run similar checks for other distributions.

* Disable `selinux`. Use `gentenforce` to check the current level. Edit the following path: `/etc/sysconﬁg/selinux` (or this path: `/etc/selinux/conﬁg` ) and set `SELINUX` to **disabled**. Reboot your system to make this change effective.

* Disable `iptables` using the following command: `/sbin/chkconﬁg iptables --level 2345 off`

* Disable `postﬁx` using the following command: `/sbin/chkconﬁg postﬁx –level 2345 off`

* Ensure that the ports that Calm will require are free. Run `netstat -tnpl` to view all TCP ports. The following ports should be free: **80**, **443**, **2812**, **4949**, **5000**, **5432**, **6379**, **6543**, **7777**, **7778**, **8005**, **8080**, **8888**, **9000**.

* Set run level as **3**. Edit `/etc/inittab` and change the run level from **5** to **3** (if it is not **3** already). The `inittab` entry should read: `id:3:initdefault`. 

* Ensure that the `redhat-lsb` package is installed. Use the following command to check whether the package is installed: `yum install redhat-lsb`. This command supplies the start daemon command in `/etc/init.d/python-calm`.

* Reboot the system. Ensure that all the changes are effected in the server.

# Installing Calm

Once you’ve completed the checks and have met all the requirements for installing Calm, transfer the Calm installer onto the machine where you’re installing Calm and then follow these instructions:

* Provide execute permissions to the installer by running the command: `chmod +x <installer.run>`

* Start the installation by running the command: `./<installer.run>`. Note: The extraction of the installer requires `bzip2` to be installed on your system. In case `bzip2` isn’t installed, install `bzip2` and then proceed with the installation. 

* Once the extraction is complete, run the following command to continue with the installation: 
    `/opt/calmio/installer_scripts/setup.sh`

!!! tip "Note"
    If you haven’t logged in as a `root` user on your machine, try running the command by appending `sudo` at the beginning of the command.

* Provide the following information during the configuration stage:
	* **Which run level should python-calm automatically start up on? [default:5]**: Use default.
	* **Geographic area**: Enter the number that corresponds to your geographic area.
	* **Time zone**: Enter the number that corresponds to your city or region. 

This completes the installation of Calm on your machine. Before you login to Calm for the first time, you should start Calm services by running the command:

`sudo service python-calm start`

# Post-install Steps

Before you start using Calm, here are the few things that you should do, in order to make any instances of debugging or further configuration easier:

!!! tip "Note"
    The post-install steps mentioned below are **optional** for Calm Standard customers and **mandatory** for Calm Enterprise customers. 

* Consider adding the following aliases to your `~/.bashrc` in order to get into the Calm `chroot`:
	* To get into Calm `chroot` as a `root` user: `epr='/usr/sbin/chroot /opt/calmio bash -l'`
	* To get into Calm `chroot` as an `epsilon` user: `epc='/usr/sbin/chroot /opt/calmio su - epsilon'`
* Run the command `epr`, create a file named `calm.ini` in `/opt/calmio/etc/python-calm/conf/conf.d` and setup your name in the sections `[common]` and `[customer]`. For example, if you'd like Calm to be registered under your company's name, the sections should look like this:

````
[common]
customer_name = Company Name
[customer]
name = Company Name
````
* Login to your Calm installation by using the domain name of your machine in your favorite web browser. 

You will now be able to view the Welcome Screen of your Calm installation. Your Calm installation is now complete. 

# Integrating Your Email Server

Once your Calm installation is complete, you can configure your email server with your Calm server to serve the emails being sent by Calm. Calm can send email directly to a relay host. However, if SSMTP, SMTPS, or authentication is involved in the relay, you will require an intermediate Mail Transfer Agent (MTA), the one that is installed on the machine by default.

!!! tip "Note"
    Existing systems may depend on local mail; it is recommended that you use the MTA that is installed outside the Calm chroot. The postfix that is shipped inside the chroot should be used as a last resort.

The following set of commands shows you how to configure a popular MTA called postfix. Use the following commands to configure postfix, which is also the default MTA on RHEL:

* To set the relayhost:
    
    `postconf -e ’relayhost = [smtp.gmail.com]:587’`

2. To enable TLS over SMTP:	`postconf -e ’smtp_use_tls = yes’`

3. To enable SMTP-Auth:    `postconf -e ’smtp_sasl_auth_enable = yes’`
    `postconf -e ’smtp_sasl_password_maps = hash:/etc/postfix/sasl/passwd’`
    `postconf -e ’smtp_sasl_security_options = noanonymous’`

4. To set password in `/etc/postfix/sasl/passwd`:`[smtp.gmail.com]:587 username@gmail.com:password`

5. Permissions on the file should be set to `600`.
6. Run `postmap /etc/postfix/sasl/passwd`.
6. Restart postfix. The log file for postfix is located at the following directory: `/var/log/maillog`

This completes the integration of your email server with your Calm machine. You will now be able to route all the emails that are sent by Calm through this server. 


# Configuring Calm for Windows Automation

Calm uses Windows PowerShell remoting to run commands on Windows machines. The Calm component called **Karan** is used to manage Windows machines or the applications installed on Windows. **Karan** is installed as a service on the Windows slave machine, which has access to other Windows machines.

## Requirements for Windows

### Server Requirements

* **Windows Slave**: A VM to host the Windows automation component

* **OS**: 64bit Windows Server 2008 R2

* **RAM**: 8GB

* **Disk space**: 40 GB free

* **Software**: PowerShell 2.0 and .Net 4.5

### Port Requirements

* Access from the Calm server to the Windows slave port **8090**

* Access from the Windows slave to the Calm server ports **80** and **443**

* Access from the Windows slave to all managed Windows machines on ports **5985** and **5986**.

!!! tip "Note"
    The Windows VMs that are targets for automation must have PowerShell 2.0 running on them.

## Before Installing Karan

Ensure that PowerShell 2.0 is installed using the following command:
`PowerShell Get-Host`

If PowerShell is installed, this command will return the PowerShell version. If it is not installed, go to the[ Microsoft Support Center](http://support.microsoft.com/kb/968929) to download and install PowerShell.

## Installing Karan

To install **Karan**, do the following:

* Download or copy the latest version of the Karan installer. If you don’t have the installer yet, get in touch with us at [support@calm.io](mailto:support@calm.io) and we will get you the latest version of it right away. 

* Double-click the installer ﬁle. The **Welcome** screen opens. The installer ﬁle determines whether .NET 4.5 is installed on the system. If it is not installed, click Install to install .NET 4.5. After it is installed, the regular **Karan Setup Wizard** screen opens.

!!! tip "Note"
    If CLR 4.0 is already installed and is in use by a program, you will have to restart the system. After restarting, Karan installation will automatically resume.

* Click **Next**. This opens the **Karan Information** screen. 

* Complete the following checks:

    * Under **Enter conﬁg details for the Karan service**, verify that the default selection is **https**.

    * Ensure that the default value **8090** displays in the **Port for Karan Service** ﬁeld.
   
    * Provide the `gateway_uuid` available from `calm.ini` on the Calm server by running the command:
    `grep gateway_uuid /etc/python-calm/conf/calm.ini`.
    * Provide the Karan IP address in the **Karan Host** field and the Epsilon IP address in the **Epsilon Address** field.

    * Click **Check Epsilon IP** to check whether Epsilon is available at the given URL. The installation can continue even if Epsilon is not available at the time of installation. This can be changed later while configuring Karan (see [Post-install Steps](#post-install-steps_1])).

* Click **Next**. The **Service Account Information**screen opens. 

* Enter the following information:

    * In the **Specify the logon account for the Karan service** ﬁelds, enter the Administrator login credentials.

    * In the **Install Karan to** ﬁeld, enter the path of the directory in which you want Karan to be installed.

* Click **Next** to complete the installation. Karan is now installed in the speciﬁed directory. Certiﬁcates are bound to the port speciﬁed during installation. You must manually start Karan in **services.msc**.

After installation, you can conﬁgure changes to the **karan.exe.config** ﬁle in the install directory. Restart Karan after you finish updating the conﬁguration ﬁle.

## Post-install Steps

After the installation is complete, complete the following steps to conﬁgure the environment for Windows automation:

* Point Epsilon at the Karan host:

	* In the Calm environment on the Calm host, open `/etc/python-calm/conf/calm.ini`.

	* Enable Karan by setting the following line to True: `karan_enabled = True`

	* Run the command: `service python-calm restart`. 

* Update firewall settings:

	* Make the Karan ports accessible from the Epsilon server. To do this, go to **Control Panel** > **Check Firewall Status** > **Advanced Settings** > **Inbound Rules** > **New Rules**.

* Select Rule Type as "Port" and click **Next**.

	* Select **TCP** and specify the port as "8090" or the Karan port that is mentioned in karan.exe.config/epsilon.ini.

	* Accept the rest of the default values.

	* Enter a name for the rule and click **Finish**.

	* Use the following command on Epsilon server to check if Karan port is accessible:`telnet "karan server" "port number"`

Add the target windows machines to the Karan host. Add all the machines on which remote commands have to be run to the trusted hosts list. Use the following command at the PowerShell prompt:

`Set-Item wsman:\localhost\Client\TrustedHosts -Value *`

Use the following command to add individual hosts:

`Set-Item wsman:\localhost\Client\TrustedHosts <machine_name> -Concatenate -Force`

## Managed Node Requirements

To enable Karan to run commands on a Windows node, the Windows node must meet the following requirements:

* PowerShell 2.0 must be installed. Run the following command to verify the version: `PowerShell Get-Host`

* The WinRM service must be running. Check the status of WinRM and, if necessary, start the service using the following command: `PowerShell Get-Service WinRM` 
* And then run: `PowerShell Start-Service WinRM`

* PowerShell remoting must be enabled. From PowerShell, run the following command: `Enable-PSRemoting`

For Windows XP, this is done from gpedit.msc. Set the value of **Computer Conﬁguration > Windows Settings > Security Settings > Local Policies > Security Options > Network access:Sharing and Security model for local accounts to local users authenticate as themselves**.

* The execution policy must be enabled to run scripts. Use the following command:Set-ExecutionPolicy RemoteSigned

By default, only Administrators can talk remotely using PowerShell. If other users are to be conﬁgured to use PowerShell remoting, they must be added in the following UI:

`Set-PSSessionConfiguration -Name Microsoft.PowerShell –showSecurityDescriptorUI`

!!! tip "Note"
    To check whether the above setups were successful, log in to Karan host and test the remote command execution from the command line:
	`$cred=get-credential`
	`invoke-command -computername <ip> -credential $cred -scriptblock{get-process}`

## Local Windows Scripts

It is sometimes necessary to run PowerShell scripts locally on the Karan server rather than on the remotely managed machines. To enable this, some registry settings have to be changed. The account under which Karan runs must be given rights to create processes. To do this, complete the following steps:

* Run `secpol.msc`.

* Under **Security Settings** > **Local Policies** > **User Rights Management**:

    * Add the user or group to **Adjust memory quotas for a process**.

    * Add the user or group to **Replace a process level token**.

## Other Administrative Tasks and Configurations

### Sentry Configuration (For Calm Enterprise Users)
In order to configure Sentry, do the following:

* Login to `python-calm` `chroot` as a `root` user by using the command: `sudo chroot /opt/calmio bash -l` or by using the alias: `epr`, in case you've added it to your `.bashrc`.
* Run the command: `cd /etc/python-calm/conf/conf.d`
* Open the `calm.ini` file in an editor. 
* Add your Sentry configuration to the file in the following format:

````
[DEFAULT]
sentry_dsn = http://<sentry_dsn>
[sentry]
sentry_dsn = http://<sentry_dsn>
raven_js_dsn = http://<raven_js_dsn>
````

### Setting up a Tomcat Server for vCenter Configuration

Using Calm with vCenter requires the support ofa Tomcat server. To start a Tomcat server, do the following:

* Run: `sudo service python-calm stop`

* Run: `cp /opt/calmio/opt/python-calm/fullscale/supervisor/tomcat.conf /opt/calmio/etc/supervisor/conf.d/`

* Start Calm services by running: `sudo service python-calm start`

### Upgrading Calm Configurations

In order to upgrade Calm configurations, do the following:

* Stop Calm services by running: `sudo service python-calm stop`

* Run the commands:

```` 
cp /opt/calmio/opt/python-calm/fullscale/supervisor/* /opt/calmio/etc/supervisor/conf.d/
cp /opt/calmio//opt/python-calm/fullscale/bin/* /opt/calmio/usr/bin/python-calm
````

* Start Calm services by running: `sudo service python-calm start`

###Troubleshooting Installation Errors on Ubuntu 14.05
You might encounter a few errors while installing Calm on instances running Ubuntu 14.05. These errors can be resolved by doing the following:

* Once your Calm installation is complete, login to the `chroot` of your Calm instance using the command: `epr` or `/usr/sbin/chroot /opt/calmio bash -l`.
* Run the following commands in succession:
````
rm /dev/shm
mkdir /dev/shm
chmod 777 /dev/shm
vi /etc/fstab
````
* Add or modify the `shm` line as shown below: 
````
From:
none /dev/shm tmpfs rw 0 0
To:
none /dev/shm tmpfs rw,nosuid,nodev,noexec 0 0
````
* Exit `chroot` using the command `exit`
* Run the command `service python-calm stop && service python-calm start` to restart the Calm service. 






