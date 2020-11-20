# Hello World Docker-Composer para Openshift

> Nesse exemplo não é explorado ajustes na aplicação que esta sendo importada.
>
> Uma vez que a mesma faz uso de porta privilegiadas (abaixo 1024) se fez necessário habilitar explicitamente essa permissão.

```shell
$ export USER_ID=$(oc whoami)
$ oc new-project ${USER_ID}-compose

$ curl -o docker-compose.yaml https://raw.githubusercontent.com/kubernetes/kompose/master/examples/docker-compose-v3.yaml
$ docker-compose up
# ... acessar http://localhost
$ docker-compose down
```

## Conversão

```shell
$ mkdir yaml && cd $_
$ kompose convert -f ../docker-compose.yaml
$ cd ..
$ oc apply -R -f yaml/
```

> AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 10.1.2.21. Set the 'ServerName' directive globally to suppress this message
> (13)Permission denied: AH00072: make_sock: could not bind to address [::]:80
> (13)Permission denied: AH00072: make_sock: could not bind to address 0.0.0.0:80
> no listening sockets available, shutting down
> AH00015: Unable to open logs

```shell
# login como admin!
$ oc -n user2-compose adm policy add-scc-to-user anyuid -z default
# criar a rota do frontend e testar...

# baixar as app's
$ oc scale --replicas=0 deployment --all
```

# Referência:

- https://kompose.io/