---
layout: page
title: "OM2M Configuration"
description: ""
---
{% include JB/setup %}

# Server (IN-CSE) configuration

* Go to the IN-CSE product directory: 

```bash
$ cd $HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.in-cse/target/products/in-cse/<os>/<ws>/<arch>
```

* Edit the file `configuration/config.ini` to configure the IN-CSE. **(You can keep the current configuration for a local demo)**

|Parameter|Description|Example|
|---------|-----------|-------|
|org.eclipse.om2m.cseType|CSE type|	IN
|org.eclipse.om2m.cseBaseAddress|	IN-CSE ip address	|127.0.0.1|
|org.eclipse.equinox.http.jetty.http.port|	IN-CSE HTTP listening port|	8080|
|org.eclipse.om2m.coap.port|	IN-CSE CoAP listening port|	5683|
|org.eclipse.om2m.cseBaseContext|	IN-CSE listening context|	/|
|org.eclipse.om2m.dbDriver|	IN-CSE Database driver|	org.h2.Driver|
|org.eclipse.om2m.dbUrl|	IN-CSE Database file location|	jdbc:h2:./database/nscdb|
|org.eclipse.om2m.dbUser|	IN-CSE Database user name|	om2m|
|org.eclipse.om2m.dbPassword|	IN-CSE Database password|	om2m|
|org.eclipse.om2m.dbReset|	IN-CSE Database reset when starting|	true|
|org.eclipse.om2m.cseBaseId|	IN-CSE CseBase resource id|	in-cse|
|org.eclipse.om2m.cseBaseName|	IN-CSE CseBase resource name|	in-name|
|org.eclipse.om2m.cseBaseProtocol.default|	IN-CSE Default communication protocol|	http|
|org.eclipse.om2m.maxNrOfInstances|	Maximum number of content instances in a Container|	1000|
|org.eclipse.om2m.adminRequestingEntity|	IN-CSE Default admin requesting entity. (username / password)|	admin:admin|
|org.eclipse.om2m.guestRequestingEntity|	IN-CSE Default guest requesting entity. (username / password)|	guest:guest|

# Gateway (MN-CSE) configuration

* Go to the MN-CSE product directory: 

```bash
$ cd $HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.mn-cse/target/products/mn-cse/<os>/<ws>/<arch>
```

* Edit the file `configuration/config.ini` to configure the MN-CSE. **(You can keep the current configuration for a local demo)**

|Parameter|Description|Example|
|---------|-----------|-------|
|org.eclipse.om2m.cseType|CSE type|	MN
|org.eclipse.om2m.cseBaseAddress|	MN-CSE ip address	|127.0.0.1|
|org.eclipse.equinox.http.jetty.http.port|	MN-CSE HTTP listening port|	**8181**|
|org.eclipse.om2m.coap.port|	MN-CSE CoAP listening port|	**5684**|
|org.eclipse.om2m.cseBaseContext|	MN-CSE listening context|	/|
|org.eclipse.om2m.dbDriver|	MN-CSE Database driver|	org.h2.Driver|
|org.eclipse.om2m.dbUrl|	MN-CSE Database file location|	**jdbc:h2:./database/mncsedb**|
|org.eclipse.om2m.dbUser|	MN-CSE Database user name|	om2m|
|org.eclipse.om2m.dbPassword|	MN-CSE Database password|	om2m|
|org.eclipse.om2m.dbReset|	MN-CSE Database reset when starting|	true|
|org.eclipse.om2m.cseBaseId|	MN-CSE CseBase resource id|	**mn-cse**|
|org.eclipse.om2m.cseBaseName|	MN-CSE CseBase resource name|	**mn-name**|
|org.eclipse.om2m.cseBaseProtocol.default|	MN-CSE Default communication protocol|	http|
|org.eclipse.om2m.maxNrOfInstances|	Maximum number of content instances in a Container|	1000|
|org.eclipse.om2m.adminRequestingEntity|	MN-CSE Default admin requesting entity. (username / password)|	admin:admin|
|org.eclipse.om2m.guestRequestingEntity|	MN-CSE Default guest requesting entity. (username / password)|	guest:guest|


to specify the remote IN-CSE to which the MN should be authenticated in the same file:

|Parameter|Description|Example|
|---------|-----------|-------|
|org.eclipse.om2m.remoteCseId|	Remote MN Id|	in-cse|
|org.eclipse.om2m.remoteCseBaseName|	in-name|
|org.eclipse.om2m.remoteCseAddress|	Remote MN ip address|	127.0.0.1|
|org.eclipse.om2m.remoteCsePort|	Remote MN listening port|	8080|
|org.eclipse.om2m.remoteCseContext|	Remote MN listening context|	/|

* You can configure MN-CSE and IN-CSE to work on distributed machines.
* You can configure multiple MN-CSEs by setting different identifiers.

