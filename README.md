# Devops Guide

### Docker Documentation

etc:

Ex.1;

### Docker Commands

etc:

Ex.1;


#### --- ###

# DevOps

### Docker Documentation


```
docker login -u           floryos    -p          123456789

docker login --username   floryos    --password  123456789

docker login -u           floryos    --password  123456789

```

```
docker run    --name   my-postgres   -e POSTGRES_USER=postgres    -e POSTGRES_PASSWORD=123456789   -e POSTGRES_DB=postgres  -p 9999:5432    -d postgres
```


### ===============  kendi jarlarımızı image olarak docker'a verme  ======================

```
docker build    --build-arg   JAR_FILE=target/devops-01-1.0.1.jar      --tag floryos/devops-01:v001   .
```
docker build    --build-arg   JAR_FILE=target/devops-01-1.0.1.jar      --tag floryos/devops-01:latest   .
```
docker build    --build-arg   JAR_FILE=target/devops-01-1.0.2.jar      --tag floryos/devops-01:v002   .
```
docker build    --build-arg   JAR_FILE=target/devops-01-1.0.2.jar      --tag floryos/devops-01:latest   .
```
docker build    --build-arg   JAR_FILE=target/devops-01-1.0.3.jar      --tag floryos/devops-01:v003   .
```
docker build    --build-arg   JAR_FILE=target/devops-01-1.0.3.jar      --tag floryos/devops-01:latest   .
```



### ===============  kendi imagelerimizi container olarak çalıştırma ======================


```
docker           run       -it     -d           --name my-app1         -p 8081:8080                      floryos/devops-01:v001
```

```
docker container run       -it     -d           --name my-app1         -p 8081:8080                      floryos/devops-01:v001
```

```
docker  run       -it     -d           --name my-app2         -p 8082:8080                      floryos/devops-01:v002
```

```
docker  run       -it     -d           --name my-app3         -p 8083:8080                      floryos/devops-01:latest
```

```
docker  run       -it     -d           --name my-app4         -p 8084:8080                      floryos/devops-01:v003
```


http://localhost:8081 </br>
http://localhost:8082 </br>
http://localhost:8083 </br>
http://localhost:8084 </br>


### ===============  kendi imagelerimizi dockerhub'a gönderme  ======================
```
docker push floryos/devops-01:v001
docker push floryos/devops-01:latest
```

### ===============  kendi imagelerimizi dockerhub'dan çekme  ======================
```
docker pull floryos/devops-01:v001
docker pull floryos/devops-01:latest
```



### ============== network ==============
### networkleri listele

```
docker network ls
```

### yeni bir network oluştur
```
docker network create my-network
```

### network tipini değiştirmek istiyorsanız --driver parametresi
```
docker network create --driver bridge my-network
```


### network bilgisi ve onu kullanan containerlar
```
docker network inspect my-network
```


### networke container ekleme
```
docker network connect my-network my-app1
docker network connect my-network my-app2
docker network connect my-network my-app3
```

### network bilgisi ve onu kullanan containerlar
```
docker network inspect my-network
```

### networke container çıkarma
```
docker network disconnect my-app2
```


### network bilgisi ve onu kullanan containerlar
```
docker network inspect my-network
```

### networkü silme
```
docker network rm my-network
```


### ============== volume ==============
```
docker volume ls
```
### Yeni bir volume oluşturmak
```
docker volume create my-volume
```

```
docker volume ls
```

```
docker volume inspect my-volume
```

### bir volume silmek
```
docker volume rm my-volume
```

### kullanılmayan tüm volumeleri silmek
```
docker volume prune
```

### ============= docker-compose ===================
```
docker compose -f docker-compose.yml up

docker compose -f docker-compose.yaml up
```

```
docker ps
```

```
docker container ls
```

```
docker-compose logs mongo
docker-compose logs -f  mongo
```


```
docker compose -f docker-compose.yml down

docker compose -f docker-compose.yaml down
```