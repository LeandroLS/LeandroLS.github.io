---
title: "Objeto arguments em JavaScript "
date: 2018-11-02
category: Javascript
comments: true
thumbnail: false
---

Tenho estudado bastante JavaScript nas últimas semanas, durante esses estudos, descobri um objeto interessante que eu não havia o conhecido antes. Esse objeto é o `arguments`.  
A descrição do objeto segundo a Rede de Desenvolvedores da Mozilla (MDN) é essa:  
> O objeto `arguments` é uma variável local disponível dentro de todas as funções. Você pode referenciar os argumentos de uma função dentro da função usando o objeto `arguments`. Esse objeto contém um registro para cada argumento fornecido para a função, com o índice do primeiro registro começando em 0.  

Vamos supor que temos a seguinte função:  
```javascript
function testeArguments(){
    console.log(arguments.length);
}
```  
Observe que na declaração da função não foi passado nenhum argumento.  
Uma vez que a função está declarada, vamos tentar invoca-la passando argumentos, assim:  
```javascript
testeArguments(arg1,arg2,arg3);
```  
O resultado que irá aparecer no console será `3`.  
Antes de descobrir esse objeto, eu também não sabia que eu podia invocar funções passando o tanto de argumento que eu quiser, mesmo que na declaração dessa função eu não tenha específicado que aquela função espera argumentos. Isso é uma coisa que eu não encontrei nas outras linguagens de programação, ainda não consegui concluir se isso é bom ou ruim dentro do JavaScript.

