

```shell
$ export USER_ID=$(oc whoami)
$ oc new-project ${USER_ID}-compose

$ curl -o docker-compose.yaml https://raw.githubusercontent.com/kubernetes/kompose/master/examples/docker-compose-v3.yaml
$ docker-compose up
# ... acessar http://localhost
$ docker-compose down
```



```shell
$ kompose convert
```



# Referência:

- https://kompose.io/