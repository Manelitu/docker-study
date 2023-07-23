1\. Publicar uma porta do host para uma porta específica no contêiner NGINX:

Comando: docker run -p 8080:80

Significado: Isso mapeia a porta 8080 do host (seu computador) para a porta 80 do servidor NGINX dentro do contêiner. Portanto, o servidor NGINX no contêiner será acessível através da porta 8080 do seu computador.

2\. Executar um contêiner NGINX em segundo plano (modo "detached") e publicar uma porta:

Comando: docker run -d -p 8080:80

Significado: Além de fazer o mesmo mapeamento de porta que o comando anterior, a tag "-d" desacopla o terminal do processo do contêiner, permitindo que ele seja executado em segundo plano.

3\. Remover e parar um contêiner especificado pelo nome ou ID:

Comando: docker rm -f <nome ou ID do container>

Significado: Isso para a execução do contêiner especificado pelo nome ou ID e, em seguida, o remove. A flag "-f" é usada para forçar a parada do contêiner caso ele esteja em execução.

4\. Executar um contêiner NGINX em segundo plano com um nome específico:

Comando: docker run -d --name <nome que você quer dar ao container> nginx

Significado: Isso inicia o contêiner NGINX em segundo plano (modo detached) e atribui um nome especificado após "--name" ao contêiner.

5\. Executar comandos dentro de um contêiner:

Comando: docker exec <container>

Significado: Isso permite executar comandos no contêiner especificado após o comando "docker exec".

6\. Executar um shell interativo dentro de um contêiner NGINX em execução:

Comando: docker exec -it <container> bash

Significado: A opção "-it" permite a execução interativa no contêiner, o que significa que você pode interagir com o terminal. O comando "bash" é executado dentro do contêiner, fornecendo um shell bash para realizar ações dentro dele.

7\. Executar um contêiner NGINX em segundo plano, atribuir um nome e montar um volume:

Comando: docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/html,target=/usr/share/nginx/html

Significado: Este comando inicia um contêiner NGINX em segundo plano (modo detached), atribui o nome "nginx" ao contêiner, publica a porta 8080 do host na porta 80 do contêiner e monta o volume do diretório atual do host chamado "html" para o diretório "/usr/share/nginx/html" no contêiner. Isso permite que o servidor NGINX no contêiner sirva o conteúdo da pasta "html" do host.

8\. Listar os volumes do Docker:

Comando: docker volume ls

Significado: Esse comando lista todos os volumes criados no Docker. Os volumes são usados para persistir dados entre contêineres ou para compartilhar dados entre o host e os contêineres. O docker volume ls mostra uma lista dos nomes dos volumes disponíveis, juntamente com seu identificador único (ID) e outras informações, como driver de armazenamento utilizado e tamanho do volume. Ao listar os volumes, é possível identificar quais volumes estão sendo utilizados pelos contêineres e verificar sua utilização no sistema Docker.

9\. Criar um novo volume no Docker:

Comando: docker volume create <volume_name>

Significado: Esse comando cria um novo volume no Docker com o nome especificado após o comando "docker volume create". Os volumes são usados para persistir dados entre contêineres ou para compartilhar dados entre o host e os contêineres. Ao criar um volume, você pode atribuir um nome personalizado para identificá-lo posteriormente.

10\. Inspecionar um volume no Docker:

Comando: docker volume inspect <volume_name>

Significado: Esse comando exibe informações detalhadas sobre um volume específico no Docker. Basta substituir <volume_name> pelo nome do volume que deseja inspecionar. A saída do comando mostra várias propriedades do volume, incluindo o nome do volume, o driver de armazenamento utilizado, o caminho do sistema de arquivos onde o volume está localizado no host, entre outras informações úteis. A inspeção de um volume pode ser útil para entender melhor suas características e uso, bem como para depurar problemas relacionados ao armazenamento de dados em contêineres.

11\. Remover volumes não utilizados no Docker:

Comando: docker volume prune

Significado: Este comando remove todos os volumes do Docker que não estão sendo usados por nenhum contêiner. Os volumes são criados para persistir dados entre contêineres, mas às vezes, quando você para ou remove contêineres, os volumes associados a eles podem ficar ociosos e consumir espaço em disco. O comando docker volume prune ajuda a liberar espaço no sistema, excluindo os volumes que não estão sendo usados. Antes de executar esse comando, é importante garantir que você não precisa mais dos dados armazenados nos volumes a serem removidos, pois a ação é irreversível e os dados associados serão perdidos.

12\. Baixar uma imagem Docker do Docker Hub:

Comando: docker pull <nome_da_imagem>

Significado: Esse comando permite baixar uma imagem Docker do Docker Hub ou de um registro de container semelhante. A imagem será baixada para o seu sistema local e poderá ser usada posteriormente para criar contêineres com base nessa imagem. Substitua <nome_da_imagem> pelo nome da imagem que você deseja baixar. Por exemplo, se você quiser baixar a imagem oficial do Nginx, o comando seria docker pull nginx. O Docker Hub é uma plataforma online que contém um vasto repositório de imagens Docker públicas e compartilhadas pela comunidade, e o comando docker pull é a maneira de obter essas imagens em sua máquina local.

13\. Listar as imagens Docker disponíveis no sistema:

Comando: docker images

Significado: Esse comando exibe uma lista de todas as imagens Docker disponíveis no sistema local. As imagens são como "modelos" ou "templates" que são usados para criar contêineres. Cada imagem pode ser baseada em outra imagem ou conter um sistema operacional e aplicativos específicos. A saída do comando mostrará informações sobre cada imagem, incluindo o nome da imagem, a tag (versão), o ID da imagem, o tamanho da imagem e o repositório de origem (caso a imagem tenha sido baixada do Docker Hub ou de outro registro de imagens). A listagem de imagens ajuda a identificar as imagens disponíveis localmente e é útil para saber quais imagens você pode usar para criar contêineres.

14\. Remover uma imagem Docker do sistema local:

Comando: docker rmi <nome_da_imagem>

Significado: Esse comando permite remover uma imagem Docker do sistema local. Substitua <nome_da_imagem> pelo nome da imagem que você deseja remover. Certifique-se de que não há contêineres em execução que dependam dessa imagem antes de removê-la, pois a ação é irreversível e a imagem será excluída permanentemente do sistema. Se houver contêineres usando essa imagem, primeiro você deve removê-los com docker rm e, em seguida, poderá usar docker rmi para excluir a imagem. A remoção de imagens não utilizadas ajuda a liberar espaço em disco no sistema local.

15\. Criar uma nova imagem Docker usando um Dockerfile:

Comando: docker build -t manelito/nginx-with-vim:latest .

Significado: Esse comando cria uma nova imagem Docker com base nas instruções definidas em um arquivo chamado Dockerfile, localizado no diretório atual ("."). O Dockerfile é um arquivo de texto que contém todas as configurações necessárias para criar uma imagem personalizada.

-t manelito/nginx-with-vim:latest: Especifica o nome da nova imagem que será criada. Neste caso, a imagem será nomeada como "manelito/nginx-with-vim" com a tag "latest". A tag "latest" é uma convenção comum para indicar a versão mais recente da imagem.

.: Especifica o contexto de build para o Docker. O Docker irá procurar o arquivo Dockerfile no diretório atual para construir a imagem.

Após a execução do comando, o Docker analisará o Dockerfile presente no diretório atual, executará cada instrução e criará uma nova imagem com o nome e tag especificados. Essa imagem pode ser usada posteriormente para criar contêineres com as configurações definidas no Dockerfile.