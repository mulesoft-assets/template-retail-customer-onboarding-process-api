# Template Customer Onboarding Process API

+ [License Agreement](#licenseagreement)
+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [APIs security considerations](#apissecurityconsiderations)
+ [Run it!](#runit)
	* [Running on premise](#runonopremise)
	* [Running on Studio](#runonstudio)
	* [Running on Mule ESB stand alone](#runonmuleesbstandalone)
	* [Running on CloudHub](#runoncloudhub)
	* [Deploying your Anypoint Template on CloudHub](#deployingyouranypointtemplateoncloudhub)
	* [Creating externally reachable proxy and applying policies](#proxy)
	* [Properties to be configured (With examples)](#propertiestobeconfigured)

# License Agreement <a name="licenseagreement"/>
Note that using this template is subject to the conditions of this [License Agreement](AnypointTemplateLicense.pdf).
Please review the terms of the license before downloading and using this template. In short, you are allowed to use the template for free with Mule ESB Enterprise Edition, CloudHub, or as a trial in Anypoint Studio.

# Use Case <a name="usecase"/>

As a new Retail API Led Connectivity Web Portal user I want a microservice to create new customer.

This template should serve as a foundation for implementing an API for creating new customer. API is defined using [RAML](https://docs.mulesoft.com/anypoint-platform-for-apis/walkthrough-design-existing#about-raml) and this implementation uses [APIkit](https://docs.mulesoft.com/anypoint-platform-for-apis/apikit-basic-anatomy#basic-anatomy).
The Onboarding Process API is part of the Retail Templates Solution.

# Considerations <a name="considerations"/>

To make this Anypoint Template run, there are certain preconditions that must be considered. **Failling to do so could lead to unexpected behavior of the template.**

## APIs security considerations <a name="apissecurityconsiderations"/>
This Process API is meant to be deployed within a CloudHub and managed using the API Platform Manager.

### Exposing external endpoints with HTTPS
+ It is triggered using HTTPS

### Exposing internal endpoints with RAML and HTTPS
+ It is interconnected internally with Customer System API using HTTP as well

### Exposing internal endpoints with RAML and HTTP
+ It is also interconnected with Notification System API using HTTP as well

# Run it! <a name="runit"/>
Simple steps to get Onboarding Process API running.
See below.

## Running on premise <a name="runonopremise"/>
In this section we detail the way you should run your Anypoint Template on your computer.


### Where to Download Mule Studio and Mule ESB
First thing to know if you are a newcomer to Mule is where to get the tools.

+ You can download Mule Studio from this [Location](http://www.mulesoft.com/platform/mule-studio)
+ You can download Mule ESB from this [Location](http://www.mulesoft.com/platform/soa/mule-esb-open-source-esb)

### Importing an Anypoint Template into Studio
Mule Studio offers several ways to import a project into the workspace, for instance: 

+ Anypoint Studio Project from File System
+ Packaged mule application (.jar)

You can find a detailed description on how to do so in this [Documentation Page](http://www.mulesoft.org/documentation/display/current/Importing+and+Exporting+in+Studio).

## Running on Studio <a name="runonstudio"/>
Once you have imported you Anypoint Template into Anypoint Studio you need to follow these steps to run it:

+ Generate keystore (You can find a detailed description on how to do so in this [Documentation Page](https://docs.mulesoft.com/mule-user-guide/v/3.7/tls-configuration#generating-keystores-and-truststores))
+ Locate the properties file `mule.dev.properties`, in src/main/resources
+ Complete all the properties required as per the examples in the section [Properties to be configured](#propertiestobeconfigured)
+ Once that is done, right click on you Anypoint Template project folder 
+ Hover you mouse over `"Run as"`
+ Click on  `"Mule Application"`

## Running on Mule ESB stand alone <a name="runonmuleesbstandalone"/>
Complete all properties in one of the property files, for example in [mule.prod.properties](../master/src/main/resources/mule.prod.properties) and run your app with the corresponding environment variable to use it. To follow the example, this will be `mule.env=prod`.

## Running on CloudHub <a name="runoncloudhub"/>
While [creating your application on CloudHub](http://www.mulesoft.org/documentation/display/current/Hello+World+on+CloudHub) (Or you can do it later as a next step), you need to go to `"Manage Application"` > `"Properties"` to set all environment variables detailed in **Properties to be configured**.
Follow other steps defined [here](#runonpremise) and once your app is all set and started, there is no need to do anything else.

## Deploying your Anypoint Template on CloudHub <a name="deployingyouranypointtemplateoncloudhub"/>
Mule Studio provides you with really easy way to deploy your Template directly to CloudHub, for the specific steps to do so please check this [link](http://www.mulesoft.org/documentation/display/current/Deploying+Mule+Applications#DeployingMuleApplications-DeploytoCloudHub)

## Properties to be configured (With examples) <a name="propertiestobeconfigured"/>
In order to use this Mule Anypoint Template you need to configure properties (APIs, configurations, etc.) either in properties file or in CloudHub as Environment Variables. The Onboarding Process API is using secured connection. Detail list with examples:
### Application properties
+ https.port `8082`
+ keystore.location `keystore.jks`
+ keystore.password `pass123!`
+ key.password `pass123!`
+ key.alias `1`

### API calls configuration
+ customers-system-api.host `customer-system-api.cloudhub.io`
+ customers-system-api.port `80`
+ customers-system-api.basePath `/api`
+ customers-system-api.protocol `HTTP`

+ notifications-system-api.host `=dev-retail-notifications-system-api.cloudhub.io`
+ notifications-system-api.port `80`
+ notifications-system-api.basePath `/api`
+ notifications-system-api.protocol `HTTP`

### Path to cretail portal shown in email sent to new customer
+ catalyst.url `http:\\path-to-retail-portal.com`
