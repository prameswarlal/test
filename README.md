#Filebeat

Filebeat is a log data shipper.  It ships log files either to Logstash for parsing or directly to Elasticsearch for indexing.


#Supported Tags

Filebeat Version: 
- 5.0.0-alpha5 : [Dockerfile](https://github.com/prameswar/filebeat/blob/master/5.0/Dockerfile) Tag: [latest](https://github.com/prameswar/filebeat/tree/master/5.0)
- 1.2.3  : [Dockerfile](https://github.com/prameswar/filebeat/blob/master/1.2/Dockerfile) Tag: [1.2](https://github.com/prameswar/filebeat/tree/master/1.2)
- 1.1.2  : [Dockerfile](https://github.com/prameswar/filebeat/blob/master/1.1/Dockerfile) Tag: [1.1](https://github.com/prameswar/filebeat/tree/master/1.1)
- 1.0.1  : [Dockerfile](https://github.com/prameswar/filebeat/blob/master/1.0/Dockerfile)  Tag: [1.0](https://github.com/prameswar/filebeat/tree/master/1.0)

## Installation
Pull docker image from [Dockerhub](https://hub.docker.com/r/prameswar/filebeat/) using command 

```
docker pull prameswar/filebeat
```
Above command will install `latest` version.

OR

You can install older version of filebeat using tag.

```
docker pull prameswar/filebeat:1.2
```
OR

You can clone repository and build filebeat Dockerfile in your system.
```
git clone https://github.com/prameswar/filebeat.git
cd 1.2
docker build .
```
## Use filebeat
list docker images 
```
docker images

REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
prameswar/filebeat        latest              b491dda413ec        8 days ago          235 MB
```
Login docker image
```
docker run -d -ti --name filebeat b491dda413ec
docker exec -ti filebeat /bin/bash
```
change `/etc/filebeat/filebeat.yml` according to your requirement 
```
filebeat:
  # List of prospectors to fetch data.
  prospectors:
    # Each - is a prospector. Below are the prospector specific configurations
    -
      # Paths that should be crawled and fetched. Glob based paths.
      # For each file found under this path, a harvester is started.
      paths:
        - "/var/log/*.log"
        #- c:\programdata\elasticsearch\logs\*

      # Type of the files. Based on this the way the file is read is decided.
      # The different types cannot be mixed in one prospector
      #
      # Possible options are:
      # * log: Reads every line of the log file (default)
      # * stdin: Reads the standard in
      input_type: log
```
Output to elasticsearch
```
output:
  ### Elasticsearch as output
  elasticsearch:
     hosts: ["10.0.10.5:9200"]
```
OR

Output to logstash
```
output:
  logstash:
    hosts: ["10.0.10.6:5044"]
```
## References
- [Filebeat Documentation](https://www.elastic.co/guide/en/beats/filebeat/current/filebeat-overview.html)
