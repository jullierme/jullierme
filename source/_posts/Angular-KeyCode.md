title: Angular KeyCode
date: 2015-10-31 12:16:28
tags: Angularjs KeyboardEvent
---
![](/Angular-KeyCode/banner.jpg)

Números mágicos nunca mais. Utilize este serviço em AngularJS para verificar o código das teclas do teclado.

<!--more-->
[![](https://img.shields.io/bower/v/angular-keycode.svg)](http://bower.io/search/?q=angular-keycode)
[![](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/jullierme/angular-keycode?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


Números mágicos nunca mais \o/
===================

O que é Angular Keycode? É um serviço de códigos de teclado.

Quando você precisar capturar um evento de teclado e verificar qual tecla foi precionada, ao invés de colocar o código das teclas, utilize este serviço.

Por exemplo:


```js
if(codigoCapturado === KeyCode.ENTER){
```

Um arquivo bem pequeno. Menos que 2kb minificado :)

Instalação
-------------

### bower

```shell
# Para instalar a última versão
bower install angular-keycode


# Para instalar a última versão e atualizar o arquivo bower.json
bower install angular-keycode --save
```

Registrar
-------------
```js
angular.module('myApp',['angular-keycode']);
```

Importar no seu html
-------------
```html
<script src="bower_components/angular-keycode/angular-keyboard.min.js"></script>
```

Com usar?
-------------
```js
(function(){
	'use strict';

	MyService.$inject = ['KeyCode'];

	function MyService(KeyCode){
		var vm = this;
		vm.onKeydown = onKeydown;

		//errado
		function onKeydown($event){
			var code = $event.which || $event.keyCode;

			if(code === 13){//magic number detectado
				...faça algo
			}
		}

		//correto
		function onKeydown($event){
			var code = $event.which || $event.keyCode;

			if(code === KeyCode.ENTER){//muito melhor agora :)
				...faça algo
			}
		}

	}
})();

```

Alguns exemplos
------------

```js
KeyCode.BACKSPACE
KeyCode.TAB
KeyCode.ENTER

KeyCode.A
KeyCode.B
KeyCode.C

KeyCode.NUMPAD_8
KeyCode.NUMPAD_9

KeyCode.F1
KeyCode.F2
KeyCode.F3

```

[Veja mais aqui...](https://github.com/jullierme/angular-keycode)


LICENCE
-------------

MIT (Livre pra vc fazer o que quiser)

Um abraço, até a próxima
