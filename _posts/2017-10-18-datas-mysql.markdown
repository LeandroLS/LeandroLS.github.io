---
title:  "Trabalhando com datas no MySQL"
date:   2017-10-18 17:00:00
comments: true
---
Quando eu comecei a trabalhar na área de desenvolvimento, eu tive bastante dificuldade pra recuperar e inserir datas no banco de dados, depois de um tempo consegui pegar uma experiência e já me sinto seguro pra postar algo sobre.

Suponha que eu tenha uma variável seguinte variável:
<span class="code">$data = '18/10/2017'</span>
Observe que a variável está com o formato 'dd/mm/yyyy'.

Para inserir essa data no banco, eu não posso fazer isso:
<span class="code">INSERT INTO tabela (data) VALUES ('18/10/2017')</span>
Eu não posso fazer isso pois o MySQL recupera e exibe valores de DATA no formato 'yyyy-mm-dd' e no código acima eu estou tentando inserir no formato 'dd/mm/yyyy', caso tivesse no formato 'yyyy-mm-dd' iria funcionar. 

Pra converter inserir da maneira correta, teria que ser feito isso:
<span class="code">INSERT INTO tabela (data) VALUES (STR_TO_DATE('18/10/2017'),'%d/%m/%Y')</span>
A função <span class="code">STR_TO_DATE</span> pega uma string (primeiro parâmetro) e um formato (segundo parâmetro) e retorna uma data que o MySQL entende, no caso a data será transformada em: '2017-10-18'. 
Se o formato informado pra função não for válido com a string, será retornado <span class="code"> null </span>, cuidado com isso. 



