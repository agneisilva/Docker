
docker network prune
docker container prune
docker image prune
 
docker-compose -f docker-compose.yml -f docker-compose.override.yml --no-ansi build
 
docker-compose -f docker-compose.yml -f docker-compose.override.yml --no-ansi up -d --no-build --force-recreate --remove-orphans
 
docker-compose -f docker-compose.yml -f docker-compose.override.yml --no-ansi up -d --build --force-recreate --remove-orphans
 
docker-compose -f docker-compose.yml -f docker-compose.override.yml down
 
docker container ls -a
docker container ls -aq
<!-- Parar todos container que estiverem rodando no servidor -->
docker container stop $(docker container ls -aq)
 
<!-- Remover todos container que estiverem rodando no servidor -->
docker container rm $(docker container ls -aq)
 
docker container stop $(docker ps --filter "status=running" --format {{.ID}})
docker container rm $(docker ps --filter "status=running" --format {{.ID}})
 
docker ps --filter "status=running" --format {{.ID}};{{.Names}}
 
<!-- #acessa um container -->
docker exec -it 96ff9b2568c1 bash
docker exec -it 96ff9b2568c1 /bin/bash
docker exec -it 96ff9b2568c1 /bin/sh
 
<!-- ##copia dados de dentro de um container para o host -->
docker cp 634529bf6427:/identityService_log.txt .
 
<!-- ##install curl -->
apt update && apt upgrade && install curl
 
<!-- ##install ping -->
apt-get install iputils-ping
 
docker build . -t noah-app
 
ng build --prod --aot --build-optimizer 
 
docker run noah-app -port 8010:80 -it bash -env production=false -env IdentityServerURI=http://localhost:8000 -env ApiURI=http:localhost:8001 -env FrontendURI=http://localhost:8010
 
 docker-compose -f docker-compose.nobuild.yml -f docker-compose.prod.yml pull
 
docker-compose -f docker-compose.nobuild.yml -f docker-compose.prod.yml up -d --no-build --force-recreate --remove-orphans
 
netstat -a -b -n -o > port.txt

<!-- Não rodar esse comando em Produção (apaga os dados dos banco de dados(Volumes)) -->
docker system prune --volumes


docker run -it -d -p 2884:1883 -p 9001:9001 eclipse-mosquitto