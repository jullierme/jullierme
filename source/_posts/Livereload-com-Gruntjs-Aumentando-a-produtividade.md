title: Livereload com Gruntjs - Aumentando a produtividade
date: 2015-08-04
tags: ['gruntjs', 'livereload']
---
![](/Livereload-com-Gruntjs-Aumentando-a-produtividade/banner.jpg)

## Como isso funciona?

A idéia é que a medida que você vai alterando seu código (js, html, css etc), essas alterações possam ser refletidas imediatamente no browser.

### De que preciso?

Você precisa do [Gruntjs](http://gruntjs.com/) configurado no seu projeto e de apenas um plugin. O [grunt-contrib-watch](https://github.com/gruntjs/grunt-contrib-watch).

### Instalação


Pelo prompt de comando, navegue até a raiz do seu projeto, onde se encontra o arquivo <b>Gruntfile.js</b>
``` bash
npm install grunt-contrib-watch --save-dev
```

Esse é o plugin vai fazer o livereload funcionar :)

Aqui, eu utilizo outro plugin do grunt, indispensável por sinal. O [matchdep](https://www.npmjs.com/package/matchdep). Ele simplesmente importa todos os plugins do grunt de uma vez. Para instalar, basta fazer:

``` bash
npm install matchdep --save-dev
```

Configurando nosso arquivo Gruntfile.js
<!--more-->
{% codeblock [lang:javascript] Gruntfile.js%}
module.exports = function(grunt) {
    //Carrega todos os plugins do Grunt declarados no arquivo package.json de uma vez
    require('matchdep').filterDev('grunt-*').forEach(grunt.loadNpmTasks);

    // Configura o Grunt
    grunt.initConfig({
        // Tarefa watch
        watch: {
            options: {
                livereload: true
            },
            js: {
                files: ['**/*.js'],
            },
            html: {
                files: ['**/*.html']
            },
            css: {
                files: ['**/*.css'],
            },
        },
    });

    //registra uma tarefa
    grunt.registerTask( "livereload", [ "watch" ]);
};
{% endcodeblock %}

Agora, basta você adicionar esse código no index do seu projeto

{% codeblock [lang:html] index.html%}
<script src="//localhost:35729/livereload.js"></script>
{% endcodeblock %}

## Resumindo

Da linha 9 a 11, temos a ativação do livereload. Da linha 12 a 20, temos a configuração da escuta, ou seja, toda vez que um arquivo .js, .html ou .css for alterado, será feito o recarregamento da página no browser.

## Vamos aos testes

Inicie o servidor de aplicação e depois digite o comando:

``` bash
grunt livereload
```

Lembrando que <b>livereload</b> é o nome da tarefa que registramos na linha 25

Abra sua aplicação pelo browser, altere algum arquivo e salve. Veja que a página foi recarregada com as novas alterações.

## Dica

Eu divido a tela em duas. Do lado esquerdo deixo o webstorm e do lado direito o browser com a aplicação carregada. Dessa forma, vou fazendo a codificação do meu sistema e verificando imediatamente o visual da página. É bem melhor que um "mode design" de alguma ferramenta rad por exemplo.

## \o/

É isso ai. Espero que te ajude como me ajudou :) Dúvidas? Deixe seu comentário.

Obrigado
