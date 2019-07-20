# Java (openjdk-11) skeleton application

## Getting started

### Install tln-cli
* link

### Attach to the existing project
* Add skeleton as subtree
```
git remote add tln-java https://github.com/project-talan/tln-java.git
git subtree add --prefix services/api tln-java master --squash
```
* Update to get latest version
```
git subtree pull --prefix services/api tln-java master --squash
```

### or Fork/clone repository
To develop standalone project, just clone repository or create fork using your account

### Refresh configuration
* execute **tln prereq** from the project's home using command line
* Update environment variables inside **.env** file
```
COMPONENT_GROUP_ID=io.company.project.services
COMPONENT_ARTIFACT_ID=api
COMPONENT_ID=io.company.project.services.api
COMPONENT_VERSION=19.8.0-SNAPSHOT
COMPONENT_PARAM_HOST=localhost
COMPONENT_PARAM_LSTN=0.0.0.0
COMPONENT_PARAM_PORT=80
COMPONENT_PARAM_PORTS=443
COMPONENT_PARAM_SSL_CERTS=
COMPONENT_PARAM_CORS_WHITELIST=
```
### Generate project skeleton using maven
```
tln generate-jersey-grizzly2
```
### Add missing dependencies
```
<dependency>
  <groupId>javax.xml.bind</groupId>
  <artifactId>jaxb-api</artifactId>
  <version>2.3.0</version>
</dependency>
<dependency>
  <groupId>com.sun.xml.bind</groupId>
  <artifactId>jaxb-impl</artifactId>
  <version>2.3.0.1</version>
</dependency>
<dependency>
  <groupId>com.sun.xml.bind</groupId>
  <artifactId>jaxb-core</artifactId>
  <version>2.3.0.1</version>
</dependency>
<dependency>
  <groupId>javax.activation</groupId>
  <artifactId>javax.activation-api</artifactId>
  <version>1.2.0</version>
</dependency>
```
### Update compilation plugin
```
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-compiler-plugin</artifactId>
  <version>3.8.1</version>
  <inherited>true</inherited>
  <configuration>
    <source>11</source>
    <target>11</target>
  </configuration>
</plugin>
```
### Add assemply plugin
```
<plugin>
  <artifactId>maven-assembly-plugin</artifactId>
  <version>3.1.1</version>
  <executions>
    <execution>
      <phase>package</phase>
      <goals>
        <goal>single</goal>
      </goals>
    </execution>
  </executions>
  <configuration>
    <archive>
      <manifest>
        <addClasspath>true</addClasspath>
        <mainClass>${project.groupId}.${project.artifactId}.Main</mainClass>
      </manifest>
    </archive>
    <descriptorRefs>
      <descriptorRef>jar-with-dependencies</descriptorRef>
    </descriptorRefs>
  </configuration>
</plugin>
### Migration tutorials
* http://www.javainthebox.com/2018/07/case-study-of-migration-to-java-se-11.html
* https://winterbe.com/posts/2018/08/29/migrate-maven-projects-to-java-11-jigsaw/
* https://medium.com/@Leejjon_net/migrate-a-jersey-based-micro-service-to-java-11-and-deploy-to-app-engine-7ba41a835992

### HTTP/HTTPS
* During deployment procedure, create ssl folder under project's root with two sertificates. Use your project id as files' names
```
  io.company.project.services.api.key
  io.company.project.services.api.crt
```
* otherwise, **http** access will be configured


## SDLC


| command  | Description |
| ------------- | ------------- |
| tln  prereq | Prepare local dev box configuration scripts |
