Plugin for monitoring responses and log events of DropWizard
============================================================

Dropwizard is a Java framework for developing ops-friendly, high-performance, RESTful web services.

For monitoring the responses and log events count metrics of DropWizard servers using Site24x7 Server Monitoring Plugins. 
  
### Author: Vinoth Manoharan, Zoho Corp
### Language : Python
### Tested in Ubuntu

Dropwizard Event metrics plugin installation
================

1. Have the site24x7 server monitoring agent up and running.
2. Download the plugin from github https://raw.githubusercontent.com/site24x7/plugins/master/dropwizard\_event\_metrics/dropwizard\_event\_metrics.py
3. Create a folder in name of the plugin under agent plugins directory (/opt/site24x7/monagent/plugins/)
4. Place the plugin inside the folder 

Commands to perform the above streps:

	cd /opt/site24x7/monagent/plugins/
	mkdir dropwizard_event_metrics
	cd dropwizard_event_metrics
	wget https://raw.githubusercontent.com/site24x7/plugins/master/dropwizard_event_metrics/dropwizard_event_metrics.py


Configure the agent plugin
==========================
 
Make the following changes in the dropwizard_connection_metrics plugin file ( copied to agent's plugin directory earlier ).

- Replace the shebang character "#!" in line1 to the appropriate path for python in your system.
		#!/usr/bin/python3
- Change the values of hostname and port according to your Dropwizard's hostname and port.

- Save the changes and restart the agent.
		/etc/init.d/site24x7monagent restart

	PROTOCOL = 'http'
	HOSTNAME = 'localhost'
	PORT = '8081'
change the above values according to your requirements

Site24x7 agent will now report dropwizard's request statistics in the plugins tab under the site24x7.com portal.


Dropwizard Attributes:
======================
	log_count		- represents the total number of logged events
	log_*_count	- represents the total number of logged events based on severity (debug, error, info, trace, warn)
	xxx-responses 	- count of aggregation of responses based on their response codes (1xx, 2xx, 3xx, 4xx, 5xx)

Monitoring additional metrics:
==============================
To monitor additional metrics, edit the "dropwizard\_event\_metrics.py" file and add the new metrics that need monitoring
 
Increment the plugin version value in the file "dropwizard\_event\_metrics.py" to view the newly added metrics ( For e.g. Change the default plugin version from PLUGIN_VERSION = "1" to "PLUGIN_VERSION = "2") 


Learn more about the plugin installation steps and the various performance metrics that you can monitor in https://www.site24x7.com/plugins.html        