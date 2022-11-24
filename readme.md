# Baixando e criando um container baseado na imagem nginx para hospedar site
> docker container run -d -p 8080:80 --name <nome> nginx:alpine
>> nginx:alpine tem o comando ping 
>> inicia um container novo
>> -d executa em background
>> se usar o P (maiusculo) randomiza a porta automaticamente (nao precisa passar)

> docker container run -d --name <nome> --network <nomedarede> nginx:alpine
>> cria um container em uma rede especifica Bridge

> docker container start <id ou nome> 
>> inicia um container ja existente (nao cria outro)

> docker container rm -f ${docker container ls -a -q}
>> remove todos os container ls -a -q que estao na listagem ao mesmo tempo
>> -q lista apenas nos IDs para fazer comandos juntos

> docker container logs <nome>
>> lista os logs do container

>> docker container logs -f <nome>
>> acompanha no terminao os logs "ao vivo"

> docker container top <nome>
>> lista os processos que o container esta rodando

> docker container stats <nome>
>> lista os status de todos os containers (monitoramento)

> docker container inspect <nome>
>> dados totais do container

> docker container inspect --format='{{<json $.NetworkSettings>}}' <nome>
>> dados do container usando um template de saida padrao go

> docker container cp nginx1:/usr/share/nginx/html/index.html .
>> copio um arquivo de dentro do container para minha maquina

> docker container run -d --name nginx1 -v ${pwd}/index.html:/usr/share/nginx/html/index.html -p 80:80 nginx
>> copiando o arquivo index.html para criar um container com ele 