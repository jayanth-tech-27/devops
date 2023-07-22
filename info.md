api gateway is exposed to internet
saturation in which server is saturated requests from users will be increased
some basic checks to applications like network is goes to application or not
tracing is used to when we installed tracing tools in the application we enable tracing what will happen is at which point code is fail.it will show all info related to code
tracing is costlier
eventvwr for windows logs in win+r
memory is ram
f12 in webpage
curl I https://ipaddress
apm can never tell system failures.it will tell all the application failures
elastic stack major components are opensource
everthing stored in elastic search
kibana is ui of elastic search
beats are installed on the server which application is running
elastic x-pack is for notifications
logstash is to fetch meaningful info
elastic stack is combo of elk
horizontal scaling is increase of servers{replicas} vertical means increase of ram or memory in one server itself
in elastic search index can have multiple documents of same type.each record is json document
sudo journalctl --unit elasticsearch for logs in elastic search
elastic search runs default by 9200 port
from elastic 8 it will become secure use https
to ignore ssl certification use "curl --insecure https://localhost:9200
login user elastic
use "curl --insecure -u elastic:password https://localhost:9200 use credentials generated in installation
to communicate with elastic search we use rest apis
in configuration file http.host means connect from any network interface i.e, local host 127.0.0.1 and ipaddress
we have index apis

####
procedure to configure elastic search and kibana in ubuntu
when we install elastic search we got
--------------------------- Security autoconfiguration information ------------------------------

Authentication and authorization are enabled.
TLS for the transport and HTTP layers is enabled and configured.

The generated password for the elastic built-in superuser is : # password whichcan be used in login #

If this node should join an existing cluster, you can reconfigure this with
'/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node --enrollment-token <token-here>'
after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with
'/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with
 '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'.

Generate an enrollment token for Elasticsearch nodes with
'/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node'.

-------------------------------------------------------------------------------------------------
### NOT starting on installation, please execute the following statements to configure elasticsearch service to start automatically using systemd
 sudo systemctl daemon-reload
 sudo systemctl enable elasticsearch.service
### You can start elasticsearch service by executing
 sudo systemctl start elasticsearch.service
install elastic search in ubuntu and copy the security configuration to login elastic search with insecure
by using we login into elasticsearch "curl --insecure -u elastic:password https://localhost:9200"
the data we got is 
{
  "name" : "ip-172-31-22-94",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "J0HbZbaZTg-RRW8tMvIvlg",
  "version" : {
    "number" : "8.6.2",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "2d58d0f136141f03239816a4e360a8d17b6d8f29",
    "build_date" : "2023-02-13T09:35:20.314882762Z",
    "build_snapshot" : false,
    "lucene_version" : "9.4.2",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
}

#### install kibana
####
kibana runs on 5601
after configure kibana we got to sudo vi /etc/kibana/kibana.yml
change following
server.host to 0.0.0.0 to listen all hosts
create a token after install kibana 
to communicate kibana and elastic search use "sudo /usr/share/bin/elasticsearch-create-enrollment-token -s kibana"
a token is created
save the token
browse kibana by using http://publicip:5601
it will ask enrolllment token
use this enrollment command "/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node"
####
to reset password use "sudo /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic"
login into web using http://ipaddress:5601 and it will ask enrollment and user name and password of elastic search
logs are in var/log/elasticsearch
sudo journalctl --unit elasticsearch
each log is a document it is stored in index
apache server cannot read java
tail -f for view last few lines in file
http methods get{to get info} post{send info} put{send info} delete
in properties log level is mentioned

log formats of different applications:
apache2:
eg:
115.98.186.251 - - [15/Mar/2023:10:34:26 +0000] "GET / HTTP/1.1" 200 3460 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/111.0.0.0 Safari/537.36"
"%h %l %u %t \"%r\" %>s %b" common
postgresql:
format:
<date_utc> <hostname> postgres[<pid>] : [<group_id>] <sql_error_code> <session_id> <message_type>: <message>
eg:
Feb 24 14:58:08 webappsecure postgres[7694]: [10-1] 42701 530b5e00.1e0e ERROR: column "requests" of relation "sessiongroup" already exists
tomcat:
eg: 127.0.0.1 - sccott [10/Nov/2020:13:55:35 -0700] "GET /server-status HTTP/1.1" 200 2326
format:
input plugins: it will where logs will come from or from some port.is it a file.beats
filter plugins: 
output plugins:elastic search
splunk:etl
index is like table in database
man ls to help in commands
stdin means typing something on terminal
stdoutput is giving the output
escape sequence: \", \? before special characters we use \
codecs: output plugins.output format.
default codec format is rubydebug
to kill process use "kill pid"
in filter user add fields and tag for giving extra info
when mentioning hash means {}
in filters we have
mututate is for basic transformations.
in mututate we have uppercase try to see the fields and write it in uppercase 
 sudo /usr/share/logstash/bin/logstash -f /home/ubuntu/elk/new.conf --log.level trace
 in above --log.level trace is for tracing the logs
 