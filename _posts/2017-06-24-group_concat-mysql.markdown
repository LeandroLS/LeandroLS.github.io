---
title:  "Utilizando GROUP_CONCAT() no MySQL"
date: 2017-06-24 14:57:38
category: MySQL
comments: true
---


A função <span class="code">GROUP_CONCAT()</span> serve pra trazer todos os resultados de uma coluna de uma tabela em uma linha só. 
Exemplo, eu tenho a tabela contas:

![Descrição tabela contas]({{ site.baseurl }}../assets/img/GROUP_CONCATnoMySQL.png)

<span class="code">SELECT</span> normal na tabela contas:

<script src="https://gist.github.com/LeandroLS/8cb33777006dcc9e385d55d0a2ddb8bc.js"></script>

<span class="code">SELECT</span> com <span class="code">GROUP_CONCAT</span>:

<script src="https://gist.github.com/LeandroLS/b5bb85be231955b4236fdc44051f3a76.js"></script>

# Como isso poder ser útil ?
Se você olhar novamente a descricação da minha tabela <span class="code">contas</span>, verá que ela recebe um id da tabela <span class="code">classificacao</span>, a tabela <span class="code">classificacao</span> guarda as classificações das contas. Exemplo: 

<script src="https://gist.github.com/LeandroLS/8991666b299e18f3719a9bd45738bef2.js"></script>

Imagina que você tenha que trazer todas as classificações __sem repetir__ elas, e também trazer __todas__ as contas que carregam as respectivas classificações em um <span class="code">SELECT</span>. Pra resolver esse problema, temos que usar o <span class="code">GROUP_CONCAT()</span>. Sem o <span class="code">GROUP_CONCAT()</span> isso não seria possível. Fariamos assim: 

<script src="https://gist.github.com/LeandroLS/1d5cfdd71843380ae630b1802bb499f0.js"></script>



