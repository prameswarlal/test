##Kibana

Kibana is an  analytics and visualization platform tool to visualize elasticsearch data. Data can be visualize in form of  charts, tables, and maps etc.


##Supported Tags

Kibana Version: 
- 5.0.0-alpha5 : [Dockerfile](https://github.com/prameswar/kibana/blob/master/5.0/Dockerfile) Tag: [latest](https://github.com/prameswar/kibana/tree/master/5.0)
- 4.5.4  : [Dockerfile](https://github.com/prameswar/kibana/blob/master/4.5/Dockerfile) Tag: [4.5](https://github.com/prameswar/kibana/tree/master/4.5)


## Installation
Pull docker image from [Dockerhub](https://hub.docker.com/r/prameswar/kibana/) using command 

```
docker pull prameswar/kibana
```
Above command will install `latest` version.

OR

You can install older version of kibana using tag.

```
docker pull prameswar/kibana:4.5
```
OR

You can clone repository and build kibana Dockerfile in your system.
```
https://github.com/prameswar/kibana.git
cd 4.5
docker build .
```
## Use kibana
list docker images 
```
docker images

REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
prameswar/kibana          latest              1135b6dbcb49        7 days ago          356 MB
```
Login docker image
```
docker run -d -ti --name kibana 1135b6dbcb49
docker exec -ti kibana /bin/bash
```
change `/etc/kibana/kibana.yml` for kibana configuration
Browse Kibana Dashboard at http://localhost:5601

## References
- [Kibana Documentation](https://www.elastic.co/guide/en/kibana/current/introduction.html)
