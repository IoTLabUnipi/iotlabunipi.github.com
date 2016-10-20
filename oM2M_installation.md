---
layout: page
title: "OM2M Installation"
description: "OM2M Download and Setup"
---
{% include JB/setup %}

# Prerequisites
* Git
* Apache Maven
* Oracle Java 8

#### Install Git

```bash
$ sudo apt-get install git
```

#### Install Apache Maven

```bash
$ sudo apt-get install maven
```

#### Install Oracle Java 8

```bash
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer
```

##### Configure JAVA_HOME 
To set this environment variable, we will first need to find out where Java is installed. You can do this by executing:

```bash
$ sudo update-alternatives --config java
```

Copy the path from your preferred installation and then open `/etc/environment` using nano or your favorite text editor.

```bash
$ sudo nano /etc/environment
```

At the end of this file, add the following line, making sure to replace the highlighted path with your own copied path.

```vim
JAVA_HOME="/usr/lib/jvm/java-8-oracle"
```

Save and exit the file, and reload it.

```bash
$ source /etc/environment
```
You can now test whether the environment variable has been set by executing the following command:

```bash
$ echo $JAVA_HOME
```

This will return the path you just set.

# Configure Eclipse for developing oM2M
First of all, install the lastest [Eclipse for RCP and RAP Developers](http://www.eclipse.org/downloads/packages/eclipse-rcp-and-rap-developers/neon1a) (at time of writing Eclipse Neon 1).

### Install Tycho Plugin
Click Window -> Preferences -> maven -> discovery -> open catalog and type Tycho. Check the “Tycho Configurator” checkbox and install the connector.

### Clone oM2M repository
* Select Window->Show View -> Other.
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