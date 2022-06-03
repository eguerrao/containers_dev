### Build image:
```console
$ docker build -t scl .
```
### Run container:
```console
$ docker run -it -h licencias -d -p 27021:27020 scl 
```
### Getting MAC address from container
```console
docker inspect <container name or id> |grep MacAddress|tr -d ' ,"'|sort -u
```
