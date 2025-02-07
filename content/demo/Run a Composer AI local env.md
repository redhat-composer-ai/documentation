**Clone the front and back end git repos:**

https://github.com/redhat-composer-ai/quarkus-llm-router

https://github.com/redhat-composer-ai/chatbot-ui

## Prerequisites for Mac users

**Install Podman**

Download and install from https://podman.io/

> [!NOTE]
> For Mac users:
> 
> Run `podman machine init`
> 
> Run `podman machine start`

**Install maven**

Mac:

`brew install maven`

Linux:

`dnf install maven`

**Install java version 21**

   https://www.oracle.com/java/technologies/downloads/#java21
      

> [!NOTE]
>   Mac Users:
>   
>   If you have updated the apple version of java, and it is at a version higher than java 21, you may need to set the JAVA_HOME environment variable to that maven picks up the correct version:
> 
>   edit .zshenv
> 
>   add this line to the file:
> 
>   `export JAVA_HOME=$(/usr/libexec/java_home)`
> 
>   source the new setting: 
>   
>   `source .zshenv`

  
  Check the versions of maven and java:

  `java --version`

  `mvn --version`

**Install npm**

Mac:

`brew install npm`

Linux:

`dnf install npm`
   
**Install sirv**

  `npm install --save sirv`

## Install LLM Router
Create *application-local.properties* file (example below) and copy into *src/main/resources* of the quarkus-llm-router directory. You will need to fill in the LLM information in the first three lines (https://github.com/redhat-composer-ai/quarkus-llm-router?tab=readme-ov-file#llm-connection)

```
openai.default.url=https://mistral-7b-instruct-v0-3-maas-apicast-production.apps.prod.rhoai.rh-aiservices-bu.com:443/v1
openai.default.apiKey=***********
openai.default.modelName=mistral-7b-instruct

elasticsearch.default.apiKey=nothing
elasticsearch.default.host=localhost
elasticsearch.default.index=test_index


disable.authorization=true

quarkus.http.cors=true
quarkus.http.cors.origins=*
quarkus.http.cors.origins=http://localhost:9000
quarkus.http.cors.methods=GET,PUT,POST,DELETE,PATCH,OPTIONS
quarkus.http.cors.headers=accept,authorization,content-type,x-requested-with
quarkus.http.cors.exposed-headers=location,info
quarkus.http.cors.access-control-max-age=24H
quarkus.http.cors.allow-credentials=true

# Set liquibase context (note if using multiple quarkus profiles last one takes precedence)
quarkus.liquibase-mongodb.contexts=local
```

Mac users: make sure your podman machine has started per the instructions above.

Run `mvn clean install` in the quarkus-llm-router directory.

Run `mvn quarkus:dev -Dquarkus.profile=local` in the quarkus-llm-router directory.

## Chatbot-UI Install
 In a new terminal, cd into the chatbot-ui directory (from https://github.com/redhat-composer-ai/chatbot-ui)

 run `npm install`
 
 run `npm run openapi`
 
 run `npm run start:dev`
 

 This should open a browser window with the Chatbot-UI:
 
![[Chatbot-UI.png]]

Make sure to choose an Assistant:

![[Assistant.png]]

Click on LLM Connections to make sure you have a default connection:

![[Default LLM.png]]




Ask your LLM a question:

![[LLM Question.png]]

