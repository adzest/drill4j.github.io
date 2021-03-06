---
layout: page
title: How to start
permalink: /how-to-start/
---

![image](/assets/img/d4j_img_install_steps.png)


## 1. Install docker 
> _Whether you have Docker please skip this step_

Docker is supported by all major Linux distributions, MacOS and Windows.

[Download](https://www.docker.com/community-edition) and install Docker (Docker Engine, Compose, etc) 


**IMPORTANT** Allocate at least 3+Gb of RAM for Docker via Docker Settings > Advanced. 

## 2. Configure and deploy Drill4J Admin with Docker-Compose file

![image](/assets/img/d4j_img_download_docker_1.png)
<p><a href="/assets/files/0.5.0-rc1/docker-compose.yml" download><img src="/assets/img/d4j_img_download_docker_2.png" alt="image" /></a></p>


If you want to write a docker compose manually, you can use the latest compose descriptor example in [Github repository](https://github.com/Drill4J/drill4j.github.io/blob/master/assets/files/0.5.0-rc1/docker-compose.yml)

Start Drill4J using the following command and wait a bit.
```console

docker-compose -f docker-compose.yml -p drill up -d --force-recreate

```

## 3. Run your JVM application with Drill Agent

Download the archive with the agent distribution for your OS:  
[**Linux**](https://oss.jfrog.org/artifactory/oss-release-local/com/epam/drill/drill-agent-linuxX64/0.5.0-rc1/drill-agent-linuxX64-0.5.0-rc1.zip)    
[**MacOS**](https://oss.jfrog.org/artifactory/oss-release-local/com/epam/drill/drill-agent-macosX64/0.5.0-rc1/drill-agent-macosX64-0.5.0-rc1.zip)    
[**Windows**](https://oss.jfrog.org/artifactory/oss-release-local/com/epam/drill/drill-agent-mingwX64/0.5.0-rc1/drill-agent-mingwX64-0.5.0-rc1.zip)  
  and extract files.

To demonstrate the capabilities of the product, you can use Example Agent for Windows (based on Spring PetClinic Sample Application).    
>Download zip archive by the link [ExampleAgent.zip](/assets/files/0.5.0-rc1/ExampleAgent.zip) and run **start.bat**

or start **your** java project with parameters (example for Windows):
```console

-javaagent:{path_to_extracted_agent_folder}/drill-proxy.jar=ttl.agent.logger:STDOUT -agentpath:{path_to_extracted_agent_folder}/drill_agent.dll=drillInstallationDir={path_to_extracted_agent_folder},adminAddress=localhost:8090,agentId=ExampleAgent,buildVersion=0.1.0

```
> Use **.dll** for Windows, **.so** for Linux and **.dylib** agent file fo MacOS

## 4. Open Drill4J
Open new browser tab with Drill Admin [http://localhost:8091](http://localhost:8091)

Drill4J is ready for login. Press Continue as a guest button to get access.
 
The **last steps** before you can start working with Drill4J.  
Download [**drill-browser-extension.zip**](/assets/files/0.5.0-rc1/drill-browser-extension.zip) and install the browser extension for manual testing.

>Do not forget to register an agent before the start testing and add Test2Code plugin

Press "Register" button and follow registration wizards steps:
  * Fill all necessary general settings
  * Configure all necessary packages of your application
  * Add **Test2code** plugin
  
### Open your application and start testing   
> If you use Example Agent you can find it here [localhost:8080](http://localhost:8080)


## Also, if you want to try auto tests, follow this instruction:
[Install auto tests agent](/auto-tests-agent-guide/)

