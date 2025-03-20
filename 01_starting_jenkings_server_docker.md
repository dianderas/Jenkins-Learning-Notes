Decarga la imagen oficial:
```
docker pull jenkins/jenkins:lts
```

Corre jenking en el contenedor con los puertos correctos y persistencia de datos:
```
docker run -d --name jenkins \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

Obten clave de desbloque inicial
```
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Abre navegador ve a la ruta y pega el codigo de configuracion inicial
```
http://localhost:8080
```