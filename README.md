# Comandos básicos Git e Github

## Versionando os arquivos localmente.

Para criar iniciar o versionamento em um projeto utilizando o Git, dentro da pasta do projeto execute o comando:
`git init`

Para adicionar os arquivos para salvar o commit, é necessário adiciona-los a fila, para isso execute o comando:
`git add <nome do arquivo>`

Ou se quiser adicionar todos os arquivos modificados à lista, execute:
`git add .`

Para salvar as alterações feitas, depois de adicionar os arquivos a fila, é necessário fazer o commit, para isso execute:
`git commit -m "Descrição do commit"`

## Subindo o repositório local para a nuvem (Github).
Podemos sincronizar um projeto local do Git com um repositório remoto no Github, para fazer isso precisamos vincular o projeto local com esse repositório na nuvem.

Para isso executamos: 
`git remote add <apelido do repositorio remoto> <link do repositório>`

Por exemplo: 
`git remote add origin https://github.com/Thiago-Nascimento/referencia-git`

Esse comando vincula um repositório remoto (< link do repositório >), utilizando um "apelido" (< apelido do repositório>).

Depois de vincular o repositório remoto, já podemos subir os commits para ele, para fazer isso usamos o comando:
`git push <apelido do repositorio remoto> <branch atual>`

Por exemplo: 
`git push origin main`

Esse comando sobe os commits feitos na branch (< branch atual>) para o repositorio remoto (< apelido do repositorio remoto>)

Com esses passos, o repositório no github já vai conter os commits realizados.

Caso queiramos trazer uma cópia do repositório do github, para a nossa máquina, teremos que clonar o repositório, para isso execute o comando:
`git clone <link do repositorio>`

Por exemplo:
`git clone https://github.com/Thiago-Nascimento/referencia-git`
Esse comando vai trazer uma cópia do repositório, inclusive já pronta para os futuros commits e pushes.

## Trabalhando com branches
#### O que são branches?
Branches são ramificações do código principal, onde conseguimos trabalhar em separado, geralmente criamos uma branch para desenvolver uma funcionalidade e ao mesmo tempo não alterar o código principal.

É uma prática muito utilizada entre os desenvolvedores, principalmente para termos um ambiente de homologação, de teste, e não colocarmos o código novo direto em produção, evitando que códigos não revisados sejam incrementados ao código principal.

#### Como trabalhar com as branches?

Quando criamos um repositório, por padrão, ele possui uma única branch, que é a branch principal, geralmente tem o nome `main`.
Para criarmos uma branch de homologação, podemos seguir os seguintes passos:

1. ##### Criando a branch de homologação
	Para criar uma branch de homologação chamada develop, executamos:
	`git branch <nome da branch>`
	Nesse caso:
	`git branch develop`
2. ##### Para utilizarmos a branch "develop"
	Para utilizarmos essa branch criada temos que sair da branch "main" e ir para a "develop", para isso, executamos:
	`git checkout <branch de destino>`
	Nesse caso:
	`git checkout develop`

Depois de feitos os commits nessa branch, para subirmos ela para o repositório no Github, executamos:
`git push origin develop`

#### Juntando as branches
Quando queremos juntar o conteúdo das branches, temos que fazer o `merge`.
Por exemplo, depois de uma revisão e sabendo que o código está correto podemos levar o código da branch de homologação (`develop`), para a branch principal (`main`), para isso...
1. ##### Primeiro mudamos para a branch principal
	`git checkout main`
2. ##### E juntamos o código da "develop" com a "main" 
	`git merge develop`