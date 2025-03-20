- New Item -> Ingresar Nombre y selecionar Pipeline.
- En pipeline definition: 
```
pipeline {
    agent any
    
    stages {
        stage("Saludo 1") {
            steps {
                echo "Hola desde saludo 1"
            }
        }
        stage("Saludo 2") {
            steps {
                echo "Hola desde saludo 2, paso 1"
                echo "Hola desde saludo 2, paso 2"
            }
        }
    }
}
```

Agregando variables de entorno
```
pipeline {
    agent any
    environment {
        INSTAGRAM_ENZO="@enrael"
    }
    
    stages {
        stage("Saludo 1") {
            steps {
                echo "Hola desde saludo 1"
            }
        }
        stage("Saludo 2") {
            steps {
                echo "Hola desde saludo 2, paso 1"
                echo "Hola desde saludo 2, paso 2"
            }
        }
        stage("Imprimir Variable de entorno") {
            steps {
                echo "${env.INSTAGRAM_ENZO}"
                echo "${INSTAGRAM_ENZO}"
                echo "$INSTAGRAM_ENZO"
            }
        }
    }
}
```

Puedes entrar al servidor del servidor (agente) a traves de la funcion shell
```
stage("Imprimir Variable de entorno") {
    steps {
        echo "${env.INSTAGRAM_ENZO}"
        echo "${INSTAGRAM_ENZO}"
        echo "$INSTAGRAM_ENZO"
        echo "============================="
        sh "echo 'hola-mundo'"
        sh "echo ${env.INSTAGRAM_ENZO}"
        sh "echo ${INSTAGRAM_ENZO}"
        sh "echo $INSTAGRAM_ENZO"
    }
}
```
De igual manera se pueden imprimir variables del System
```
stage("Imprimir Variables de entorno definida en System") {
    steps {
        echo "${env.INSTAGRAM}"
        echo "${INSTAGRAM}"
        echo "$INSTAGRAM"
        
        sh "echo ${env.INSTAGRAM}"
        sh "echo ${INSTAGRAM}"
        sh "echo $INSTAGRAM"
    }
}
```