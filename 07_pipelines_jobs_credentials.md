- Jenkins Manager > (Security) Credentials > (Store) System > Global credentials
- Existen varios de tipos de credenciales para crear https://www.jenkins.io/doc/pipeline/steps/credentials-binding/. Ejemplo: Username with password
  - Username
  - Password
  - Treat username as secret (check input)
  - ID
    - Se requiere para referenciales en un pipeline.
    - No puede ser modificado una vez creado.
  - Description
- Otro ejemplo de tipo es el Secret Text
  - Secret
  - ID
  - Description
```
pipeline {
    agent any
    stages {
        stage('Imprimir credenciales') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId:'github_credentials', 
                    usernameVariable: 'CUSTOM_USER', 
                    passwordVariable: 'CUSTOM_PASSWORD'
                    )]) {
                        script {
                            echo "El nombre usuario es: $CUSTOM_USER y la contraseña es: $CUSTOM_PASSWORD"
                        }
                    }
                withCredentials([string(
                    credentialsId: 'SECRET',
                    variable: 'MY_CUSTOM_SECRET'
                    )]) {
                        script {
                            echo "El valor de mi texto secreto es: $MY_CUSTOM_SECRET"
                        }
                    }
            }
        }
    }
}
```

```
Started by user Enzo Neyra
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/jenkins_home/workspace/Tercer-Pipeline
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Imprimir credenciales)
[Pipeline] withCredentials
Masking supported pattern matches of $CUSTOM_PASSWORD
[Pipeline] {
[Pipeline] script
[Pipeline] {
[Pipeline] echo
Warning: A secret was passed to "echo" using Groovy String interpolation, which is insecure.
		 Affected argument(s) used the following variable(s): [CUSTOM_PASSWORD]
		 See https://jenkins.io/redirect/groovy-string-interpolation for details.
El nombre usuario es: enrael y la contraseña es: ****
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // withCredentials
[Pipeline] withCredentials
Masking supported pattern matches of $MY_CUSTOM_SECRET
[Pipeline] {
[Pipeline] script
[Pipeline] {
[Pipeline] echo
Warning: A secret was passed to "echo" using Groovy String interpolation, which is insecure.
		 Affected argument(s) used the following variable(s): [MY_CUSTOM_SECRET]
		 See https://jenkins.io/redirect/groovy-string-interpolation for details.
El valor de mi texto secreto es: ****
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // withCredentials
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
- los valores de las credenciales estan encryptadas al imprimirse, pero para su usu durante el pipeline si ejecutara correctamente.