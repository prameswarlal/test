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


### Todos
