---
layout: page
title: Autotests agent installation guidelines
permalink: /auto-tests-agent-guide/
---

For using Drill4J **Test-to-code mapping plugin** with api autotests (RESTful API) you need to add 
special auto tests agent to your test automation framework.

**IMPORTANT** JAVA 8 is required.

### 1. Clone [auto-tests-agent](https://github.com/Drill4J/auto-tests-agent) project
```console
git clone https://github.com/Drill4J/auto-tests-agent.git
```
### ...and build

```console
./gradlew clean build
```

### 2. Add to framework build configuration following instructions

_Gradle_ (to test task):
```gradle
val agentPath = System.getProperty("agentPath")
val adminUrl = System.getProperty("admin.url")
val adminId = System.getProperty("agent.id")
val pluginId = System.getProperty("plugin.id")
setJvmArgs(listOf("-javaagent:$agentPath=adminUrl=$adminUrl,agentId=$adminId,pluginId=$pluginId"))
```
_Maven_ (to configuration):
```pom
<systemPropertyVariables>
    <propertyName>agentPath</propertyName>
    <propertyName>admin.url</propertyName>
    <propertyName>agent.id</propertyName>
    <propertyName>plugin.id</propertyName>
</systemPropertyVariables>
<argLine>
   -javaagent:${agentPath}=adminUrl=${admin.url},agentId=${agent.id},pluginId=${plugin.id}
</argLine>
```

### 3. Run your auto tests with agent

For example, if you use _Gradle_ then the command may be looks like:

```console
./gradlew clean test -Dadmin.url=localhost:8090 -Dagent.id=ExampleAgent -Dplugin.id=test-to-code-mapping -DagentPath=../auto-tests-agent/build/libs/auto-tests-agent.jar  

```
...or for _Maven_:

```console
mvn clean test -Dadmin.url=localhost:8090 -Dagent.id=ExampleAgent -Dplugin.id=test-to-code-mapping -DagentPath=../auto-tests-agent/build/libs/auto-tests-agent.jar  

```
...where **admin.url** is a url of your _Drill Admin_, **agent.id** is _ID_ of _Drill Agent_ and **agentPath** is a path to
 **jar** file of the agent (we built this jar in _step 1_)
 