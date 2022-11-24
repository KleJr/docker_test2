# Redes

> docker network ls
>> lista as redes disponiveis 

> docker network inspect <?bridge>
>> inspeciona a rede que quero ver

> docker network create <nomedaredenova> 
>> cria uma nova rede SubRede para os containers.

> docker container exec -it <nomedocontainer> sh 
>> executa o sh do container para uso no terminal
>> ifconfig, ping, 

>> OBS dentro de containers nao é possivel enxergar outra rede

> docker container run -d --name <nome> --network <nomedarede> nginx:alpine
>> cria um container em uma rede especifica Bridge

> Brige (nao é a ponte) - é o padrao quando cria container
>> Padrão - NAT - Comunicação interna entre os containers
>> Melhor prática é criar uma nova rede virtual para cada app.
>>> my_web = mysql, apache, php
>>> my_api = flask, nodejs

> Host (esta que faz a ponte) 
>> Mesmo IP da maquina
>> Não precisa publicar portas (-p ou P)
>> Não inicia outro container com a mesma porta
>> Nao funciona em modo swarm

> None
>> container fica isolado nesta rede

> docker network create <nomedanovarede> --gateway 172.20.0.1 --subnet 172.20.0.0/24
>> cria uma rede customizada com o ip que definimos 

> docker network rm <nomedarede>

> docker network prune

> docker container exec -it h_ambiente ping h_ambiente2
>> executa o ping direto na linha de comando
