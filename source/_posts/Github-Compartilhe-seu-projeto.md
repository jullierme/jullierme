title: 'Github: Compartilhe seu projeto'
date: 2015-08-14
tags: ['git', 'github']
---
![](/Github-Compartilhe-seu-projeto/banner.png)
Neste mini-tutorial, vamos aprender a colocar nosso projeto no github. Também vamos aprender os principais comandos git.

<!--more-->
###Pra começar...

Antes de tudo, você precisa criar um repositório no github, na sua conta. É bem simples. Importante: NÃO CRIE O ARQUIVO README. Vamos criar este arquivo pela linha de comando.

Pelo prompt, navegue até a raiz do seu projeto e digite:
```
$ git init
```
Agora vamos criar o arquivo <b>.gitignore</b> s

```bash
$ touch .gitignore
```

O arquivo <b>.gitignore</b> serve para informarmos as pastas/arquivos do nosso projeto que não serão 'comitados'.

Por exemplo: se você tem o bower no seu projeto, não vai querer comitar a pasta <b>bower_components</b> nem a pasta <b>node_modules</b>. Para configurar essas pastas, abra o arquivo e informe:

```txt
node_modules/
bower_components/
```
Agora sim vamos criar o arquivo <b>README.md</b>. Digite o comando:

```bash
$ touch README.md
```

Agora, informe ao git quem é você. Ele precisa dessas informações para fazer o <b>commit</b>

```bash
$ git config --global user.name "Seu Nome"
$ git config --global user.email “seuemail@gmail.com”
```

Para verificar as pastas observadas pelo git, digite:

```bash
$ git status
```

Os arquivos de verde estão 'na fila' para serem 'comitados'. Os de vermelho foram alterados mas não foram 'adicionados na fila'.

Como estamos configurando o git agora, todos os arquivos precisam ser adicionados na fila para serem comitados. Para isso, digite:

```bash
$ git add .
```

Agora vamos informar ao git da nossa máquina, qual é nosso repositório remoto.

```bash
$ git remote add origin https://github.com/jullierme/angularjs.git
```

Ok, agora vamos fazer nosso primeiro commit.

```bash
$ git commit -m “comentário do seu comit”
```

Lembrando que, o comando <b>commit</b> envia os arquivos para um no repositório local (INDEX) que está na nossa máquina. Estes ainda não foram para o servidor remoto. Podemos fazer diversos 'commits' antes de enviar tudo para o repositório remoto (HEAD)

Para enviar todos os nossos commits para o servidor remoto, digite:

```bash
$ git push -u origin master
```

E se eu quiser atualizar meu repositório local com as informações do repositório remoto?

```bash
$ git pull
```

Esse comando simplesmente 'puxa' todos os arquivos alterados (commits de outros desenvolvedores) para seu projeto.

Durante o desenvolvimento, você basicamente irá utilizar os comandos:

```bash
$ git add *
```
O <b>*</b> diz que o git deve adicionar todos os arquivos alterados 'na fila' para o próximo commit

Continuando...

```bash
$ git status
```

O comando <b>git status</b> sempre vai te mostrar se tem algo para adicionar na fila para ser 'comitado' e se não tiver, vai te mostrar quantos commits precisam ser enviados para o repositório remoto (head).

e por ai vai...

```bash
$ git commit -m “comentário do seu comit”
$ git push -u origin master
$ git pull
```

Um abraço, até a próxima