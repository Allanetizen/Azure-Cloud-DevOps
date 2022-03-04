# Azure-Cloud-DevOps
Deploying a MERN Stack application to Azure Cloud

## On Premise Data Center
**High Responsibility** - employee / maintenance-cooling,electric, hardware
Data replication for backup

## Cloud Computing

- Availability of comp resources when you need it- computing and storage
- No active involvement i.e no employee
- Different Locations for data centers i.e no effect after calamities
- Shared resources - achieve coherence and economy of scale - **pay for duration** => storage and processor 
- Pay as you go -> Reduces capital expenses(capex) no employee , no hardware though unexpected operating expenses(opex) may  arise is misused i.e forgetting to turn off system after use as it is pay per duration usage
- Providers: aws, Azure , Google Cloud, Alibaba Cloud , Digital Ocean , Salesforce etc.

## Types of Cloud Computing Services
All cover different degrees of management by you(cloud computing as-a-service)
- Infrastructure-as-a-service(IaaS)
- Platform-as-a-service(PaaS)
- Software-as-a-service(SaaS)

![image](https://user-images.githubusercontent.com/39994438/156827974-408f662b-3b3f-481b-87c0-d6a7ed2772f5.png)

## Summary of the differences Chart

![image](https://user-images.githubusercontent.com/39994438/156828316-681a3250-e392-4716-869a-5b233fa68b77.png)

**Key**

![image](https://user-images.githubusercontent.com/39994438/156828760-c6317d0a-1341-4ac6-a9c4-ab00d349ef40.png)
### Azure Cloud
- services:

![image](https://user-images.githubusercontent.com/39994438/156829270-44956b92-2431-4155-811f-8e69193cdaf4.png)

### Azure DevOps


**Intro**

![image](https://user-images.githubusercontent.com/39994438/156850800-ba706edc-19ab-4240-88c8-3f7ffac6e5c0.png)

### Steps in deploying a MERN App

- **creating a cosmos** -> DB- NoSQL API

Fill the details below and click create/review the create :

#### Node Express API

![image](https://user-images.githubusercontent.com/39994438/156851411-9873414f-4f41-4f1f-b897-135179786f2a.png)

- After DB is created succesfully, 
- go to resource,
- Connection string for connection
- Copy primary connection string
-	Go to source code
-	paste string in db.js --> has connection string
-	run app, upload some data
-	go to data explorer to check the data

## Push front/backend code to Azure repos
-	Go to repos
-	Create 2 New repos and name them fe & be

## Integrate Backend( CI Pipeline)
-	Click on the repo
-	clone repo
-	copy the URL
-	git clone link pasted
-	go to the cloned backend folder
-	copy all files, can ignore node_modules
-	paste to your application folder, BE part
-	git commit and push

## Create CI pipeline
-	Go to pipeline
-	create pipeline
-	chose editoer/classic
-	choose project repo
- continue to empty job, name --> project name CI e.g myapp-be-CI pipeline
-	click on agent job
-	add task **--npm --npm install at root level**
-	add task npm test for test, not compulsary, control option continue on error, so no fail
-	add task Publish Artifact: drop, pasth to publish :Build.SourcesDirectory, choose drop
-	Save and run
-	**NB: if error check to ensure pipelines allowed**
-	search app service, create app service , choose mern 
-	stack from resource group, node , windows, region .. then create, deployment suceeded
-	Go to resource, check url for appservice
-	go to pipelines, CI , triggers, enable Continous Integration, branch

## Deploy Backend( CD Pipeline)
-	Go to pipelines, releases, new pipeline
-	choose an empty one , name it next , change name of pipeline
-	add artifact
-	choose build pipeline
-	click on the creates pipeline thunder icon, choose branch then save
-	click on one job
-	search app service deploy, name it, 
-	enter credentials to authorize, choose subscription, 
-	choose platform windows/linux
-	enter folder /directory
-	generate web.config parameters, click on the 3 dots
-	choose node and save, then save
-	every commit triggers a new pipeline, creates a release job for CD {new release}

## Connect-Local-React-code-to-Azure-Backend-CosmosDB
Edit out all base URLs using the generated azure URL
## Push-React-code-to-Azure-Repos
- go to repos ,files , front end file
-	copy the url
-	go to computer and clone the url
-	copy the files except node modules to the cloned folders
-	commit code & push

## CI Pipeline for React front-end
-	go to pipelines, new , use classic editor
-	choose , project , repo , branch
-	choose empty job and name
-	add tasks: npm install , npm run build in command and arguments
-	add task: publish artifact: drop drop is artifact name and run

**can add npm run tests**

## Create Storage Account container(file storage)
-	search storage accounts
-	create storage accounts
-	choose mern stack resource group
-	add name, region & review create and create again
-	Go to resource, containers click + container , add anonymous access



















