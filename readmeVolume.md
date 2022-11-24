

# Container é Efêmero
    > tem curta duração, ele nasce para morrer. 

# Container é Imutável
    > ele morre e perde tudo que esta dentro dele. 

# Como persistir Dados??

# Volume = guarda as infos do container. 
>> o conteudo do container é imutavel, quando mata ele nao salva nada dentro dele. 

>> -v ou --mount
>> --mount é mais completo passa mais informações

> -v mysql-db:/var/lib/mysql:rw 
>> mysql-db - Volume Nomeado no docker host
>> /var/lib/mysql - diretorio dentro do container
>> RW ou RO (Read Write ou Read Only)

> --mount 'type=volume, source=mysql-db,target=/var/lib/mysql, readwrite'
>> sintaxe mais descritiva

> Volumes = volume nomeado.
>> gerenciado pelo docker host

> Bind Volume - para persistir os dados quando recria o container
> -v $(pwd)/mysql:/var/lib/mysql
>> $(pwd) - diretorio local 
> --mount 'type=volume,source=$(pwd)/mysql,target=/var/lib/mysql,readwrite'
>> depende de uma estrutura de diretório no docker host (nossa maquina)
>> mapeamos o conteudo da nossa maquina para dentro do container

# nfsserver compartilha os dados para persistir os dados

# temos que ter cuidado com as IMAGENS que puxamos 
> toda imagem puxada tem na descrição onde fica o VOLUME da imagem
>> Ex. container mysql => volume é [/var/lib/mysql]

> docker container run -d -e MYSQL_ROOT_PASSWORD=senha mysql
>> quando lista container mysql ou outro que necessita de volume ele cria automaticamente

> docker volume ls
>> lista os volumes

> OBS apos remover os containers o volume nao é removido, precisa remover se nao estiver usando. 

> docker volume create mysql-db
>> usar o volume para todas as instancias q precisam persistir os dados

> docker container run -d --name mysql-db -v mysql-db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=senha mysql
>> utilizando o nome do volume criado acima

> docker volume prune
>> remove os volumes que nao estao sendo utilizado


