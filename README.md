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
![CPD-OPERATOR](images/cpd-operators.PNG?raw=true)
- To Navigate ***ibm-common-services***
```
$oc project ibm-common-services
```
![IBM-COMMON-SERVICES](images/ibm-common.PNG?raw=true)

**1.6 Monitor the critical objects running in the CP4D projects**
- When it comes to the project level in OCP, there are such a critical component that needs to be monitored. [kubernetes Objects](https://chkrishna.medium.com/kubernetes-objects-e0a8b93b5cdc)
   - ***i. Deployments***
   - ***ii. Pods***
   - ***iii. Services***
   - ***iv. Route***
   - ***v. Config map***
   - ***vi. Secrets***

- To check the various objects on the project that needs to be executed the following command
```
To view all pods in the project
$oc get pods
```
:point_right:[PODS](https://docs.openshift.com/online/pro/architecture/core_concepts/pods_and_services.html)
```
To viwe all the deployments in the project
$oc get deployment
```
:point_right:[DEPLOYMENT](https://docs.openshift.com/container-platform/4.6/applications/deployments/what-deployments-are.html)
```
To View all the services in the project
$oc get service
```
:point_right:[SERVICES](https://docs.openshift.com/online/pro/architecture/core_concepts/pods_and_services.html)
```
To View all the route in the projects
$oc get route
```
:point_right:[ROUTE](https://docs.openshift.com/container-platform/4.10/networking/understanding-networking.html)
```
To View all the config maps in the project
$oc get cm
```
:point_right:[CONFIG-MAP](https://docs.openshift.com/container-platform/4.9/nodes/pods/nodes-pods-configmaps.html)
```
To View all the secrets in the project
$oc get secret
```
:point_right:[SECRETS](https://docs.openshift.com/container-platform/3.11/dev_guide/secrets.html#:~:text=The%20Secret%20object%20type%20provides,sensitive%20content%20from%20the%20pods.)
```
To View all objects in the project
$oc get all
```
