
# cf-approuter-destination

A simple app router in Cloud Foundry to connect to ABAP System or any destination.

# Pre-requisites

- SAP Cloud Platform with Cloud Foundry
- Create the required service instances in Cloud Foundry
    - Connectivity (connectivity)
	- Destination (destination)
	- Authorization & Trust Management (xsuaa)
- Cloud Foundry CLI

# Usage

1. In file *xs-app.json*, modify/add source, target & destination as required.

2. Replace *<unique_id>* of the *host* in file *manifest.yml* with something unique, for example the subaccount ID.

3. Create a zip archive called *approuter.zip* containing files *xs-app.json*, *.npmrc* & *package.json*.

    - For Linux or macOS, run the below code in bash.

    ```bash
    {
        for file in xs-app.json .npmrc package.json; do
            if [[ ! -e $file ]]; then
                echo -e "\e[33m[WARNING] $file does not exist\e[0m"
            fi
        done

        zip -r approuter.zip xs-app.json .npmrc package.json
    }
    ```

    - For Windows, run the below code in Powershell

    ```powershell
    foreach ($file in @("xs-app.json",".npmrc", "package.json")){
        if (-not (Test-Path $file)) { Write-Warning "$file does not exist" }
    }

    Get-ChildItem -Path xs-app.json, .npmrc, package.json | Compress-Archive -DestinationPath approuter.zip
    ```

4. Make sure you have logged into CF CLI and push the approuter to your CF space.

```
> cf push
```

5. SAP Cloud Platform with try to start the app router after deployment and you should see a green state *Started*.

![](/images/01.png)

6. By clicking the application name, you will get into the application details and the routes URL is provided.

![](/images/02.png)

# Reference
[Use the Application Router in Cloud Foundry to Connect to ABAP System](https://developers.sap.com/tutorials/cp-connectivity-consume-odata-service-approuter.html)