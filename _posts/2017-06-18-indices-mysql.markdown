---
title:  "Índices no MySQL"
date:   2017-06-18 22:07:20
description: Explicando um pouco sobre índices no MySQL
category: MySQL
---


# Índices no MySQL

Imagine que você tenha que estudar sobre as funções do MySQL em um determinado livro que aborda o assunto, porem nesse livro não há um sumário pra você saber em quais páginas se encontra a explicações sobre funções do MySQL, nesse caso você terá que folhear o livro até chegar nas páginas do assunto que você quer estudar. Se houvesse um sumário nesse livro, você demoraria menos tempo pra achar o que queria. A mesma coisa acontece numa consulta SQL. Para entender melhor: 

Vamos supor que eu tenha uma tabela chamada <span class="code">`livros`</span>

![Descrição tabela livros]({{ site.baseurl }}assets/img/indices-mysql.png)

Nessa tabela eu tenho 20 mil registros:


<script src="https://gist.github.com/LeandroLS/32cfb80a2df3619eb0b6aeab9f35ff73.js"></script>

Com base nessa tabela, eu quero saber quantos livros são lançados no mesmo dia:

<script src="https://gist.github.com/LeandroLS/b906cc03e04df309ce9bc252a540e460.js"></script>

Essa query acima irá demorar cerca de 2 minutos pra ser concluida. É uma eternidade. 

Essa demora acontece porque essa tabela tem um volume muito grande de registros. Para cada registro da query principal, ele irá executar a subquery, por isso ele __demora quase dois minutos__ pra trazer o resultado.

É aí que entra os <span class="code">índices</span> pra resolver esse problema.

Para criar um índice em uma tabela:

<span class="code">
	CREATE index nome_do_index ON nome_tabela(nome_coluna);
</span>

No meu caso quero criar um índice por data de lançamento, então ficará assim:

<script src="https://gist.github.com/LeandroLS/6ebdbe84ccf21521932686871c0c4c82.js"></script>

Após a adição do índice, ao executar a query para saber quantos livros são lançados no mesmo dia, a query __demora menos de um segundo__ a ser executada. Tudo isso graças a adição do índice.

Após a adição do índice na tabela, uma maneira grosseira de entender isso é imaginar que estivesse adicionando um "sumário" na tabela. Assim o banco consegue ir direto aos registros solicitados pela query muito mais rápido. 



