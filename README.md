# Commandos docker
## 1\. Publicar uma porta do host para uma porta específica no contêiner NGINX:

Comando: 
```bash
docker run -p 8080:80
```

Significado: Isso mapeia a porta 8080 do host (seu computador) para a porta 80 do servidor NGINX dentro do contêiner. Portanto, o servidor NGINX no contêiner será acessível através da porta 8080 do seu computador.

## 2\. Executar um contêiner NGINX em segundo plano (modo "detached") e publicar uma porta:

Comando: 
```bash
docker run -d -p 8080:80
```

Significado: Além de fazer o mesmo mapeamento de porta que o comando anterior, a tag "-d" desacopla o terminal do processo do contêiner, permitindo que ele seja executado em segundo plano.

## 3\. Remover e parar um contêiner especificado pelo nome ou ID:

Comando:
```bash
 docker rm -f <nome ou ID do container>
```

Significado: Isso para a execução do contêiner especificado pelo nome ou ID e, em seguida, o remove. A flag "-f" é usada para forçar a parada do contêiner caso ele esteja em execução.

## 4\. Executar um contêiner NGINX em segundo plano com um nome específico:

Comando: 
```bash
 docker run -d --name <nome do container> nginx
```

Significado: Isso inicia o contêiner NGINX em segundo plano (modo detached) e atribui um nome especificado após "--name" ao contêiner.

## 5\. Executar comandos dentro de um contêiner:

Comando: 
```bash
 docker exec <container>
```

Significado: Isso permite executar comandos no contêiner especificado após o comando "docker exec".

## 6\. Executar um shell interativo dentro de um contêiner NGINX em execução:

Comando: 
```bash
  docker exec -it <container> bash
```

Significado: A opção "-it" permite a execução interativa no contêiner, o que significa que você pode interagir com o terminal. O comando "bash" é executado dentro do contêiner, fornecendo um shell bash para realizar ações dentro dele.

## 7\. Executar um contêiner NGINX em segundo plano, atribuir um nome e montar um volume:

Comando: 
```bash
  docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/html,target=/usr/share/nginx/html
```

Significado: Este comando inicia um contêiner NGINX em segundo plano (modo detached), atribui o nome "nginx" ao contêiner, publica a porta 8080 do host na porta 80 do contêiner e monta o volume do diretório atual do host chamado "html" para o diretório "/usr/share/nginx/html" no contêiner. Isso permite que o servidor NGINX no contêiner sirva o conteúdo da pasta "html" do host.

## 8\. Listar os volumes do Docker:

Comando: 
```bash
  docker volume ls
```

Significado: Esse comando lista todos os volumes criados no Docker. Os volumes são usados para persistir dados entre contêineres ou para compartilhar dados entre o host e os contêineres. O docker volume ls mostra uma lista dos nomes dos volumes disponíveis, juntamente com seu identificador único (ID) e outras informações, como driver de armazenamento utilizado e tamanho do volume. Ao listar os volumes, é possível identificar quais volumes estão sendo utilizados pelos contêineres e verificar sua utilização no sistema Docker.

## 9\. Criar um novo volume no Docker:

Comando: 
```bash
  docker volume create <volume_name>
```

Significado: Esse comando cria um novo volume no Docker com o nome especificado após o comando "docker volume create". Os volumes são usados para persistir dados entre contêineres ou para compartilhar dados entre o host e os contêineres. Ao criar um volume, você pode atribuir um nome personalizado para identificá-lo posteriormente.

## 10\. Inspecionar um volume no Docker:

Comando: 
```bash
  docker volume inspect <volume_name>
```

Significado: Esse comando exibe informações detalhadas sobre um volume específico no Docker. Basta substituir <volume_name> pelo nome do volume que deseja inspecionar. A saída do comando mostra várias propriedades do volume, incluindo o nome do volume, o driver de armazenamento utilizado, o caminho do sistema de arquivos onde o volume está localizado no host, entre outras informações úteis. A inspeção de um volume pode ser útil para entender melhor suas características e uso, bem como para depurar problemas relacionados ao armazenamento de dados em contêineres.

