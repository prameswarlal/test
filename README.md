##Logstash

Logstash is an open source data collection engine with real-time pipelining capabilities. Logstash can dynamically parse and ship data of different types inputs, filters, and outputs. It support more than 200 plugins. For more information Read [Logstash Documentation](https://www.elastic.co/guide/en/logstash/current/introduction.html)


##Supported Tags

Logstash Version: 
- 2.3.4-1 : [Dockerfile](https://github.com/prameswar/logstash/blob/master/2.3/Dockerfile) Tag: [latest](https://github.com/prameswar/logstash/tree/master/2.3)
- 2.2.4-1  : [Dockerfile](https://github.com/prameswar/logstash/blob/master/2.2/Dockerfile) Tag: [2.2](https://github.com/prameswar/logstash/tree/master/2.2)
- 2.1.3-1  : [Dockerfile](https://github.com/prameswar/logstash/blob/master/2.1/Dockerfile) Tag: [2.1](https://github.com/prameswar/logstash/tree/master/2.1)
- 2.0.0-1  : [Dockerfile](https://github.com/prameswar/logstash/blob/master/2.0/Dockerfile)  Tag: [2.0](https://github.com/prameswar/logstash/tree/master/2.0)

## Installation
Pull docker image from [Dockerhub](https://hub.docker.com/r/prameswar/logstash/) using command 

```
docker pull prameswar/logstash
```
Above command will install `latest` version.

OR

You can install older version of Logstash using tag.

```
docker pull prameswar/logstash:2.2
```
OR

You can clone repository and build Logstash Dockerfile in your system.
```
git clone https://github.com/prameswar/logstash.git 
cd 2.3
docker build .
```
## Use Logstash
list docker images 
```
docker images

REPOSITORY                TAG                 IMAGE ID            CREATED             SIZE
prameswar/logstash        2.3                 19aa20a050c4        6 days ago          759 MB
```
Login docker image
```
docker run -d -ti --name logstash 19aa20a050c4
docker exec -ti logstash /bin/bash
```
add input, output and filter config file to  `/etc/logstash/conf.d/` 

Sample input file 
```
input {
  file {
    type => "syslog"
    path => ["/var/log/auth.log", "/var/log/syslog"]
    start_position => beginning
    sincedb_path => "/dev/null"
  }
}
```
Sample output file to push logs to elasticsearch
```
output {
  elasticsearch {
    hosts => "localhost"
  }
}
```

## References
- [Logstash Documentation](https://www.elastic.co/guide/en/logstash/current/introduction.html)
