# Referência Git

Comandos Básicos de Git para Repositórios online do Github

## Sumário

* [Guia Rápido](#guia-rápido)
	* [Versionando os arquivos localmente](#versionando-com-o-git)
	* [Subindo para o Github](#subindo-o-repositório-local-para-o-github)
	* [Trazendo um repositório da nuvem](#trazendo-clonando-um-repositório-da-nuvem)
	* [Sincronizando um repositório local com o da nuvem](#sincronizando-um-repositório-local-com-o-da-nuvem)
	* [Trabalhando com branches](#trabalhando-com-branches)
	    * [Para criar uma nova branch](#para-criar-uma-nova-branch)
	    * [Para listar as branches existentes](#listar-as-branches-existentes-a-branch-que-estiver-marcada-é-a-branch-atual)
	    * [Para mudar de branch](#para-mudar-de-branch)
	    * [Para juntar os códigos das branches](#para-juntar-os-códigos-das-branches)
* [Conceitos](#conceitos)
	* [Versionamento com o Git](#versionamento-com-o-git)
	* [Subindo o repositório local para a nuvem](#subindo-para-o-github)
	* [Branches e Merge](#branches-e-merge)

---
## Guia Rápido

### Versionando com o Git

1. Para iniciar o versionamento Git em um projeto:

	```sh 
	git init
	```
	
2. Adicionar os arquivos para o commit:

	```sh 
	git add .
	```

    Ou

	```sh 
	git add "Nome do arquivo"
	```
    
3. Salvar as alterações criando o commit:

	```sh 
	git commit -m "Descrição do commit"
	```

### Subindo o repositório local para o Github

1. Primeiro vincule um repositório remoto

	`git remote add <apelido do repositório> <link do repositório>`

	Exemplo:
	
	```sh 
	git remote add origin https://github.com/Thiago-Nascimento/referencia-git
	```
2. Com o repositório vinculado, podemos subir os commits para a nuvem

	`git push <apelido do repositorio remoto> <branch atual>`

	Exemplo:
	
	```sh 
	git push origin develop
	```

### Trazendo (clonando) um repositório da nuvem

* Se você não possui o repositório na sua máquina, para trazer um repositório do Github, execute:

	`git clone <link do repositório>`

	Exemplo:
	
	```sh 
	git clone https://github.com/Thiago-Nascimento/referencia-git
	```

### Sincronizando um repositório local com o da nuvem

* Se você já possui o repositório na sua máquina e na nuvem, e quer trazer as alterações que foram feitas no repositório remoto, execute:

	`git pull <nome do repositório> <nome da branch>`

	Exemplo:
	
	```sh 
	git pull origin main
	```

### Trabalhando com branches

* #### Para criar uma nova branch:

	`git branch <nome da nova branch>`

	Exemplo:
	
	```sh 
	git branch develop
	```

* #### Listar as branches existentes, a branch que estiver marcada é a branch atual

	```sh 
	git branch -a
	```

* #### Para mudar de branch:

	`git checkout <nome da branch de destino>`

	Exemplo:
	
	```sh 
	git checkout develop
	```

* #### Para juntar os códigos das branches

	Supondo que estamos na branch "pagina-login", e queremos adicionar o código dessa branch na branch "develop"

	1. Precisamos mudar para a branch onde ficarão as alterações (Nesse caso "develop"):

        ```sh 
        git checkout develop
        ```

	2. Agora trazemos os commits da branch "pagina-login" para a branch atual (develop):

		`git merge <branch de onde queremos trazer o código>`

        Nesse caso:
	
        ```sh 
        git merge pagina-login
        ```
	
## Conceitos

### Versionamento com o Git 

* Para iniciar o versionamento em um projeto utilizando o Git, dentro da pasta do projeto execute o seguinte comando:

	```sh 
	git init
	```

* Para adicionar os arquivos e para salvar o commit, é necessário adiciona-los na fila.
    * Se quiser adicionar todos os arquivos modificados na fila, execute:

        ```sh 
        git add .
        ```

    * Se quiser adicionar arquivos específicos, execute:

        `git add <nome do arquivo>`

        Por exemplo:

        ```sh 
        git add "index.html"
        ```

* Para salvar as alterações feitas, depois de adicionar os arquivos na fila, é necessário fazer o commit, para isso execute:

	```sh 
	git commit -m "Descrição do commit"
	```

### Subindo para o Github

* Podemos sincronizar um projeto local do Git com um repositório remoto no Github, para fazer isso precisamos vincular o projeto local com esse repositório na nuvem.

   1. Para isso executamos:

        `git remote add <apelido do repositorio remoto> <link do repositório>`

        Por exemplo:

        ```sh 
        git remote add origin https://github.com/Thiago-Nascimento/referencia-git
        ```

        Esse comando vincula um repositório remoto (< link do repositório >), utilizando um "apelido" (< apelido do repositório>).

    2. Depois de vincular o repositório remoto, já podemos subir os commits para ele, para fazer isso usamos o comando:

        `git push <apelido do repositorio remoto> <branch atual>`

        Por exemplo:

        ```sh 
        git push origin main
        ```

        Esse comando sobe os commits feitos na branch (< branch atual>) para o repositorio remoto (< apelido do repositorio remoto>)

    Com esses passos, o repositório no github já vai conter os commits realizados.

* Se deseja trazer uma cópia de um repositório do github, para a sua máquina, é necessário clonar o repositório, para isso execute o comando:

    `git clone <link do repositorio>`

    Por exemplo:

    ```sh 
    git clone https://github.com/Thiago-Nascimento/referencia-git
    ```

    Esse comando vai fazer uma cópia do repositório, inclusive já pronta e linkada para os futuros commits e pushes.

* Agora para trazer as mudanças que estão no repositório remoto, e ainda não estão no repositório local, precisar fazer o "pull" desses commits. Para isso executamos:

    `git pull <nome do repositorio> <nome da branch>`

    Por exemplo:

    ```sh 
    git pull origin main
    ```

    Se o repositório local já estiver na branch que deseja trazer do repositório remoto podemos omitir o nome do repositorio e o nome da branch, ficando simplesmente:

    ```sh 
    git pull
    ```


### Branches e Merge

* #### O que são branches?

    Branches são ramificações do código principal, onde conseguimos trabalhar em separado, geralmente criamos uma branch para desenvolver uma funcionalidade e ao mesmo tempo não alterar o código principal.

    É uma prática muito utilizada entre os desenvolvedores - principalmente para ter ambientes de desenvolvimento, homologação, testes separados - e não colocar o código novo direto em produção, evitando que códigos não revisados sejam incrementados ao código principal.

* #### Como trabalhar com as branches?

    Quando criamos um repositório, por padrão, ele possui uma única branch, que é a branch principal, geralmente tem o nome `main`.

    Para criarmos uma branch de desenvolvimento, podemos seguir os seguintes passos:

    1.  ##### Criando a branch de desenvolvimento

        Para criar uma branch de desenvolvimento chamada develop, executamos:

        `git branch <nome da branch>`

        Nesse caso:

        ```sh 
        git branch develop
        ```

    2.  ##### Para utilizarmos a branch "develop"

        Para utilizarmos essa branch criada temos que sair da branch "main" e ir para a "develop", para isso, executamos:

        `git checkout <branch de destino>`

        Nesse caso:

        ```sh 
        git checkout develop
        ``` 

    3. Depois de feitos os commits nessa branch, para subirmos ela para o repositório no Github, executamos:

        ```sh 
        git push origin develop
        ```

* #### Juntando as branches

    Quando queremos juntar o conteúdo das branches, temos que fazer o `merge`.

    Por exemplo, depois de uma revisão e sabendo que o código está correto podemos levar o código da branch de desenvolvimento (`develop`), para a branch principal (`main`), para isso...

    1.  ##### Primeiro mudamos para a branch principal

        ```sh 
        git checkout main
        ```

    2.  ##### E juntamos o código da "develop" com a "main"

        ```sh 
        git merge develop
        ```
