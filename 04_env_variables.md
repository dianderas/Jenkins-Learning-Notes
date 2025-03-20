Como usar variables de entorno:
```shell
echo $BUILD_NUMBER
echo ${BUILD_NUMBER}
echo $BRANCH_NAME
```
```
Started by user Enzo Neyra
Running as SYSTEM
Building in workspace /var/jenkins_home/workspace/Despliegues/Despliegue 2
[Despliegue 2] $ /bin/sh -xe /tmp/jenkins1856043131307100191.sh
+ echo 3
3
+ echo 3
3
+ echo

Finished: SUCCESS
```
- Muchas varibles de entorno se agregan por la instalacion de algun plugin
- Hay algunas variables que pueden dar null y esto es debido al contexto. Es si en un job no estas utilizando Git, sus
    variables de entorno, que estan disponibles globalmente, devolveran null.

Para crear variables de entorno:
- Manage Jenkins > System > [Global properties]
- check en Environment variables > Add

```shell
echo "el instagram de enzo es: $INSTAGRAM ${INSTAGRAM}"
```
```
Started by user Enzo Neyra
Running as SYSTEM
Building in workspace /var/jenkins_home/workspace/Despliegues/Despliegue 2
[Despliegue 2] $ /bin/sh -xe /tmp/jenkins710186646586727153.sh
+ echo el instagram de enzo es: @enrael @enrael
el instagram de enzo es: @enrael @enrael
Finished: SUCCESS
```

- Algo importante de recordar es que las variables de entorno con VISIBLES, es decir, no es lugar para colocar datos sensibles.