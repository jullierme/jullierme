title: 'Contextualizar o componente de Toast do Angular Material'
date: 2015-12-31
tags: AngularJS, Angular Material, Toast
---

Essa dica é pra quem deseja alterar a cor de fundo do componente de Toast, pois, por padrão, ele possui apenas a cor preta.

![](https://lh3.googleusercontent.com/-CDp6kaf5ckg/VoQYaMXKJ1I/AAAAAAABT00/dGVlb-V4yB8/s0/registro+salvo+com+sucesso.png "registro salvo com sucesso.png")

A ideia seria contextualizar o componente para exibir mensagens por tipo.

Ex:

 - Verde: Mensagens de operações realizadas com sucesso
 - Vermelho: Erros de validação
 - Laranja: Alertas
 - Azul: Informações gerais

<!--more-->

Vamos lá...
-------------

O grande truque é alterar o css para um tema específico:

```css
--css do theme green
md-toast.md-green-theme .md-toast-content {
  background-color: #62c462;--verde
}

--css do theme red
md-toast.md-red-theme .md-toast-content{
  background-color: #ee5f5b;--vermelho
}

--css do theme orange
md-toast.md-orange-theme .md-toast-content{
  background-color: #fb921a;--laranja
}

--css do theme blue
md-toast.md-blue-theme .md-toast-content{
  background-color: #0088cc;--azul
}
```

----------

Agora é só acionar o toast, definindo o 'theme' da mensagem.

```js
$mdToast.show(
    $mdToast.simple()
        .theme('green')//<-- Segunda parte do truque
        .content('Registro salvo com sucesso');
);
```
Resultado:

![](https://lh3.googleusercontent.com/-uCNoqDvQBm8/VoQYjjVT5SI/AAAAAAABT1A/0zqJP6QxYoM/s0/registro+salvo+com+sucesso+verde.png "registro salvo com sucesso verde.png")


```js
$mdToast.show(
	$mdToast.simple()
		.theme('orange')
		.content('Atenção, preencha os campos obrigatórios');
);
```
Resultado:

![](https://lh3.googleusercontent.com/-U3cIfhGVEBw/VoQYrND6zQI/AAAAAAABT1M/CUWfnuU3YDE/s0/alerta.png "alerta.png")


```js
$mdToast.show(
	$mdToast.simple()
		.theme('red')
		.content('Erro a tentar executar a operação XYZ');
);
```
Resultado:

![](https://lh3.googleusercontent.com/-JCyTvGS6Wkc/VoQYwO79nrI/AAAAAAABT1Y/eP7EAtVNREs/s0/erro.png "erro.png")


```js
$mdToast.show(
	$mdToast.simple()
		.theme('blue')
		.content('Você possui uma nova mensagem');
);
```
Resultado:

![](https://lh3.googleusercontent.com/-Q9mn8iqfBOo/VoQY3bKjShI/AAAAAAABT1w/mbr_NtCaV6k/s0/informacao.png "informacao.png")



Lembrando que sua app pode estar utilizando qualquer outro tema. A propriedade 'theme' do toasd irá afetar apenas a mensagem naquele exato momento.

Componente de toast: https://material.angularjs.org/1.0.1/demo/toast

Versão do angular material utilizada: **v1.0.1**


É isso ai, um abraço e até a próxima.