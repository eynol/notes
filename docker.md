

[Return to content](../index.md)
##  docker.host.internal

If there is a application running on your host machine and listen at port 3000, how to connect to that port inside a docker container? On Windows or MacOS, you can use `host.docker.internal` in docker containers to refer your host machine. On linux, use the following configuration.

`docker run --add-host=host.docker.internal:host-gateway xxx`

or 

```yml
services:
  foo:
    image: alpine
    extra_hosts:
      - "host.docker.internal:host-gateway" 
```


[Return to content](../index.md)