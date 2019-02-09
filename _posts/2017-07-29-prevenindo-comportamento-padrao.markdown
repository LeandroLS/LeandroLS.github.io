---
title:  "Evitando submissão de um formulário de maneira simples"
date:   2017-07-29 19:39:46
comments: true
description : "Evitando submissão de formulário"
---

Recentemente eu tive que fazer um evento de clique funcionar em um botão de um formulário e perdi um tempo enorme tentando entender porque não funcionava o evento que implementei. 
Imagine o seguinte formulário:

![Foto formulário]({{ site.baseurl }}../assets/img/testa-js.png)

Observe que no botão eu adicionei um evento que chama a função <span class="code">clicou()</span>. Aparentemente está tudo certo, após eu clicar no botão a função <span class="code">clicou()</span> deveria funcionar, certo ? Era assim que eu pensava, só que se eu clicar no botão, o evento que eu adicionei não vai funcionar. Não vai funcionar pois quando eu clicar, o formulário vai ser submetido e a página vai ser __recarregada__ e eu nem vou ver a mensagem da função <span class="code">clicou()</span>. 

A origem do problema é que ao clicar no botão, o formulário é submetido e a página recarrega. Para que a página não seja recarregada após eu clicar no botão, basta eu __evitar o comportamento padrão do botão__. Eu posso fazer isso de algumas maneiras, uma maneira bem fácil de resolver isso basta adicionar o atributo <span class="code">type="button"</span> ao botão. Exemplo:

![Foto formulário]({{ site.baseurl }}../assets/img/testa-js2.png)

Dessa maneira sim, a função <span class="code">cliclou()</span> funcionará.

Quando voce adiciona <span class="code">button</span> dentro de um <span class="code">form</span> você atribuindo ou não um <span class="code">type</span> pro botão, o comportamento padrão dele será como se tivesse com um <span class="code">type="submit"</span>, e esse <span class="code">type="submit"</span> tem o comportamento de fazer a submissão do <span class="code">form</span> e após isso a página é recarregada.

Quando você seta o atributo <span class="code">type="button"</span>, você tira o comportamento padrão do botão, ele não vai tentar enviar os dados do <span class="code">form</span> e não vai recarregar a página.

Para maiores detalhes, recomendo consultar a documentação da [Mozilla Developer Network](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/button).

