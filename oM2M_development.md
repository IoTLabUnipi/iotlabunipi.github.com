---
layout: page
title: "OM2M Development"
description: ""
---
{% include JB/setup %}

# Prerequisites

### Postman

Postman is a chrome extensions which allows to send http REST requests with custom headers.

* Install Chrome
* Install Postman extension

### Californium

In order to simulate CoAP connected devices, you must download Californium.

* Open Eclipse
* Select Window -> Show View -> Other.
* In the dialog box, select the Git view.
* Click on “Clone a Git repository”.
* In the URI form type: https://github.com/eclipse/californium.git 
* In the second page, keep **ONLY** the “master” branch checkbox selected and click Next.
* Click “Finish”.
* This will clone the oM2M repository inside: `$HOME/git/californium/`.
* Select File -> Import
* In the dialog box, select Maven -> Existing Maven Project.
* In the Root Directory type: `$HOME/git/californium/`.
* Click “Finish”.

# Create your new Application Dedicated Node (ADN)

* Open Eclipse
* Select File -> New -> Project.
* In the dialog box, select Maven -> Maven Project.
* Click on "Next".
* Check the "Create a simple project" and click Next.
* In the second page, choose a Group id and an artifact id (e.g. it.unipi.iot.om2m and lamp, respectively).
* Click “Finish”.

### Add Californium dependencies

* Open the `pom.xml` file of your project.
* Switch to the last tab called `pom.xml`
* Add the following dependencies and Maven repository to your pom.xml (without the dots) inside the project tag:

```xml
<dependencies>
...
    <dependency>
            <groupId>org.eclipse.californium</groupId>
            <artifactId>californium-core</artifactId>
            <version>1.1.0-SNAPSHOT</version>
    </dependency>
...
</dependencies>
...
<repositories>
...
    <repository>
      <id>repo.eclipse.org</id>
      <name>Californium Repository</name>
      <url>https://repo.eclipse.org/content/repositories/californium/</url>
    </repository>
    ...
</repositories>
```


### Create the Main Class

* Right click on your project folder in the Project Structure Tab (on the left)
* Select New -> Class
* In the dialog box type the name of your class and set the package according to the Group id selected for the project (it is not required but it is a good practice).
* Check the "public static void main(String[] args)" in the stub creation section and click Finish.
* Finally to make your jar executable modify the `pom.xml` adding the following before the `</project>` closing tag:

```xml
<build>
		<pluginManagement>
			<plugins>
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-jar-plugin</artifactId>
					<version>3.0.2</version>
					<configuration>
						<archive>
							<manifest>
								<addClasspath>true</addClasspath>
								<mainClass>$PACKAGE.$MAINCLASS</mainClass>
								<addDefaultImplementationEntries>true</addDefaultImplementationEntries>
							</manifest>
						</archive>
						<descriptorRefs>
							<descriptorRef>jar-with-dependencies</descriptorRef>
						</descriptorRefs>
					</configuration>
				</plugin>
			</plugins>
		</pluginManagement>
  </build>
```

where in my example `$PACKAGE = it.unipi.iot.om2m` while `$MAINCLASS = Lamp`.

#### Run your application

* Go inside your project root folder, e.g. `$HOME/workspace/lamp`.
* Type `mvn clean install`. It will generate the jar file inside the target folder.
* Execute your application by issuing:

```bash
$ java -jar target/$ARTIFACTID-0.0.1-SNAPSHOT.jar
```

where in my example `$ARTIFACTID = lamp`.