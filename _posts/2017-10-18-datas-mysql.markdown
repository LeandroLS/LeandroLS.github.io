---
title:  "Trabalhando com datas no MySQL"
date:   2017-10-18 17:00:00
comments: true
---
Quando eu comecei a trabalhar na área de desenvolvimento, eu tive bastante dificuldade pra recuperar e inserir datas no banco de dados, depois de um tempo consegui pegar uma experiência e já me sinto seguro pra postar algo sobre.

### Inserindo Datas no MySQL
Suponha que eu tenha uma variável seguinte variável:  
<span class="code">$data = '18/10/2017'</span>  
Observe que a variável está com o formato 'dd/mm/yyyy'.

Para inserir essa data no banco, eu não posso fazer isso:  
<span class="code">INSERT INTO tabela (data) VALUES ('18/10/2017');</span>  
Eu não posso fazer isso pois o MySQL recupera e exibe valores de DATA no formato 'yyyy-mm-dd' e no código acima eu estou tentando inserir no formato 'dd/mm/yyyy', caso tivesse no formato 'yyyy-mm-dd' iria funcionar. 

Pra converter inserir da maneira correta, teria que ser feito isso:  
<span class="code">INSERT INTO tabela (data) VALUES (STR_TO_DATE('18/10/2017'),'%d/%m/%Y');</span>  

A função <span class="code">STR_TO_DATE</span> pega uma string (primeiro parâmetro) e um formato (segundo parâmetro) e retorna uma data que o MySQL entende, no caso a data passada no exemplo acima será transformada em: '2017-10-18'.  

Se o formato informado pra função não for válido com a string, será retornado <span class="code">null</span>, cuidado com isso.  

### Recuperando datas no formato dd-mm-yyyy
Depois que a data foi inserida, quando eu for recuperar/exbir essa data, eu não quero que a mesma seja exibida no formato que o MySQL armazena que no caso é o formato 'yyyy-mm-dd', quero exibi-la no formato 'dd/mm/yyyy'. Pra fazer isso é simples, dizer pro MySQL que você quer recuperar a data em um formato específico, a função <span class="code">DATE_FORMAT()</span> nos ajuda nisso. Fariamos isso assim:  
<span class="code">SELECT DATE_FORMAT(data, '%d/%m/%Y') FROM tabela;</span>  

Esse select irá retornar a data assim: <span class="code">'18/10/2017'</span>.

A função <span class="code">DATE_FORMAT()</span> pega uma data (primeiro parâmetro) e um formato (segundo paramêtro) e formata a data passada de acordo com o parâmetro passado.  

:)








