- Cuando un job depende de otro job
- Cuando se necesita modularizar el proyecto, segmentar el trabajo. por ejemplo un pipeline demasiado largo.

Primer pipeline
```
pipeline {
    agent any
    parameters {
        string(name: 'NOMBRE_PIPELINE')
        string(name: 'ID_JOB')
    }
    
    stages {
        stage("Hola mundo") {
            steps {
                script {
                    sh "echo 'hola mundo'"
                }
            }
        }
        stage("Print params") {
            steps {
                script {
                    sh "echo $NOMBRE_PIPELINE"
                    sh "echo $ID_JOB"
                }
            }
        }
    }
}
```
Job que llama al primer job, se requiere el nombre de maquina de dicho job
```
pipeline {
    agent any
    
    stages {
        stage("Trigger job") {
            steps {
                build job: 'Quinto-Pipeline', parameters: [
                    string(name: 'NOMBRE_PIPELINE', value: 'Sexto Pipeline'),
                    string(name: 'ID_JOB', value: '10000010000010')
                ]
            }
        }
    }
}
```
pasando como parametros variables de entorno para el primer job:
```
pipeline {
    agent any
    
    stages {
        stage("Trigger job") {
            steps {
                build job: 'Quinto-Pipeline', parameters: [
                    string(name: 'NOMBRE_PIPELINE', value: "$JOB_NAME"),
                    string(name: 'ID_JOB', value: "$BUILD_ID")
                ]
            }
        }
    }
}
```