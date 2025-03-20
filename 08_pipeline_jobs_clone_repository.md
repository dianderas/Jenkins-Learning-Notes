- para evitar el ingreso manual de usuario y password, estos se puede adjuntar al comando del clone
- necesita contemplar casos de que el repo ya exista en el agente, se podria limpiar el workspace previamente.

```
pipeline {
    agent any
    
    stages {
        stage("Clear workspace") {
            steps {
                script {
                    sh "rm -rf ./*"
                }
            }
        }
        stage("Gir clone") {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'GITHUB_CREDENTIALS',
                    usernameVariable: 'GITHUB_USERNAME',
                    passwordVariable: 'GITHUB_PASSWORD'
                    )]) {
                        script {
                            sh '''
                                git clone https://$GITHUB_USERNAME:$GITHUB_PASSWORD@github.com/dianderas/java-junit-mockito-example
                            '''
                        }
                    }
            }
        }
    }
}
```
