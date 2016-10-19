---
layout: page
title: "OM2M Startup"
description: ""
---
{% include JB/setup %}

# Start IN-CSE

In the following I will assume you are using a linux environment running in a 64 bit machine, if it is not the case replace the last three segments of each URI according to your deployment.
Go to the IN-CSE product directory: 

```bash
$ cd $HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.in-cse/target/products/in-cse/linux/gtk/x86_64
```

If it is the first time you are runnin oM2M issue:

```bash
$ chmod a+x start.sh
```

In any case to start the IN_CSE:

```bash
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

* Open your browser and connect to the address [http://127.0.0.1:8080/webpage](http://127.0.0.1:8080/webpage) to access the IN-CSE web interface.
* Enter username "admin" and password "admin" then click on login button to display the IN-CSE resource tree.
* After a successful authentication, the in-cse resource will be displayed. You can see the "in-cse" CseBase sub-resources and attributes. 

# Start MN-CSE

Open another terminal and go to the MN-CSE product directory 

```bash
$ cd $HOME/git/om2m/org.eclipse.om2m/org.eclipse.om2m.site.mn-cse/target/products/mn-cse/linux/gtk/x86_64
```

If it is the first time you are runnin oM2M issue:

```bash
$ chmod a+x start.sh
```

In any case to start the MN_CSE:

```bash
$ ./start.sh
```

It will start the OSGi console with all the needed bundle already deployed. Type `ss` to view the list of bundles.


* The MN-CSE automatically authenticate to the remote IN-CSE specified in the gateway configuration file. If the IN-CSE is not already running, the MN-CSE keep sending authentication requests (A request each 10 seconds).
* After a successful authentication, the “mn-cse” resource is added to the in-cse resource tree, and respectively the “in-cse” resource is added to the mn-cse resource tree. You can now access the registered MN-CSE resource from the [IN-CSE web interface]("http://127.0.0.1:8080/webpage) under the “/in-cse/in-name/mn-cse” uri.
* Using the In-CSE web interface you can seamlessly access to all authenticated gateways. You notice the existence of one authenticated MN-CSE with id "mn-cse".
* Click on the "mn-cse" resource to display remote MN-CSE sub-resources and attributes. You can click on the “mn-cse” button of the “link” attribute to connect to the MN-CSE resources tree (Located in the right table).
* The MN-CSE resource tree will be displayed. At this moment, the IN-CSE will act as a proxy to retarget your requests to the MN-CSE.
* Initially, also the MN-CSE contains the CseBase resource (id=mn-cse), the AccessRight resource (id=acp_admin), and other empty collections.