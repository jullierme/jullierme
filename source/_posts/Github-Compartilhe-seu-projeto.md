title: 'Github: Compartilhe seu projeto'
date: 2015-08-14
tags: ['git', 'github']
---
Neste mini-tutorial, vamos aprender a colocar nosso projeto no github. Também vamos aprender os principais comandos git.


###Pra começar...

Antes de tudo, você precisa criar um repositório no github, na sua conta. É bem simples. Importante: NÃO CRIE O ARQUIVO README. Vamos criar este arquivo pela linha de comando.

Pelo prompt, navegue até a raiz do seu projeto e digite para habilitar o git:
```
git init
```
Agora vamos criar o arquivo <b>.gitignore</b> pela linha de comando: (Se preferir, crie manualmente)

```bash
touch .gitignore
```

<!--more-->

O arquivo <b>.gitignore</b> serve para informarmos as pastas/arquivos do nosso projeto que não serão 'comitados'.

Por exemplo: se você tem o bower no seu projeto, não vai querer comitar a pasta <b>bower_components</b> nem a pasta <b>node_modules</b>. Para configurar essas pastas, abra o arquivo e informe:

```txt
node_modules/
bower_components/
```
Agora sim vamos criar o arquivo <b>README.md</b> (Se preferir, crie manualmente). Digite o comando:

```bash
touch README.md
```

Agora, informe ao git quem é você. Ele precisa dessas informações para fazer o <b>commit</b>

```bash
git config --global user.name "Seu Nome"
git config --global user.email “seuemail@gmail.com”
```

Para verificar as pastas observadas pelo git, digite:

```bash
git status
```

Os arquivos de verde estão 'na fila' para serem 'comitados'. Os de vermelho foram alterados mas não foram 'adicionados na fila'.

Como estamos configurando o git agora, todos os arquivos precisam ser adicionados na fila para serem comitados. Para isso, digite:

```bash
git add .
```

Agora vamos informar ao git da nossa máquina, qual é nosso repositório remoto.

```bash
git remote add origin https://github.com/usuario/nome-projeto.git
```

Ok, agora vamos fazer nosso primeiro commit.

```bash
git commit -m “comentário do seu comit”
```

Lembrando que, o comando <b>commit</b> envia os arquivos para um no repositório local (INDEX) que está na nossa máquina. Estes ainda não foram para o servidor remoto. Podemos fazer diversos 'commits' antes de enviar tudo para o repositório remoto (HEAD)

Para enviar todos os nossos commits para o servidor remoto, digite:

```bash
git push -u origin master
```

Se houve alterações no projeto, seu push será rejeitado. É necessário atualizar o projeto local antes de enviar as novas modificações.

```bash
git fetch origin
```

Atualizar o repositório local antes de enviar é uma boa prática a ser seguida para quem usa svn ou cvs e é obrigatória no git.

Imagine o seguinte cenário. Você chega no trabalho e manhã e a primeira coisa que precisa fazer é baixar as atualizações do projeto feitas pela equipe.

Para isso, basta fazer um <b>pull</b>

```bash
git pull origin master
```

Esse comando simplesmente 'puxa' todos os arquivos alterados (commits de outros desenvolvedores) para seu projeto.

Durante o desenvolvimento, você basicamente irá utilizar os comandos:

```bash
git add .
```
O <b>.</b> diz que o git deve adicionar todos os arquivos alterados 'na fila' para o próximo commit

Continuando...

```bash
git status
```

O comando <b>git status</b> sempre vai te mostrar se tem algo para adicionar na fila para ser 'comitado' e se não tiver, vai te mostrar quantos commits precisam ser enviados para o repositório remoto (head).

e por ai vai...

```bash
git commit -m “comentário do seu comit”
git push -u origin master
git pull origin master
```

Clonar um repositório existente
-------------

Se o repositório já existe, você vai precisar baixar o projeto completamente antes de começar a trabalhar nele...

Pra isso, será necessário fazer um <b>git clone</b>.

Primeiro, navegue até a pasta raiz onde vai ficar seu projeto

Ex: workspace

Dentro da pasta, digite:

```bash
git clone git://github.com/usuario/nome-projeto.git
```

Neste caso, será criada uma pasta chamada seuProjeto dentro de workspace com todos os arquivos do projeto.


Registrar no bower
-------------

Registre seu projeto para que outras pessoas possam instalar

```bash
bower register nome-projeto git://github.com/usuario/nome-projeto.git
```

Para verificar informações do registro, digite:

```bash
bower info nome-projeto
```

Agora qualquer pessoa pode instalar seu projeto pelo comando:

```bash
bower install nome-projeto
```

Criar uma tag
-------------

Mas qual versão será instalada quando alguém digitar o comando acima? Você precisa criar uma tag sempre que precisar gerar uma versão do seu projeto.

####Ex: 1.0.0, 1.0.1 etc...

Quando seu projeto for instalado pelo comando <b>bower install</b>, sempre virá a última versão do projeto.

Para criar uma tag, digite:

```bash
git tag -a v1.0.0 -m "primeira versao"
```

Depois é só fazer um <b>push</b> da tag para que ela seja criada remotamente:

```bash
git push origin v1.0.0
```

###Regra para criação da tag

Um v minúsculo na frente e sempre três dígitos

Ex: v1.0.8, v2.0.0


Remover uma tag
-------------

Se você precisar remover uma tag, é bem simples:

```bash
git tag -d v1.1.2
git push origin :refs/tags/v1.1.2
```

Um abraço, até a próxima
-------------