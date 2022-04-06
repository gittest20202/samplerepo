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
***$oc get nodes***
```
