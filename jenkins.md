jenkins:
-------
Q)What is jenkins?
------------------
* it is a coontinuous integartion (CI) and continuous deployment (CD) tool.

Q)what is cI and CD?
----------------------

* CI means integrate the developers code. CD means deliver or deploy the code into the different envirnoment (QA,pre-production,production).
- It is a java based application.
- it will help to automate the process of code integraton,code build,code delivery.
- it is a opensource tool like hudson/bamboo/teamcity.
- jenkins has original name as hudson.
- Jenkins is the core part of the devops.
- jenkins will connect to the scm,qa,tomcat,production,etc. to interact with these system.
- it is interacted with those systems with the plugins.
- it is plugin based tool.
- nearly 1000+ plugins jenkins will support.

Q)important section of jenkins?
-------------------------------
 - Plugin management.
 - global tool management.
 - job management.
 - jenkins dashboard.
 - user management.
 - security management.
 - slave connection.

Q)Role of Devops Engineer (or) Build and Release Engineer?
----------------------------------------------------------
 - Installation and configuration.
 - plugin management.
 - user management.
 - security management.
 - global tool management.
 - creating jobs.
 - monitoring jobs.
 - jobs pipeline
 - integrating different tools.
 - taking jenkins backup.
NOTE: in jenkins server git must and should install.

Steps to install:
-----------------
 1. 
 - set up the repositories.
 - install jenkins (yum -y install jenkins)
 2. 
 - set up docker environment
 - download jenkins image.
 - start the container.
 3. 
 - download jenkins.war LTS file from offical site
 - start jaenkins.war (java -jar jenkins.war)
 4. 
 - download tomcat 7
 - download jenkins.war
 - copy jenkins.war file into the webapps folder of the tomcat (/opt/apache-tomcat-7-xx/ webapps/)
 - start the tomcat. (./startup.sh)

Configuration:
-------------
1)unlock the jenkins use admin password
 - cat /home/shivaji/.jenkins/secrets/AdminPasword
2) install the required plugins.
3)setup the user and password.
4)login to the dashboard using username and password.

Plugin Management:
-----------------
**Q)what is plugin ?**
  plugin is a additional software.it will help to interact with the other systems.
 under plugin mangement we can install,update,remove the plugins.
Manage jenkins--manage plugins

Global tool management:
----------------------
these are tools it will help develop the application like maven.
difference between tool and plugin
 we can maintin multiple versions of tool.
but we can maintain only single version of plugin.
Manage jenkins----global tool configuration

Job management:
--------------

**Q)what is job?**
  job means task. to build ,integration ,delivery these kind of tasks we can handle in jenkins job management.
 job is a core part of the jenkins.job will pull the code from scm server.build the application if successfully build delivery the code.

There are different types of jobs:
----------------------------------
1. free style
   we can integrate any type of files.
2. maven job
   we can integrate only java files
3. pipeline jobs
  sequence of jobs, one job is connected to anothr job.
4. multipipe line jobs

**Q)how to schedule a job in jenkins?**
 - get the code from scm server (github)
 - setting trigger (build process trigger)
 - setup build environment
 - build acion
 - post build action

build maven Job in jenkins:
---------------------------
code compile:
code test:
code integration:
code package:
for job pipeline install the "build pipeline plugin"
here trigger the job as build after other job.

deploy:
-------
for deploy the code into tomcat install "deploy to container plugin"
at post build action setup the "deploy war/ear to container"

backup:
-------
for jenkins server backup install "backup plugin"

email notification in jenkins:
-----------------------------
install the plugin "email extension plugin", "email extension template plugin"
configure mailserver,port,smtp authentication in "system configure"

User management:
---------------
1. install necessary plugin
  role based authorization strategy	
2. create users
	Manage jenkins ---> Manage users --> create users
	dev_user
	test_user
	manager
3. create roles
	developer
	tester
 for this you need to enable "role based strategy" in "configure global security"




