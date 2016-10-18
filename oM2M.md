---
layout: page
title: "OM2M"
description: "oM2M"
group: navigation
---
{% include JB/setup %}

# Prerequisites
* Git
* Apache Maven
* Oracle Java 8

#### Install Git
```
$ sudo apt-get install git
```

#### Install Apache Maven
```
$ sudo apt-get install maven
```

#### Install Oracle Java 8
```
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
```

##### Configure JAVA_HOME 
To set this environment variable, we will first need to find out where Java is installed. You can do this by executing:

```
$ sudo update-alternatives --config java
```

Copy the path from your preferred installation and then open `/etc/environment` using nano or your favorite text editor.

```
$ sudo nano /etc/environment
```

At the end of this file, add the following line, making sure to replace the highlighted path with your own copied path.

```
JAVA_HOME="/usr/lib/jvm/java-8-oracle"
```

Save and exit the file, and reload it.

```
$ source /etc/environment
```
You can now test whether the environment variable has been set by executing the following command:

```
$ echo $JAVA_HOME
```

This will return the path you just set.

# Configure Eclipse for developing oM2M
First of all, install the lastest [Eclipse for RCP and RAP Developers](http://www.eclipse.org/downloads/packages/eclipse-rcp-and-rap-developers/neon1a) (at time of writing Eclipse Neon 1).

### Install Tycho Plugin
Click Window -> Preferences -> maven -> discovery -> open catalog and type Tycho. Check the “Tycho Configurator” checkbox and install the connector.

### Clone oM2M repository
* Select Window->Show View -> Other .
* In the dialog box, select the Git view.
* Click on “Clone a Git repository”.
* In the URI form type: https://git.eclipse.org/r/om2m/org.eclipse.om2m 
* In the second page, keep **ONLY** the “master” branch checkbox selected and click Next.
* In the third page, check the “import all existing projects after clone finishes” and click “Finish”.
* This will clone the oM2M repository inside: `$HOME/git/`

# Build oM2M

### Build from shell

Replace the $HOME with your home folder path.

```bash
$ cd $HOME/git
$ mvn clean install
```

### Build from Eclipse

* Select “org.eclipse.om2m” package and right click
* Select “Run as -> maven install”

#### Build Results

Two Eclipse products will be generated after a successful built:
* The IN product can be found on this *generic* directory:

```bash
$HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.in-cse/target/products/in-cse/<os>/<ws>/<arch>
```

* The MN product can be found on this *generic* directory:

```bash
$HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.mn-cse/target/products/mn-cse/<os>/<ws>/<arch>
```

* The ASN product can be found on this *generic* directory: 

```bash
$HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.asn-cse/target/products/asn-cse/<os>/<ws>/<arch>
```

where on a linux environment running in a 64 bit machine the last part of each URI is translated to: 

```bash
linux/gtk/x86_64
```

# Test oM2M

In the following I will assume you are using a linux environment running in a 64 bit machine, if it is not the case replace the last three segments of each URI according to your deployment.
Go to the IN-CSE product directory: 

```
$ cd $HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.in-cse/target/products/in-cse/linux/gtk/x86_64
```

If it is the first time you are runnin oM2M issue:

```
$ chmod a+x start.sh
```

In any case to start the platform:

```
$ ./start.sh
```

It will start the OSGi console with all the needed bundle already deployed. Type `ss` to view the list of bundles. The output will be similar to the following:

```bash
osgi> ss
"Framework is launched."

id      State       Bundle
0       ACTIVE      org.eclipse.osgi_3.10.2.v20150203-1939
1       RESOLVED    javax.servlet_3.1.0.v20140303-1611
2       RESOLVED    javax.xml_1.3.4.v201005080400
3       RESOLVED    org.apache.commons.codec_1.6.0.v201305230611
4       RESOLVED    org.apache.commons.logging_1.1.1.v201101211721
                    Fragments=25
5       ACTIVE      org.apache.felix.gogo.command_0.10.0.v201209301215
6       ACTIVE      org.apache.felix.gogo.runtime_0.10.0.v201209301036
7       ACTIVE      org.apache.felix.gogo.shell_0.10.0.v201212101605
8       RESOLVED    org.apache.httpcomponents.httpclient_4.3.6.v201411290715
9       RESOLVED    org.apache.httpcomponents.httpcore_4.3.3.v201411290715
10      ACTIVE      org.eclipse.equinox.console_1.1.0.v20140131-1639
11      ACTIVE      org.eclipse.equinox.http.jetty_3.0.200.v20131021-1843
12      ACTIVE      org.eclipse.equinox.http.servlet_1.1.500.v20140318-1755
13      RESOLVED    org.eclipse.equinox.launcher_1.3.0.v20140415-2008
14      RESOLVED    org.eclipse.jetty.continuation_8.1.16.v20140903
15      RESOLVED    org.eclipse.jetty.http_8.1.16.v20140903
16      RESOLVED    org.eclipse.jetty.io_8.1.16.v20140903
17      RESOLVED    org.eclipse.jetty.security_8.1.16.v20140903
18      RESOLVED    org.eclipse.jetty.server_8.1.16.v20140903
19      RESOLVED    org.eclipse.jetty.servlet_8.1.16.v20140903
20      RESOLVED    org.eclipse.jetty.util_8.1.16.v20140903
21      ACTIVE      org.eclipse.om2m.binding.coap_1.0.0.20161018-0857
22      ACTIVE      org.eclipse.om2m.binding.http_1.0.0.20161018-0857
23      RESOLVED    org.eclipse.om2m.binding.service_1.0.0.20161018-0857
24      RESOLVED    org.eclipse.om2m.commons_1.0.0.20161018-0857
25      RESOLVED    org.eclipse.om2m.commons.logging_1.0.0.20161018-0857
                    Master=4
26      ACTIVE      org.eclipse.om2m.core_1.0.0.20161018-0857
27      RESOLVED    org.eclipse.om2m.core.service_1.0.0.20161018-0857
28      ACTIVE      org.eclipse.om2m.datamapping.jaxb_1.0.0.20161018-0857
29      RESOLVED    org.eclipse.om2m.datamapping.service_1.0.0.20161018-0857
30      RESOLVED    org.eclipse.om2m.interworking.service_1.0.0.20161018-0857
31      ACTIVE      org.eclipse.om2m.persistence.eclipselink_1.0.0.20161018-0857
32      RESOLVED    org.eclipse.om2m.persistence.service_1.0.0.20161018-0857
33      ACTIVE      org.eclipse.om2m.webapp.resourcesbrowser.xml_1.0.0.20161018-0857
34      RESOLVED    org.eclipse.osgi.services_3.4.0.v20140312-2051
osgi> 

```

* Open your browser and connect to the address "http://127.0.0.1:8080/webpage" to access the IN-CSE web interface.
* Enter username "admin" and password "admin" then click on login button to display the IN-CSE resource tree.
* After a successful authentication, the in-cse resource will be displayed. You can see the "in-cse" CseBase sub-resources and attributes. 

