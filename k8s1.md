

KUBERNETES: it have 8 charectores  between k and s



* Need of k8s
    * High availability: some applications will go down k8s try to restart the containers 
    * Autoscalling: containers don’t scale on there own

 	    Horizontal: increase the no. of containers

	    Vertical: increase the size of container

    * Zero down time deployment:

        roolout:new version

        roolback:old version

        we have any bugs in new version we went to choose old version(for example we take ubuntu 20.04 sor the installation of azuredevops agent)

* DISTRIBUTED SYSTEM: multiple machines can work (master node , node )

* CLUSTER: combination of multiple machines but it speaks or looks like one machine(that is master server)

* STATE: storage

* STATEFULL: store your application in your local s/m

* STATELESS:it can be stored in external (storing in db)

* MONOLITH: running hole application in one server

* MICRO SERVICES: we splite the huge application into simple steps

* DESIRED STATE:
    1) declarative: docker file (or)docker-compose.yaml 

    2) imperative:using command lines (it is not a correct approach)

* In kubernetes we don't have pets mind set(means cannot connect emotionally for special treatment of healthcheck) . we have cattle mindset (means one of the cow will be sick its replaced by other one )

* kubernetes is not only desired  for docker 

* MASTERNODE:
    1)kubeAPI: all the communications (internal/external)in k8s will done by kubeAPI  server . It exposes funtionally over HTTP(S)protocol& provide REST API
        kube api can understand only json & http languages , manifest yaml files understand by kubeapi we use "kubeconfig"

    2) Etcd: it has own life ; any thing stored in k8s cluster we need etcd. all k8s stored in etcd(defalut & non-default): cluster crash ayipotea backup cheayalsina componet etcd.

    3) SHEDULER: in k8s we want to create  something new node(object) by using of scheduler.(its responsible for maintaining desired state)
     sheduler communicate with API  and API communicate with node 
     sheduler----API---node

     4)CONTROLLER: controller manager is responsible for maintaining desired state.(changes jarigite contrller manageer check cheasi matramea controller daniki saripade size ni batti node ni choose cheastumdhi) 
        (this recognation loop that checks for desired state . to did assigned work to scheduler by controller)
    5) cloud component management
    
WORKER NODE: 
    1) kubelet: control plan is assigned any work that work will be done by kubelet(agent)(to pass information from worker node to master node)

    2) conntainer runtime: container technology to be used in k8s cluster(Docker , docker support, ....)

    3) kube-proxy: this component is responsible for networking for containers on the node.

    container network interface pluggins:(ex: planner, calico, wave unit)
   
    CLOUD CONTROLE MANAGEMENT

* EKS:elastic kubernetes service

* AKS:azure kubernetes service

* GKE: google kubernetes engine

* CONTROL PLAN: example:how do you run 4 components is our choise

* MASTER: example:all of 4 components are placed in master plan

* KUBELET: its sends status will be send to after finishing work of kubectl what ever work assigned by controlplane

* CONTAINER RUNTIME: container technology to be used in k8s cluster

* KUBE_PROXY: this component is responsible for networking of containers on the node

* KUBE CTL CONFIG: which contains api-server information, kubectl allows to communication with cluster to create resources.

* for high availability cluster we choose only odd no. of services

* kubeadm: the command to bootstrap the cluster.


kubelet: the component that runs on all of the machines in your cluster and does things like starting pods and containers.

kubectl: the command line util to talk to your cluster.



* k8s object: every thing in k8s is an object

* CATALOG: list of all the requests(menu) 

* PODS: k8s creates smallest unit is called pod , 
    pod is automatic unit of creation of k8s    ,   
    every pod have specific ip adress(not for container)    , 
    docker containers placed inside the pod ,
    pods speaks creating base job   .

* CRON JOB: sheduling base job

* JOB:somthing runs in one time, a job does not deleted by itself , we have to delete it.
        vi job.yaml
        kubectl apply -f job.yaml
        kubectl delete -f job.yaml
        
* SCALLING: to create no.of pods, scalling in k8s is ncreases no.of pods not containers.  pods can assigned to node
* containers go down k8s trying to restartthe containers .
* OCI:  Open container Initiative work is  stores the function's logs in Oracle Cloud Infrastructure (or in an external logging destination. When the function has finished executing and after a period being idle, the Docker container )
* SHIM: create containers periodically interface b/w docker to kubernetes

* PODS LIFE CYCLE:
    1)pending: "once your container connected to your pods it takes some time "

    2) running:

    3) succeed: " finished/complete the exeution"

    4)failed: "one container in the pod was terminated means stop"

    5) unknown:"error state(no communications between two containers)

* CONTAINER STATES IN K8S PODS: 

    1) waiting:
    2) running:
    3) terminated

