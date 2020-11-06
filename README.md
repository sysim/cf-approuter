
# cf-approuter-destination

A simple app router in Cloud Foundry to connect to ABAP System or any destination.

# Pre-requisites

Create the required service instances in Cloud Foundry.

 - SAP Cloud Platform with Cloud Foundry
 - Service Instances
	 - Connectivity (connectivity)
	 - Destination (destination)
	 - Authorization & Trust Management (xsuaa)
 - Cloud Foundry CLI

# Usage

1. In file *xs-app.json*, modify/add source, target & destination as required.

2. Replace *<unique_id>* of the *host* in file *manifest.yml* with something unique, for example the subaccount ID.

3. Make sure you have login to CF CLI with your CF credentials.

4. Execute `cf push`. This will build and push the approuter to your CF space.

5. SAP Cloud Platform with try to start the app router after deployment and you should see a green state *Started*.

![](./images/0.jpg)

6. By clicking the application name, you will get into the application details and the routes URL is provided.

![](./images/1.jpg)

# Reference
[Use the Application Router in Cloud Foundry to Connect to ABAP System](https://developers.sap.com/tutorials/cp-connectivity-consume-odata-service-approuter.html)