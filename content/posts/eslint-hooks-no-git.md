---
title: Usando ESlint e hooks no git
authors: Tailo Mateus Gonsalves
type: post
image: https://cdn-images-1.medium.com/max/1600/1*5ytPO1t6Dhz-RuN0NtBiJw.jpeg
date: 2018-03-05
excerpt: Como mandar bem nos commits
categories:
  - Front-end
  - JavaScript
  - C�digo
  - Git
---

Quantas vezes voc� mandou aquele push com erros ou totalmente fora do padr�o? Aquele commit faltando 5 minutos para acabar o hor�rio de expediente.  Isso pode acontecer com qualquer pessoa, indiferente se voc� � um iniciante ou um �senior� que s� faz coisas fant�sticas. Cabe a n�s melhorar as nossas limita��es ou falta de aten��o. O objetivo deste artigo � te ajudar nesse quesito.

## Criando o package.json

Com isso, vai criar o arquivo e aceitar todos os valores default:
```
npm init �y
```
Para saber mais:

[Working with package.json] (https://docs.npmjs.com/getting-started/using-a-package.json)

[npm-init] (https://docs.npmjs.com/cli/init)

## Instalando ESlint

� um analisador de c�digo JavaScript, criado em 2013 por Nicholas C. Zakas. Basicamente, ESlint permite que os desenvolvedores encontrem problemas e criem suas pr�prias regras e padr�es de desenvolvimento. Escrito em Node.js podemos instal�-lo via npm.

```
npm install eslint --save-dev
```
Configurando o arquivo de configura��o:
```
./node_modules/.bin/eslint --init
```
Selecione a op��o: �Use a popular style guide� e ap�s selecione o style guide da empresa que preferir.

Selecione o formato do arquivo em �JavaScript�. Ap�s esses passos e se tudo ocorreu bem, vai ser criado o arquivo .eslintrc.js. 

## Testando ESlint

Crie um arquivo chamado main.js, dentro dele coloca o c�digo:
```
a = 10
const b = 5;
b = 10
```

Ao ler o c�digo, podemos perceber que vai acontecer alguns erros. Mas vamos testar como o ESlint se comporta, para executar:

```
./node_modules/.bin/eslint *.js
```

Agora � s� corrigir os erros :D

Para saber mais: 

[Documenta��o ESlint] (https://eslint.org)

[Demo ESlint] (https://eslint.org/demo/)

[Setting up ESLint on Sublime Text 3] (https://medium.com/@junshengpierre/making-the-switch-from-jshint-to-eslint-5b6c4fa3c92a)

## Utilizando npm Scripts

No arquivo package.json, substitua esse trecho:
```
�scripts�: {
	�lint�: �./node_modules/.bin/eslint *.js�
}
```
Para rodar no terminal:
```
npm run lint
```

Para saber mais:
[Why npm Scripts? ] (https://css-tricks.com/why-npm-scripts/)

## Hooks no git

S�o scripts que fazem algo antes ou depois de alguma tarefa, por exemplo, antes de um commit fa�a algo.

Instalando o Husky:
```
npm install husky@next --save-dev
```
Para utilizar vamos adicionar o comando prepush no npm scripts:
```
�scripts�: {
	�lint�: �./node_modules/.bin/eslint *.js�,
	�prepush�: �lint�
}
```
Antes de enviarmos o push, vai executar o lint.

Para saber mais:

[Reposit�rio GitHub] (https://github.com/typicode/husky)

## Conclus�o

Espero ter ajudado. Qualquer d�vida, em todas as partes deste artigo tem refer�ncias. Tem alguma dica? Deixa nos coment�rios :D