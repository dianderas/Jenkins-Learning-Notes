- Variables dinamicas tambien conocidos como parametros
- Se pueden hacen dinamicas las variables desde el mismo pipeline
  - Debemos tener en cuenta el contexto por ejemplo en 'sh' si hay un error en las comillas va a ser un error de linea de comando,
    pero si ocurre un error con una funcion de groovy va ser un error de este. Aun que echo y sh sean funciones de groovy
    para el caso de sh cualquier error dentro de las comillas es un error de linea de comandos. Entonces este compatamiento va
    a variar depende de la funcion que se este usando.
  - Tener en cuenta que para los temas de programacion, todo lo que tenga que ver con logica, asignacion de variables, condicionales
    funciones y ciclos, debe estar dentro de la funcion 'script'
```
pipeline {
    agent any
    environment {
        INSTAGRAM_ENZO="@enrael"
    }
    
    stages {
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
        stage("cambio de valor") {
            steps {
                script {
                    INSTAGRAM_ENZO="@enzoisrael31"
                    echo "${INSTAGRAM_ENZO}"
                }
            }
        }
    }
}
```
- Como escribir un parametro antes de que se ejecute el pipeline
```
pipeline {
    agent any
    parameters {
        string(name: 'LASTNAME', description: 'Enter lastanme')
        text(name: 'BIOGRAFIA', description: 'Enter bio')
        booleanParam(name: 'BOOLEANO', description: 'Boolean parameter')
        choice(name: "CITIES", choices:['Cali', 'Palmira', 'Bogota', 'Buga'], description: 'Enter city')
        password(name: "PASSWORD", description: 'Enter password')
    }
    environment {
        INSTAGRAM_ENZO="@enrael"
    }
    
    stage("imprimir parametro") {
        steps {
            echo "${params.LASTNAME}"
            echo "${LASTNAME}"
        }
    }
}
...
```
- Ahora en la interfaz grafica dira "Build with Parameter" y al presionar se visualizar el campo LASTNAME para ingresar.