## 11\. Remover volumes não utilizados no Docker:

Comando: 
```bash
  docker volume prune
```

Significado: Este comando remove todos os volumes do Docker que não estão sendo usados por nenhum contêiner. Os volumes são criados para persistir dados entre contêineres, mas às vezes, quando você para ou remove contêineres, os volumes associados a eles podem ficar ociosos e consumir espaço em disco. O comando docker volume prune ajuda a liberar espaço no sistema, excluindo os volumes que não estão sendo usados. Antes de executar esse comando, é importante garantir que você não precisa mais dos dados armazenados nos volumes a serem removidos, pois a ação é irreversível e os dados associados serão perdidos.

## 12\. Baixar uma imagem Docker do Docker Hub:

Comando: 
```bash
  docker pull <nome_da_imagem>
```

Significado: Esse comando permite baixar uma imagem Docker do Docker Hub ou de um registro de container semelhante. A imagem será baixada para o seu sistema local e poderá ser usada posteriormente para criar contêineres com base nessa imagem. Substitua <nome_da_imagem> pelo nome da imagem que você deseja baixar. Por exemplo, se você quiser baixar a imagem oficial do Nginx, o comando seria docker pull nginx. O Docker Hub é uma plataforma online que contém um vasto repositório de imagens Docker públicas e compartilhadas pela comunidade, e o comando docker pull é a maneira de obter essas imagens em sua máquina local.

## 13\. Listar as imagens Docker disponíveis no sistema:

Comando:
```bash
   docker images
```

Significado: Esse comando exibe uma lista de todas as imagens Docker disponíveis no sistema local. As imagens são como "modelos" ou "templates" que são usados para criar contêineres. Cada imagem pode ser baseada em outra imagem ou conter um sistema operacional e aplicativos específicos. A saída do comando mostrará informações sobre cada imagem, incluindo o nome da imagem, a tag (versão), o ID da imagem, o tamanho da imagem e o repositório de origem (caso a imagem tenha sido baixada do Docker Hub ou de outro registro de imagens). A listagem de imagens ajuda a identificar as imagens disponíveis localmente e é útil para saber quais imagens você pode usar para criar contêineres.

## 14\. Remover uma imagem Docker do sistema local:

Comando: 
```bash
   docker rmi <nome_da_imagem>
```

Significado: Esse comando permite remover uma imagem Docker do sistema local. Substitua <nome_da_imagem> pelo nome da imagem que você deseja remover. Certifique-se de que não há contêineres em execução que dependam dessa imagem antes de removê-la, pois a ação é irreversível e a imagem será excluída permanentemente do sistema. Se houver contêineres usando essa imagem, primeiro você deve removê-los com docker rm e, em seguida, poderá usar docker rmi para excluir a imagem. A remoção de imagens não utilizadas ajuda a liberar espaço em disco no sistema local.

## 15\. Criar uma nova imagem Docker usando um Dockerfile:

Comando: 
```bash
   docker build -t manelito/nginx-with-vim:latest .
```

Significado: Esse comando cria uma nova imagem Docker com base nas instruções definidas em um arquivo chamado Dockerfile, localizado no diretório atual ("."). O Dockerfile é um arquivo de texto que contém todas as configurações necessárias para criar uma imagem personalizada.

-t manelito/nginx-with-vim:latest: Especifica o nome da nova imagem que será criada. Neste caso, a imagem será nomeada como "manelito/nginx-with-vim" com a tag "latest". A tag "latest" é uma convenção comum para indicar a versão mais recente da imagem.

## 16\. Remover todos os containers

Comando:

```bash
   docker rm $(docker ps -a -q) -f
```

O comando `docker ps` lista todos os containers ativos no momento. A opção `-a` também inclui os containers inativos (parados).
A opção `-q ou --quiet ` é usada para retornar apenas os IDs numéricos dos containers, tornando a saída mais limpa.

`$(docker ps -a -q):`
O uso do $(...) é chamado de substituição de comando no shell. Ele executa o comando entre parênteses e retorna o resultado como argumentos para o comando externo.
Neste caso, `$(docker ps -a -q)` é substituído pelos IDs dos containers ativos e inativos.

