##Elasticsearch

Elasticsearch is a full-text search and analytics engine. It is a high scalable search engine. Read elasticsearch [Documentation](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html) for more information.  


##Supported Tags

Elasticsearch Version: 
- 5.0.0-alpha5 : [Dockerfile](https://github.com/prameswar/elasticsearch/blob/master/5.0/Dockerfile) Tag: [latest](https://github.com/prameswar/elasticsearch/tree/master/5.0)
- 2.3.5  : [Dockerfile](https://github.com/prameswar/elasticsearch/blob/master/2.3/Dockerfile) Tag: [2.3](https://github.com/prameswar/elasticsearch/tree/master/2.3)
- 2.2.2  : [Dockerfile](https://github.com/prameswar/elasticsearch/blob/master/2.2/Dockerfile) Tag: [2.2](https://github.com/prameswar/elasticsearch/tree/master/2.2)
- 2.1.2 : [Dockerfile](https://github.com/prameswar/elasticsearch/blob/master/2.1/Dockerfile)  Tag: [2.1](https://github.com/prameswar/elasticsearch/tree/master/2.1)
- 2.0.2 : [Dockerfile](https://github.com/prameswar/elasticsearch/blob/master/2.0/Dockerfile) Tag: [2.0](https://github.com/prameswar/elasticsearch/tree/master/2.0)

## Installation
Pull docker image from [Dockerhub](https://hub.docker.com/r/prameswar/elasticsearch/) using command 

```
docker pull prameswar/elasticsearch
```
Above command will install `latest` version.

OR

You can install older version of elasticsearch using tag.

```
docker pull prameswar/elasticsearch:2.3
```
OR

You can clone repository and build elasticsearch Dockerfile in your system.
```
git clone https://github.com/prameswar/elasticsearch.git
cd 2.3
docker build .
```
## Use elasticsearch
list docker images 
```
docker images

REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
prameswar/elasticsearch   latest              692d02c3b921        7 days ago          649.9 MB
```
Login docker image
```
docker run -d -ti --name elasticsearch 692d02c3b921
docker exec -ti elasticsearch /bin/bash
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
