---
title:  "Recuperando no PHP form input's que tenham o mesmo nome"
date:   2017-07-05 20:48:36
category: PHP
---

Imaginem o seguinte formulário:

<script src="https://gist.github.com/LeandroLS/373299ad663cfacabd849b91ed0d5bc3.js"></script>

Observe que os inputs dentro desse <span class="code">form</span> o atributo "name" tem o mesmo valor.

Após fazer a requisição, no teste.php eu exibo as informações que vieram do <span class="code">form</span> e o retorno é esse:

<span class="code">Array ( [nome] => nome2 ) 1</span>

Veja que apesar de eu ter dois <span class="code">input</span>'s no formulário, só foi me enviado um. Isso acontece porque quando um <span class="code">form</span> é submetido e este tem vários <span class="code">input</span>'s com o valor do atributo "name" iguais, só o último é considerado.

### Para resolver isso

Para que todos <span class="code">input</span>'s com o mesmo valor do atributo "name" sejam entregues após requisição, basta adicionar colchetes ao lado do valor do atributdo "name". Exemplo:

<script src="https://gist.github.com/LeandroLS/d1aaaa4d366aad7c73d5da6150277d39.js"></script>

Após alterar o formulário, se eu fizer a requisição novamente, o resultado vai ser esse:

<span class="code">Array ( [nome] => Array ( [0] => nome1 [1] => nome2 ) )</span>

Recebi todos os <span class="code">input</span>'s, mesmo com o mesmo atributo "name" em todos eles. :D