`docker rm $(docker ps -a -q) -f:`
O comando `docker rm` é usado para remover container(s).
`$(docker ps -a -q)` é substituído pelos IDs dos containers ativos e inativos, e isso resulta em um conjunto de argumentos para o comando docker rm.
A flag -f é usada para forçar a remoção do(s) container(s), mesmo que estejam em execução (caso contrário, o Docker exige que os containers estejam parados antes de serem removidos).

O comando docker logout é usado para fazer logout de um registro de container.

## 17\. Logout de um registro de container

Comando:

```bash
   docker logout [REGISTRY_URL]
```
`docker logout [REGISTRY_URL]`
Onde `[REGISTRY_URL]` é o URL do registro de container a partir do qual você deseja fazer logout. Se você estiver logado em um registro específico, executar este comando fará com que você saia e remova as credenciais de autenticação associadas a esse registro em seu sistema. Isso significa que você não poderá mais acessar imagens privadas desse registro até fazer login novamente.

Se não for especificado um URL de registro, o comando docker logout irá deslogar do registro padrão, que é o Docker Hub.

## 18\. Login de um registro de container

Comando:

```bash
   docker login [REGISTRY_URL]
```

Onde `[REGISTRY_URL]` é o URL do registro de container onde você deseja fazer login. Se você não especificar um URL de registro, o comando docker login fará login no registro padrão, que é o Docker Hub.

Após executar o comando, você será solicitado a fornecer suas credenciais de autenticação, geralmente um nome de usuário e senha ou um token de acesso, dependendo do registro. Uma vez autenticado com sucesso, suas credenciais serão armazenadas localmente no sistema e você poderá acessar imagens privadas desse registro através do Docker CLI.

## 19\. Upload da imagen para um registro de container

Comando:

```bash
   docker push [REGISTRY_URL]/[NOME_DA_IMAGEM]:[TAG]
```

`[REGISTRY_URL]` é o URL do registro de container para o qual você deseja enviar a imagem. Se você estiver usando o Docker Hub, o URL padrão é docker.io.
`[NOME_DA_IMAGEM]` é o nome da imagem que você deseja enviar.
`[TAG]` é a tag da imagem que você deseja enviar. A tag geralmente representa a versão da imagem, como "latest", "v1.0", etc.
Antes de usar o comando docker push, você deve ter a imagem localmente em seu sistema, o que significa que você deve ter construído a imagem usando o comando docker build ou baixado uma imagem pré-existente usando o comando docker pull. Além disso, você deve estar autenticado no registro de container para o qual deseja enviar a imagem, o que pode ser feito usando o comando docker login.

Ao executar o comando docker push, a imagem é enviada para o registro de container especificado, tornando-a disponível para outros usuários baixarem e usarem em seus próprios contêineres. Certifique-se de ter permissão para enviar imagens para o registro, pois alguns registros podem exigir autenticação e autorização adequadas.

## 20\. Baixar uma imagen de um registro de container

Comando:

```bash
   docker pull [REGISTRY_URL]/[NOME_DA_IMAGEM]:[TAG]
```

`[REGISTRY_URL]` é o URL do registro de container de onde você deseja baixar a imagem. Se você estiver usando o Docker Hub, o URL padrão é docker.io.
`[NOME_DA_IMAGEM]` é o nome da imagem que você deseja baixar.
`[TAG]` é a tag da imagem que você deseja baixar. A tag geralmente representa a versão da imagem, como "latest", "v1.0", etc. Se não for especificada uma tag, o Docker irá baixar a versão "latest" por padrão.
O comando docker pull irá buscar a imagem especificada no registro de container e baixá-la para o seu sistema local. Após o download, a imagem estará disponível em seu sistema e você poderá usá-la para criar novos contêineres com base nessa imagem.

Antes de usar o comando docker pull, verifique se você está autenticado no registro de container, caso a imagem seja privada e exija autenticação. Você pode fazer login usando o comando docker login. Caso contrário, você só poderá baixar imagens públicas disponíveis no registro.