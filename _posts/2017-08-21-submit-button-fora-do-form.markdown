---
title:  "Como colocar um submit button fora do form"
date:   2017-08-21 19:36:00
comments: true
---

Olá. Hoje eu "precisei" fazer com que um botão fora de uma tag <span class="code">form</span> fizesse a submissão de um <span class="code">form</span>. A princípio eu achei que não era possível, mas com uns 5 minutos de pesquisa na internet eu descobri que agora o HTML5 tem um novo atributo chamado <span class="code">form</span> que me ajuda nisso. Assim que se usa: 
<script src="https://gist.github.com/LeandroLS/16a1249d6cace058bf38e506b475c0ef.js"></script>

Observe que eu tive que dar um <span class="code">id</span> pro <spam class="code">form</span> e ligar esse id ao <span class="code">input</spam>

Testei aqui e funcionou. Uso Chrome.

Navegadores que suportam esse atributo:

* Opera 9.5+
* Safari 5.1+ 
* Firefox 4+
* Chrome 10+

Até a próxima. :)