* CONTAINER RESTART POLICY:

    restartpolicy:onfailure(error code never restarted only success code is restarted we take two different codes)

    restartpolicy:never(after complte the state k8s cannot try to restart the container )

    restartpolicy:always(default)(container always restarts when desired state will be compleated)



    * INSTALL KUBERNETIES:
    IN MASTER AND NODE

    * # Run these commands as root
###Install GO###
> wget https://storage.googleapis.com/golang/getgo/installer_linux

chmod +x ./installer_linux

./installer_linux

source ~/.bash_profile

> git clone https://github.com/Mirantis/cri-dockerd.git

>cd cri-dockerd

> mkdir bin

> go build -o bin/cri-dockerd

> mkdir -p /usr/local/bin

> install -o root -g root -m 0755 bin/cri-dockerd /usr/local/bin/cri-dockerd

> cp -a packaging/systemd/* /etc/systemd/system

> sed -i -e 's,/usr/bin/cri-dockerd,/usr/local/bin/cri-dockerd,' /etc/systemd/system/cri-docker.service

> systemctl daemon-reload

> systemctl enable cri-docker.service

> systemctl enable --now cri-docker.socket

> sudo apt-get update

> sudo apt-get install -y apt-transport-https ca-certificates curl

> sudo curl -fsSLo /etc/apt/keyrings/kubernetes-archive-keyring.gpg https://packages.cloud.google.com/apt/doc/apt-key.gpg

> echo "deb [signed-by=/etc/apt/keyrings/kubernetes-archive-keyring.gpg] https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list

> sudo apt-get update

> sudo apt-get install -y kubelet kubeadm kubectl

> sudo apt-mark hold kubelet kubeadm kubectl
>  


* CRONJOB: job starts every one hour or week or month we use cronjob
* in spec we have controllers .
  in controllers we have cronjobs
  in cronjob we have jobs(templete)
  in job we have pods
  in pods we have containers
* controller basically maintaines to another k8s resources

* BACKOFFLIMIT: job have back of limit to limit number of restarts and active dead line seconds to limit time period of execution.

![image](./Images/11.png)
* we can delete the job (contrller)  then pods(child objects) also deleted
* pods dosnot maintain any state .
* now if we want to access the application in container we can doport - forword (not in the container)
    kubectl port-forword <application name> 
* we can't port forward the application inside the container. (kubectl port-forword --address "0.0.0.0"<pod name>8080:80)

  kubectl not recommended because it's does not a client approch . it's only in my local laptop its application works,      

  thats way we cannot recomended this application

* pod is a smallest component in the k8s . so it's a workload not a controller

* job is a controller because it controles another k8s job

* cronjob is a contoller becacuse it controlles another k8s job

*  HEALTH CHECKS/PROBES:  
 1: LIVENESS PROBE:   this checks fails k8s restart the container
 2: READINESS PROBE: when rediness probe is passed to service  the forword request passsed to pod , it fails the pod will be removed from pods
 3: STARTUP PROBES: every thing in your application is starts
* (probes) or checks can be performed on applications are running or not inside the container we check by using probes.

EXEC: when my application is not good how to restart the container(run any linux/windows command which returns status exit code)
  http: 1 -information 
        2- success
        3- restart
        4- somthing which not present
  GRPC: grpc is also one of the  communication mechanisom


  ---------------------

PODS WIth SPECIFIC reSOURCES: (cpu/memory)
 resources are two types  
1) requests: manimum memory utilization(ex: memory:64Mi , cpu: 250m)

2) limits:maximum memory utilizatin ( ex: memory: 256Mi ,  cpu: 1000m)

container: containers are threetypes 

1)normal container:

2) init container: init containers are containers job cannot run continuously , if one container will be down then init container works
till actual containers will up then init  containers will stop work.

----
![image](./Images/10.png)

3)ephemeral container: 

SCALLING: scallings are three types 
    1) horizontal scalling: depends on workload  then number of pods  increasing/decreasing
    2) vertical scalling: depends on workload size of the podm will be increases or decreases
    3) node scalling: kubeadm join

 
 * CONTROLLER:

 ![image](./Images/12.png) 

 deployment: deployment depends on two objects

    1) roolout: goto latest version(kubectl roolout --help)
        a) deployment
        b) deamon sets
        c) stateful sets
                in statefull applications store data locally . in containers the data  created locally will be lost once you delete it . so to solve this is docker we have used volumes , volumes have a lifecycle which has no relations to container ifecycle (refer volumes , image layers, containers)
                
                VOLUMES: 
                once you delete pod volume also deleted
                to store the data is called volue
                volumes are three types
                1) storage on cloud (ebs, azuredisk, efs , azure life & gcr)
                2) empty directory
                3) host path
 ![image](./Images/13.png)
 statefulset: each  pod have it's own volume is called k8s cluster . it's more predictable names
 we can access individual pod by creating headless service 

 HEADLESS SERVICE: service don't have ip address , it's runs name and name space
 SYNTAX: <podname>.<service name>.<namespace>
 
 name space: name space is used  to create verctual (isolated) space for every  pods 


 ![image](./Images/14.png)

                SHAD:  one process break into multiple functionality records is called shad.
 


                persisted volume is a live where your volume is dead

                CSI: controller storage volme(max. companies follws to storage)

                SSD: standers storage disks will not concurrensive but nod is acts concurrences

![image](./Images/16.png)

    2) undoroolout(roolback): when bugs occure in present version goto previous version

storage: 
    recreating: delete pod its replaced by default it takes desired state (no. of pods) we increase pods it will start newer version .recreate don't have downtime . its not create one by one its create all pods at a time by using storage percentage.

ANNOTATIONS: change-cause (is not a funtionality it's manage data)
    change deployment >>> change annotatins
        +
        every time you get a new version 
        +
        don't chage image we change only tag


DEAMONSET(ds): it's a  Controller which creates pod on every selected nodes in kubernetes cluster

    1) log collector 
    2) agents
    node will be deleted pods also deleted

NODE-SELECTOR: spec>> node name >> node selector( for this approch is not good approch, we always prefer label approch)
>> we pods apply on nodes then we shedule depends on senarios 
    a) node effinity
    b) pod effinity

SERVICE: 
![image](./Images/15.png)
![image](./Images/26.png)
![ss](./Images/27.png)

* port: which port you want to give the application to run

* target port : which port deafault added to the application runs

* k8s resources will be of 2 categories by scope 
    cluster resource
    name space resource

    ### Creating namespace: kubctl create ns <name>

* we configure pods  are 2 types 
        1) we use envronment
        2) inside a container command & args

        There are four different ways that you can use a ConfigMap to configure a container inside a Pod:
Inside a container command and args

Environment variables for a container

Add a file in read-only volume, for the application to read

Write code to run inside the Pod that uses the Kubernetes API to read a ConfigMap


* ### environment variables(envfrom) cannot be changed once we create the pod.
    env.variable we have to update the pods  only before we create the pods , after creation of pods some changes in the pod env.var they cannot be updated.

* this   config map is not a secret approch so we use base64 
 ### echo '<name>'  | base64
 * container - env - secret ref(we place data in secret approch its better than config)

 ### k8slens:
 monitoring open source tool

 ### valut:
 encript the data 

 ### RBAC:
 ![images](./Images/31.png)
  RBAC are two types they are 
    (1) authentication (for ex: to enter hall with movie ticket)
        * role (spoke with namespace )
            (role is nothing but policy , we apply our role into any user is called identity)
            ## identity
            identity are 4 types
            (1)user (humans)
            (2) group (humans)
            (3)service(programming tools)
            (4) account ( access to services user: & password:)

        * cluster role ( applicable entair cluster)
    (2) autherization( where your allow and where yor denied)

### identity:
![images](./Images/32.png)

 idertity is a person or system who access is called identity

 * role binding: role communicate with identity
 * cluserrole binding: cluster role communicate with identity

 ### OIDC:
  open id connects (this oidc is supports fbusers, msusers , google users ...)
  
## formula
      kubectl api-resources --namespaced=true

### Creating namespace: kubctl create ns <name>

### K8s has many installation options

single node k8s cluster

k3c
kind
minikube

Multi node k8s cluster

manual installations:
kube-adm : single master k8s cluster we use kube adm
kube-spray :
kops :

* kind is type of object

* metadata describes some additional information about object you are       trying to create (name, labels)

* spec: This is the desired state

* To get all the api-resources in your k8s cluster

###  What is CNI ?
     
     CNI – Container Network Interface

    Docker containers for networking have a Standard CNM (Container Network Model)

    CNI (Container Network Interface) is another standard which also speaks about networking to container runtime.

    CNI Plugins implement networking functionalities. In the case of k8s Networking is implemented by CNI and we have an option to choose the CNI Plugin in bare metal installations.

    CNI Plugins help kube-proxy to give a unique ip address to every Pod in the k8s cluster.

    * Some of the popular CNI Plugins
        Weave Net
        Flannel
        Calico
        Self Hosted K8s
![hema](./Images/35.png)

    K8s installations will not have default CNI. So post installtion of k8s cluster we need to install any CNI implementation which works for us

    kubelet on the node creates the container inside the Pod by using container runtime (Docker/CRI-o).

    Each Pod requires a network connection which is provided by kube-proxy which requires CNI to assist.

![oo](./Images/36.png)

### ### What is default dns in k8s?

    Kubernetes offers a DNS cluster addon, which most of the supported environments enable by default. In Kubernetes version 1.11 and later, CoreDNS is recommended and is installed by default with kubeadm.

    K8s can expose the service to the external world

    nodePort:
     Expose the service to the particular port on all the nodes of k8s cluster

    loadBalancer:
     Exposes the service to the loadbalancer
     
    external:
     Creates a DNS record which can be added to DNS servers maintaine by your org.
    





