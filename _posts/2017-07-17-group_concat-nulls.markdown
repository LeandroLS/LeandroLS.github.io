---
title:  "Recuperando valores nullos com GROUP_CONCAT()"
date:   2017-07-17 19:16:22
category: MySQL
---

Já fiz um [post]({{ site.baseurl }}{{ post.url | remove_first: '/' }}group_concat-mysql/) no blog sobre a função <span class="code">GROUP_CONCAT()</span> do MySQL, vou voltar a falar mais um pouco sobre ela. Recentemente precisei usar essa função novamente e observei que ela não traz valores nullos, mas no caso em que eu estava eu precisava que ela trouxesse esses valores. Existe uma maneira fácil de resolver isso e vou explicar mais abaixo. 

Para o exemplo irei usar uma tabela chamada <span class="code">frutas</span>:

<script src="https://gist.github.com/LeandroLS/2c6fd57c35c2ede05c553b87418b0677.js"></script>

Observe que eu adicionei algumas frutas com valores nullos.

Se eu fizer um select de todos os campos da tabela o resultado é esse:

![Descrição tabela frutas]({{ site.baseurl }}assets/img/group_concat-nulls.png)

Observe que há duas frutas que vieram sem nome, está nullo. 

Se eu selecionar a coluna <span class="code">nome_frutas</span> com <span class="code">GROUP_CONCAT()</span> os valores nullos não serão trazidos e o resultado é esse:

![Resultado GROUP_CONCAT() tabela frutas]({{ site.baseurl }}assets/img/group_concat-nulls-2.png)

### Para trazer os valores nullos

Para trazer os valores nullos com <span class="code">GROUP_CONCAT()</span> é preciso utilizar a função de controle de fluxo <span class="code">[IFNULL](https://dev.mysql.com/doc/refman/5.7/en/control-flow-functions.html#function_ifnull)</span> junto com <span class="code">GROUP_CONCAT()</span>. Exemplo:

<script src="https://gist.github.com/LeandroLS/54f4cc8aa411b48eac45e4eb4c7ed29d.js"></script> 

Resultado:

![Resultado GROUP_CONCAT() com IFNULL]({{ site.baseurl }}assets/img/group_concat-nulls-3.png)

Veja que as linhas onde havia valores nullos foram trazidas.

A função <span class="code">[IFNULL](https://dev.mysql.com/doc/refman/5.7/en/control-flow-functions.html#function_ifnull)</span> aceita dois parâmetros/expressões, como pode ser visto na imagem. Se o primeiro parâmetro for nullo, o __segundo__ parâmetro é retornado, caso contrário, o __primeiro__ parâmetro é retornado. 

Existem outras maneiras de resolver esse "problema" descrito nesse post, mas achei essa solução mais fácil e decidir publicar aqui. :D






