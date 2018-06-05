---
title:  "Escopo de variável e a palavra chave global em PHP"
date: 2018-06-04 10:03:48
category: PHP
comments: true
---

O escopo de uma variável definida em PHP, é o escopo do seu contexto atual, onde ela foi definida.

```php
<?php
$a = 1;
include 'teste2.php';
?>
```
Nesse exemplo acima a variável `$a` estará disponível no script atual e no arquivo `teste2.php`

