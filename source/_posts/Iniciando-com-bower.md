title: Iniciando com bower
date: 2015-07-27
tags: bower
---
![](/Iniciando-com-bower/banner.jpg)
## Por que utilizar o bower?

Sabe como funciona o MAVEN para gerenciamento de dependências Java? Pois bem, o bower é uma ferramenta de gerenciamento de dependências de projetos client-side, similar ao maven. Ele pode ser adicionado em qualquer projeto, independente do back-end ser Java, Node, etc.

Imagina que você tem um projeto html/javascript e precisa ficar fazendo download manual de todos os scripts/dependências que seu sistema utiliza. E o ciclo se repete a cada nova versão de uma dependência. Isso é trabalhoso e improdutivo.

Com o bower, você pode adicionar uma nova dependência configurando um único arquivo (bower.json) ou simplesmente digitar um comando no prompt do windows.

<!--more-->

## Vamos lá...

Primeiro, certifique-se que em sua máquina esta instalado o [Nodejs](https://nodejs.org/download/).

Falaremos sobre o nodejs outro post, por hora, apenas precisamos instalá-lo, pois o bower roda "em cima" do nodejs.

### GO GO GO

Primeiramente, precisamos instalar o bower no nodejs, de forma que possa ser utilziado por qualquer projeto. Para isso abra o prompt de comando (modo administrador) e digite o seguinte comando:

``` bash
$ npm install -g bower
```

### Configurando o projeto

Pelo prompt, navegue até o diretório raiz do seu projeto. Para habilitar o bower, digite:

``` bash
$ bower init
```

Algumas opções serão exibidas pra você configurar o arquivo principal do bower (bower.json). Porém, você pode fazer isso diretamente no arquivo mais tarde. Por hora, vá precionando enter até finalizar.

Ao final, seu arquivo <i>bower.json</i> será gerado na raiz do projeto.

### Instalando sua primeira dependência

``` bash
$ bower install bootstrap --save
```

O comando acima baixou (clone) todo o repositório do [bootstrap](getbootstrap.com) que está no [github](https://github.com/twbs/bootstrap). Uma nova pasta foi criada para salvar todas as dependências baixadas chamada <i>bower_components</i>

A opção <i>--save</i> fez com que seu arquivo <i>bower.json</i> fosse configurado com essa dependência. 

Agora é só apontar o script desejado na sua index.html

{% codeblock [lang:html] index.html%}
<link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap.min.css"/>
<link rel="stylesheet" href="bower_components/bootstrap/dist/css/bootstrap-theme.min.css"/>
{% endcodeblock %}
Se você utiliza o git, svn ou cvs, não precisa fazer o commit da pasta <i>bower_components</i>. Sempre que quiser execute o comando abaixo para baixar todas as dependências já configuradas no seu arquivo bower.json

``` bash
$ bower update
```

É isso ai! Não deixe de perguntar se tiver alguma dúvida. 

Obrigado, até o próximo post.