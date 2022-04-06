# OpenUniversity Openshift Cluster Monitoring RunBook

## OCP Services and Monitoring
**1.1 Steps to Login to OCP Portal UI**
- Go to the [Console Page] (https://console-openshift-console.apps.cp4d4.dev.wkc.open.ac.uk) in the browser, it will be landing to Login page.

- Select ***mit_htpasswd_provider*** and enter the Username and Password to login.
![LOGIN-PAGE](images/login-page.PNG?raw=true)

- Enter the ***Username and Password*** to login to the cluster.
![USERNAME-PASSWORD](images/username-page.PNG?raw=true)

- Once logged in, you can see the OCP cluster homepage
![HOMEPAGE](images/OCP-overviewpage.PNG?raw=true)

**1.2 Steps to Login to OCP VIA CLI**
- Navigate to ***mit_reader user*** which is located on top right corner of the OCP cluster home page, and select ***Copy login command*** :point_right:[OC Cheat Sheet](https://livebook.manning.com/book/openshift-in-action/oc-cheat-sheet/)

- It will request to enter the cluster credentials ***(Follow Step 1.1)***

- The browser re-directs to display token page, Click the Display token :point_down:
![DISPLAY TOKEN](images/token.PNG?raw=true)

- API token has generated, copy the login command and execute it to the local terminal. [CLI Download and install](https://docs.openshift.com/online/pro/cli_reference/get_started_cli.html) ![CLI-LOGIN](images/login-cli.PNG?raw=true)

**1.3 Monitoring the Node status**
- To execute a single command to view and verify the nodes those which are running in the OCP cluster
```
$oc get nodes
```

- All the nodes should be in the Ready state, so that the cluster up and running perfectly.![CLUSTER-STATUS](images/cluster-status.PNG?raw=true)

**1.4 Monitoring the status of the projects**
- To execute the following command to list and check the status of the available projects in the OCP cluster.
```
$oc get project
```

- Here can see all the projects, and there are three projects which related to CP4D services
   - ***i cpd-instance***
   - ***ii. cpd-operators***
   - ***iii. ibm-common-services*** 
![PROJECT-STATUS](images/project-status.PNG?raw=true)

**1.5 Navigate to CP4D project**
- To navigate any project, it requires to be executed the following command
```
$oc project <project-name>
```
- We have three projects are running which related to CP4D services in ***DEV CLUSTER***
![PROJECT-STATUS](images/project-status.PNG?raw=true)

- To Navigate ***cpd-instance project***
```
$oc project cpd-instance
```
![CPD-INSTANCE](images/cpd-instance.PNG?raw=true)
- To Navigate ***cpd-operators***
```
$oc project cpd-operators
```
![CPD-OPERATOR](images/cpd-operator.PNG?raw=true)
- To Navigate ***ibm-common-services***
```
$oc project ibm-common-services
```
![IBM-COMMON-SERVICES](images/ibm-common.PNG?raw=true)

