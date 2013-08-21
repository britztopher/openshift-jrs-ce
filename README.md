# OpenShift JasperReports Server CE Cartridge

This cartridge is targetted for developers that want to leverage the [JasperReports Server CE](http://www.jaspersoft.com) as the embed BI engine for their own application on  [OpenShift](https://openshift.redhat.com/app/login).

## Setup

### Requirements

  * Openshift account. 
  * rhc tools, version 1.9 or later
  
#### Application requirements

  * Gear size should be medium. You'll need to manually add additional storage (min. 2GB) to the default storage for your cartridge.
  * JBoss EAP6 cartridge
  * PostgreSQL 9.2 cartridge

### Installation

If you have already a JBoss EAP 6 application created run:

    rhc cartridge add http://cartreflect-claytondev.rhcloud.com/reflect?github=rudygodoy/openshift-jrs-ce --app <you_app_name>

If you don't have a JBoss EAP 6 Openshift application created, run:

    rhc app create -a <my_app_name> jbosseap-6.0 postgresql-9.2 -g medium http://cartreflect-claytondev.rhcloud.com/reflect?github=rudygodoy/openshift-jrs-ce


## Application integration

If you are developing a product or managing an environment in which you want to integrate or embed BI, JasperReports Server provides several interfaces to allow you to do so quickly and easily. When integrating JasperReports Server into your environment or application, you will want to integrate two key areas: authentication and user interface.


### Capabilities

   * Single Sign On
   * HTTP APIs
   * User Interface Themes/skin
   * Web Services APIs

For more details, please visit: http://www.jaspersoft.com/getting-started


### Default credentials

**Default username:** jasperadmin

**Default password:** jasperadmin

