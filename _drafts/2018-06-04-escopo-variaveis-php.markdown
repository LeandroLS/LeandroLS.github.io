---
title:  "Escopo de variável e a palavra chave global em PHP"
date: 2018-06-04 10:03:48
category: PHP
comments: true
---

Após definir uma variável em PHP, o escopo dela é o escopo do seu contexto atual, onde ela foi definida.

```php
<?php
$a = "sou a variável $a";
include 'teste.php';
?>
```
Nesse exemplo acima a variável `$a` estará disponível no script atual e no arquivo `teste.php`.

Porem, quando uma variável é declarada dentro de uma função definida pelo usuário, ela ganha outro escopo, que é o escopo local da função. A variável só é acessível apenas dentro daquela função. Exemplo:

```php
<?php 
$a = "sou a variável $a"; /* Escopo global, está acessível em todo script */

function teste(){
    /* referencia uma variável dentro do escopo da função, não está referenciando $a do escopo global */
    echo $a; 
}

teste();
?>
```

O script acima não produz resultado nenhum. Porque a função `teste()` chama a variável `$a` que não foi declarada dentro do escopo da variável. 

