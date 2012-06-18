---
layout: post
title: "Ferramentas do Desenvolvedor Moderno: Sparkup e Zen-Coding"
date: 2012-06-03 22:38
comments: true
categories: [ferramentas,dicas]
---

<p>
Escrever páginas em HTML pode ser uma tarefa bastante repetitiva... não com <a href="https://github.com/rstacruz/sparkup" target="_blank">Sparkup</a> ou <a href="http://code.google.com/p/zen-coding/" target="_blank">Zen-Coding</a>! Ambas são ferramentas que simplificam a sintaxe do HTML agindo como snippets, proporcionando escrever longos blocos de código em uma velocidade impressionante, consequentemente aumentará a produtividade, algo ideal para programadores de front-end.</p>

<p>Tratam-se de plugins que podem ser instalados em diversos ides/editores de texto (é preciso ver a compatibilidade de cada um). O Sparkup é inspirado no Zen-Coding e traz algumas melhorias, em contra-partida, o Zen-Coding possui maior compatibilidade de editores em que pode-se instala-lo. Irei falar um pouco mais sobre ambos plugins.<p>

<p>Para os exemplos demonstrados abaixo, estou utilizando o <a href="http://code.google.com/p/macvim/" target="_blank">MacVim</a>  (GUI do VIM para MacOSX).</p>


<h2>Zen-Coding: maior compatibilidade</h2>
<p>o Zen-Coding possui uma grande lista de softwares compatíveis, entre eles, ferramentas exclusivas de Windows (Notepad++, PSPad) e MacOSX (Textmate, Coda, Espresso), o que torna-o uma boa escolha. Também é suportados ferramentas <a href="http://en.wikipedia.org/wiki/Cross-platform" target="_blank">cross-plataform</a>, entre elas ferramentas que funcionam em Linux (Vim, Eclipse, Komodo Edit/IDE), então usuários de linux não tem o que se preocupar. o Zen-Coding também possui uma variação maior de snippets podendo ate ser utilizado para escrever CSS e XSI.</p>

<p>O funcionamento é bastante simples, basta escrever em uma linha o código de semântica abreviada e utilizar alguma tecla para disparar a ação, e o plugin converterá esta linha no bloco completo correspondente ao que foi escrito. Vejamos alguns exemplos:
</p>

<p>Escrevendo a linha abaixo e pressionando <code>ctrl+e</code> (no caso do MacVim):</p>

{% codeblock lang:html %}
div#pagina>div.logo+ul#menu>li*5>a
{% endcodeblock %}

será convertido em :

{% codeblock lang:html %}
<div id="pagina">
        <div class="logo"></div>
        <ul id="menu">
                <li><a href=""></a></li>
                <li><a href=""></a></li>
                <li><a href=""></a></li>
                <li><a href=""></a></li>
                <li><a href=""></a></li>
        </ul>
</div>
{% endcodeblock %}
</p>

<h2>Sparkup: Um recurso interessante</h2>
<p>O Sparkup foi inspirado no Zen-Coding e trás algumas melhorias, contudo apenas o Textmate e o Vim são editores de texto suportados oficialmente (até agora). O recurso mais notável é poder escrever <code>></code> e <code><</code> entre um node e outro para referenciar quando deseja que o próximo node seja inserido dentro ou fora do node antecessor, respectivamente. Isto faz com que seja possível escrever a estrutura de uma página inteira em poucos segundos. Em termos gerais, seu funcionamento é igual ao Zen-Coding. Vejamos alguns recursos do Sparkup demonstrados em um único exemplo:</p>

{% codeblock lang:html %}
div#wrap > div#header > div#logo > h1{seisxis.com} < div#menu > ul > li.item-$*3 <<< div#content + div#footer > p{copyright 2012}
{% endcodeblock %}

{% codeblock lang:html %}
<div id="wrap">
  <div id="header">
    <div id="logo">
      <h1>seisxis.com</h1>
    </div>
    <div id="menu">
      <ul>
        <li class="item-1"></li>
        <li class="item-2"></li>
        <li class="item-3"></li>
      </ul>
    </div>
  </div>
  <div id="content"></div>
  <div id="footer">
    <p>copyright 2012</p>
  </div>
</div>
{% endcodeblock %}

<h2>Então, qual é o melhor?</h2>
<p>Ambos são bastante similares, porém não ha como negar que recurso presente no Sparkup de poder prosseguir e retornar dentro dos nodes é uma vantagem de peso sobre o Zen-Coding. Particularmente, este é o meu preferido. Porém, pode ser um pouco frustrante para algumas pessoas não poder instala-lo, já que apenas o Textmate e o Vim são suportados oficialmente. Como ambos tem recuros similares, o Zen-Coding pode ser sim uma ótima alternativa para quem não poder instalar o Sparkup, já que o poder da ferramenta não se limita apenas a um este recurso. Vale muito utilizar algum dos dois e perceber a produtividade decolar.</p>