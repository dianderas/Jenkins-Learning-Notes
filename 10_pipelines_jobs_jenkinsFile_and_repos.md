- se debe crear un archivo con el codigo de jenkins pipeline a un repositorio
- luego se puede obtener y ejecutar el job desde dicha fuente del repositorio
- en la configuracion de pipeline en lugar de escribirlo elegimos la opcion "Pipeline Script from SCM"
  - SCM: Git
  - Repository URL
  - Credentials
  - Branch
  - Script Path: JenkinsFileSeptimoPipeline

output
```
Started by user Enzo Neyra

Obtained JenkinsFileSeptimoPipeline from git https://github.com/dianderas/Jenkins-Learning-Notes
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins
 in /var/jenkins_home/workspace/Septimo-Pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential GITHUB_CREDENTIALS
Cloning the remote Git repository
Cloning repository https://github.com/dianderas/Jenkins-Learning-Notes
 > git init /var/jenkins_home/workspace/Septimo-Pipeline # timeout=10
Fetching upstream changes from https://github.com/dianderas/Jenkins-Learning-Notes
 > git --version # timeout=10
 > git --version # 'git version 2.39.5'
using GIT_ASKPASS to set credentials Credenciales de github
 > git fetch --tags --force --progress -- https://github.com/dianderas/Jenkins-Learning-Notes +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/dianderas/Jenkins-Learning-Notes # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision ab96c5ec0a070c4d209dcebf1c14813de82842d1 (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f ab96c5ec0a070c4d209dcebf1c14813de82842d1 # timeout=10
Commit message: "first commit"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Saludo 1)
[Pipeline] echo
Hola desde saludo 1
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Saludo 2)
[Pipeline] echo
Hola desde saludo 2, paso 1
[Pipeline] echo
Hola desde saludo 2, paso 2
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Imprimir Variable de entorno)
[Pipeline] echo
@enrael
[Pipeline] echo
@enrael
[Pipeline] echo
@enrael
[Pipeline] echo
=============================
[Pipeline] sh
+ echo hola-mundo
hola-mundo
[Pipeline] sh
+ echo @enrael
@enrael
[Pipeline] sh
+ echo @enrael
@enrael
[Pipeline] sh
+ echo @enrael
@enrael
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Imprimir Variables de entorno definida en System)
[Pipeline] echo
@enrael
[Pipeline] echo
@enrael
[Pipeline] echo
@enrael
[Pipeline] sh
+ echo @enrael
@enrael
[Pipeline] sh
+ echo @enrael
@enrael
[Pipeline] sh
+ echo @enrael
@enrael
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS

```