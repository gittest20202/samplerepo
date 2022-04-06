# OpenUniversity Openshift Cluster Monitoring RunBook
<p align="center">
  <img 
    width="100"
    height="100"
    src="images/ocp-logo.png"
  >
</p>

## OCP Services and Monitoring
**1.1 Steps to Login to OCP Portal UI**
- Go to the 
     - [OU Dev Console Page](https://console-openshift-console.apps.cp4d4.dev.wkc.open.ac.uk) in the browser, it will be landing to Login page.
     - [OU PROD Console Page](https://console-openshift-console.apps.cp4d.live.wkc.open.ac.uk/) in the browser, it will be landing to Login page.
     - [BSI DEV Console Page](https://console-openshift-console.apps.cp4d.datagovernancedev.bsigroup.com/) in the browser, it will be landing to Login page.

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
  - :point_right:[PODS](https://docs.openshift.com/online/pro/architecture/core_concepts/pods_and_services.html)
  ```
    To view all pods in the project
    $oc get pods
  ```
  - :point_right:[DEPLOYMENT](https://docs.openshift.com/container-platform/4.6/applications/deployments/what-deployments-are.html)
  ```
    To viwe all the deployments in the project
    $oc get deployment
  ```
  - :point_right:[SERVICES](https://docs.openshift.com/online/pro/architecture/core_concepts/pods_and_services.html)
  ```
    To View all the services in the project
    $oc get service
  ```
  - :point_right:[ROUTE](https://docs.openshift.com/container-platform/4.10/networking/understanding-networking.html)
  ```
    To View all the route in the projects
    $oc get route
  ```
  - :point_right:[CONFIG-MAP](https://docs.openshift.com/container-platform/4.9/nodes/pods/nodes-pods-configmaps.html)
  ```
  To View all the config maps in the project
  $oc get cm
  ```
  - :point_right:[SECRETS](https://docs.openshift.com/container-platform/3.11/dev_guide/secrets.html#:~:text=The%20Secret%20object%20type%20provides,sensitive%20content%20from%20the%20pods.)
  ```
  To View all the secrets in the project
  $oc get secret
  ```
  ```
  To View all objects in the project
  $oc get all
  ```

**1.7 Steps to diagnostic when pods are not in running state**
- If any pod is not running state from CP4D related project, it needs to be troubleshot

- To check the pods which excludes the state of ***Running and Completed***, that needs to be executed the following command.
```
Navigate to respective project

$ oc project <project-name>
```
```
Check the pod status

$ oc get pods | grep -v 'Running\|Completed'
```
![POD-STATUS](images/pod-status.PNG?raw=true)

- There are some pods are in the error state, hence it needs to be investigated in-order to troubleshoot.

- To investigate the pod, initial step that needs to be checked the ***log files*** and execute the following commands to get the log
```
$ oc logs <pod-name>
```

- To get additional information, that needs to be executed the following command
```
$ oc describe pod <pod-name>
```

**1.8 Steps to diagnostic in the project level issues**
- Navigate to the respective project ***($ oc project <project-name>)***
```
 $oc project cdp-instance
         or
 $oc project cpd-operators
         or
 $oc project ibm-common-services	 
``` 

- Execute the following commands to check the event log
```
$ oc get events
```
**1.9 Monitoring the Node Workload Using Grafana**
- To access the Grafana GUI, that needs to be executed the following url from the web browser. [Grafana Tutorials](https://grafana.com/tutorials/)

[GRAFANA-DASHBOARD](https://grafana-openshift-monitoring.apps.cp4d4.dev.wkc.open.ac.uk/?orgId=1)
![Grafana](images/grafana-dashboard.PNG?raw=true)

- ***Select USE Method/Node*** option to view the node utilization

- ***Select the desired node*** from instance and view all the utilization such CPU, Memory, Net, Disk for the respective node.
![Grafana](images/grafana-dashboard1.PNG?raw=true)

***Monitoring Pod and Container Workload using Prometheus***
- Understand Prometheus Basic Query Querying basics | Prometheus

- To access the Prometheus use the following web url 
  [PROMETHEUS-DASHBOARD](https://prometheus-k8s-openshift-monitoring.apps.cp4d4.dev.wkc.open.ac.uk)

- Once the page has loaded, can see the Prometheus homepage
![PROMETHEUS](images/prometheus-dashboard.PNG?raw=true)

- Choose ***Graph*** option on the homepage
![PROMETHEUS](images/prometheus-dashboard1.PNG?raw=true)
  - To check the and verify the workload on all the pods, that needs to use the following query command
  ```
  sort_desc(topk(10, sum by (pod)(container_memory_working_set_bytes{container="",pod!="",namespace="cpd-instance"})))
  ```
  - Paste the query on the Prometheus search box to see the utilization graph.
   ![PROMETHEUS](images/prometheus-dashboard2.PNG?raw=true)
  
  - To verify the utilization for the single pod that needs to use the following command
  ```
  sort_desc(topk(10, sum by (pod)(container_memory_working_set_bytes{container="",pod="c-db2oltp-iis-db2u-0",namespace="cpd-instance"})))
  ```
  ![PROMETHEUS](images/prometheus-dashboard3.PNG?raw=true)

**1.10 Verifying the ETCD Cluster health status**
- ETCD is the heart of the cluster, where all the cluster information’s are stored.Its like a database of the running cluster

- To check the ETCD cluster health status use the following url 
[ETCD-DATABASE STATUS](https://grafana-openshift-monitoring.apps.cp4d4.dev.wkc.open.ac.uk/d/c2f4e12cdf69feb95caa41a5a1b423d9/etcd?orgId=1&refresh=5s)
![ETCD-STATUS](images/etcd-status.PNG?raw=true)
- Command Line to check ETCD health
```
$ oc get etcd -o=jsonpath='{range .items[0].status.conditions[?(@.type=="EtcdMembersAvailable")]}{.message}{"\n"}
```
