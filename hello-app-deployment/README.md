# Deploy a rest application on openshift

## Pre-requisite

1. Project Setup in openshift.
2. Docker Hub repository
3. OC client

```
	
	[root@localhost hello-app-deployment]# oc login --token=<access-token> --server=https://api.us-east-1.online-starter.openshift.com:6443
Logged into "https://api.us-east-1.online-starter.openshift.com:6443" as "sanketgupta07" using the token provided.

You have one project on this server: "scloud"

Using project "scloud".
[root@localhost openshift-tryouts]# oc new-app docker.io/sannketgupta07/hello-rest-app --name hello-app
--> Found Docker image 824a728 (About a minute old) from docker.io for "docker.io/sannketgupta07/hello-rest-app"

    * An image stream tag will be created as "hello-app:latest" that will track this image
    * This image will be deployed in deployment config "hello-app"
    * Port 8080/tcp will be load balanced by service "hello-app"
      * Other containers can access this service through the hostname "hello-app"
    * This image declares volumes and will default to use non-persistent, host-local storage.
      You can add persistent volumes later by running 'oc set volume dc/hello-app --add ...'
    * WARNING: Image "docker.io/sannketgupta07/hello-rest-app" runs as the 'root' user which may not be permitted by your cluster administrator

--> Creating resources ...
    imagestream.image.openshift.io "hello-app" created
    deploymentconfig.apps.openshift.io "hello-app" created
    service "hello-app" created
--> Success
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose svc/hello-app'
    Run 'oc status' to view your app.
[root@localhost git]# oc get po
NAME                 READY   STATUS      RESTARTS   AGE
hello-app-1-deploy   0/1     Completed   0          11m
hello-app-1-rxrvh    1/1     Running     0          11m
[root@localhost openshift-tryouts]# oc expose svc hello-app
route.route.openshift.io/hello-app exposed
	
```

![App status in openshift project](https://raw.githubusercontent.com/sanketgupta07/openshift-tryouts/master/hello-app-deployment/imgs/ose-app-status.jpg)

![App pod in Openshift](https://raw.githubusercontent.com/sanketgupta07/openshift-tryouts/master/hello-app-deployment/imgs/ose-app-pod.jpg)

![Application route in openshift after exposing service (svc)](https://raw.githubusercontent.com/sanketgupta07/openshift-tryouts/master/hello-app-deployment/imgs/ose-app-route.jpg)

![Application in web browser](https://raw.githubusercontent.com/sanketgupta07/openshift-tryouts/master/hello-app-deployment/imgs/hello-app-page.jpg)


