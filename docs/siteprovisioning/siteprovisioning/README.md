# Installation

To install/configure the service as a service, use the following parameters for the *Epona.ProvisioningService.exe*

*help* or --help Displays help

*install* Installs the service

-username The username to run the service

-password The password for the specified username

-instance An instance name if registering the service multiple times

\--autostart The service should start automatically (default)

\--disabled The service should be set to disabled

\--manual The service should be started manually

\--delayed The service should start automatically (delayed)

\--localsystem Run the service with the local system account

\--localservice Run the service with the local service account

\--networkservice

Run the service with the network service permission

\--interactive The service will prompt the user at installation for the service credentials

\--sudo Prompts for UAC if running on Vista/W7/2008

-servicename The name that the service should use when installing

-description The service description the service should use when installing

-displayname The display name the the service should use when installing

*start* Starts the service if it is not already running

-instance The instance to start

*stop* Stops the service if it is running

-instance The instance to stop

*uninstall* Uninstalls the service

-instance An instance name if registering the service multiple times

\--sudo Prompts for UAC if running on Vista/W7/2008

The service can be run as a console application by starting the executable *Epona.ProvisioningService.exe* without any parameters.

After downloading check if the files are not blocked. Use this PowerShell script to unblock the dll/exe.

~~~powershell
Get-ChildItem \<path to your folder\> -recurse \| Unblock-File
~~~
