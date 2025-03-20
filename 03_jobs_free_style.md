- Jobs Free style
- Puede crear un job como shell
  - Al crear un Job se genera un workspace en el servidor 
  - Podemos interactuar con los archivos de nuestro servidor desde jenkins:

Enntrando al Job en "Configure" >> Build Steps (Execute shell)
```shell
echo "hola mundo"
pwd
echo "dasdasdad" >> holamundo.txt
ls
cat holamundo.txt
cat hola-mundo.txt
```

Dentro del job en "Console Output"
```
Started by user Enzo Neyra
Running as SYSTEM
Building in workspace /var/jenkins_home/workspace/clase-1
[clase-1] $ /bin/sh -xe /tmp/jenkins1785992597109538728.sh
+ echo hola mundo
hola mundo
+ pwd
/var/jenkins_home/workspace/clase-1
+ echo dasdasdad
+ ls
hola-mundo.txt
holamundo.txt
+ cat holamundo.txt
dasdasdad
+ cat hola-mundo.txt
holamundo
Finished: SUCCESS
```