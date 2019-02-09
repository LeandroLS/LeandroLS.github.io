---
title:  "Escopo de variável e a palavra chave global em PHP"
date: 2018-06-05 10:03:48
category: PHP
comments: true
description: "Explicando sobre escopo de variaveis em PHP"
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

O script acima não produz resultado nenhum. Porque a função `teste()` chama a variável `$a`, como nenhuma variável `$a` foi declarada dentro do escopo da função, não vai produzir nada.

### A palavra-chave `global` 

Exemplo utilizando a palavra chave `global`:

```php
<?php

/* Variáveis em escopo global */
$a = 1; 
$b = 2;

function Soma()
{
    global $a, $b;

    $b = $a + $b;
}

Soma();
echo $b;
?>
```   
O script acima irá imprimir 3. Observem que definimos as variáveis `$a` e `$b` como globais dentro da função. Com isso, a função passa a fazer referência as variáveis `$a` e `$b` que estão no escopo global.

O mesmo script acima poderia ser feito de outra maneira, exemplo: 

```php
<?php
$a = 1;
$b = 2;

function Soma()
{
    $GLOBALS['b'] = $GLOBALS['a'] + $GLOBALS['b'];
}

Soma();
echo $b;
?>
```

O array `$GLOBALS` é um array especial definido pelo PHP.