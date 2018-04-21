---
title:  "Alterando sql-mode no MySQL"
description: Como mudar o sql-mode que vem padrão no MySQL
date: 2017-06-27 16:24:48
category: MySQL
comments: true
---

Recentemente eu fiz um <span class="code">SELECT</span> e me deparei com esse erro:

<div class="hljs">
	Expression #1 of SELECT list is not in GROUP BY clause and contains nonaggregated column 'support_desk.mod_users_groups.group_id' which is not functionally dependent on columns in GROUP BY clause; this is incompatible with sql_mode=only_full_group_by
</div>

No erro que foi me retornado, é dito no final que o comando que eu tentei rodar é incompativel com o <span class="code">sql_mode=only_full_group_by</span>. 

Eu utilizo a versão 5.7 do MySQL e descobri que a partir dessa versão o modo SQL padrão inclue esses modos: ONLY_FULL_GROUP_BY, STRICT_TRANS_TABLES, NO_ZERO_IN_DATE, NO_ZERO_DATE, ERROR_FOR_DIVISION_BY_ZERO, NO_AUTO_CREATE_USER, e NO_ENGINE_SUBSTITUTION.

O modo [only_full_group_by](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_only_full_group_by), se estiver habilitado, rejeita todas consultas da lista de seleção (os campos a serem selecionados), condição <span class="code"> HAVING </span> ou <span class="code">ORDER BY</span> que se refeferem a colunas não agregadas que __não estiverem__ dentro da clausula <span class="code">GROUP BY</span>.

# Para resolver isso

## Maneira mais fácil e rápida:

Altere o <span class="code">sql_mode</span> via query, basta rodar o código abaixo com os <span class="code">sql_mode</span> que você deseja habilitar:
<script src="https://gist.github.com/LeandroLS/52326c05d7b021df451f1524c50dd02d.js"></script>

O ruim de alterar o <span class="code">sql_mode</span> dessa maneira é que da proxima vez que você reiniciar o MySQL você vai ter que rodar o mesmo comando novamente.

## Maneira mais difícil, porem definitiva:

Para carregar o <span class="code">sql_mode</span> definido por você ao iniciar o MySQL temos que alterar o arquivo my.cnf (Sistemas operacionas Unix) ou my.ini (Windows). No Ubuntu esse arquivo costuma ficar em etc/mysql/my.cnf, porem o diretório onde ele fica pode variar. 

Edite o arquivo my.cnf setando o sql-mode:

![my.cnf editado]({{ site.baseurl }}../assets/img/sql-mode.png)

Tem que colocar o __[mysqld]__ para funcionar. 

Feito esse alteração, toda vez que o MySQL iniciar ele ira carregar os modos que você setou no my.cnf.

