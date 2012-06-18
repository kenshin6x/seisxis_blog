---
layout: post
title: "Ferramentas do Desenvolvedor Moderno: Python LiveReload"
date: 2012-05-31 22:16
comments: true
categories: [ferramentas, dicas, python]
---

<p>
Esta sem dúvidas é uma ferramenta bastante interessante, ela irá ajudar na tarefa chata de atualizar o navegador sempre que houver uma mudança nos arquivos front-end da aplicação, isto quer dizer, que sempre que você alterar conteúdo de um arquivo, seu browser automaticamente irá ser atualizado, agilizando mais o trabalho. Atualmente é suportado vários tipos de arquivo como: css, less, javascript, coffescript, etc. <a href="https://github.com/lepture/python-livereload" target="_blank">Python LiveReload</a> é o server escrito em python do aplicativo <a href="http://livereload.com" target="_blank">LiveReload</a> disponível atualmente para MacOSX e Windows. Escolhi apresentar esta por ser grátis.
</p>

<p>
    Gostaria de ressaltar, que apesar da ferramenta ser operada através de linha de comando e python, e o próprio desenvolvedor citar "Python LiveReload is designed for web developers who know Python", além de simples pode ser utilizada para qualquer propósito.
</p>


<h2>Instalação</h2>

<p>
    Se você esta em ambiente MacOSX ou Linux, este passo se torna ainda mais simples pois estes sistemas operacionais ja tem Python instalado. Caso seja ambiente Windows basta instalar <a href="http://www.python.org/download/" target="_blank">Python 2.7</a> ou superior. Também recomendo instalação do pacote <a href="http://pypi.python.org/pypi/pip" target="_blank">Pip</a>.
</p>


<p>
Para instalação execute o comando:

{% codeblock %}
pip install livereload
{% endcodeblock %}

ou

{% codeblock %}
easy_install install livereload
{% endcodeblock %}
</p>

<h2>Extensão no seu navegador</h2>
<p>
    Será necessário instalar uma extensão no navegador que você utiliza. O download pode ser feito <a href="http://help.livereload.com/kb/general-use/browser-extensions" target="_blank">nesta página</a>.
</p>

<p>
    Para iniciar o servidor que irá escutar as alterações nos documentos, é bem simples, e pode ser feito de duas maneiras: Escutando tudo, ou personalizando com um <a href="https://github.com/guard/guard" target="_blank">guardfile</a>. No caso do uso do guardfile, será necessário ter algum conhecimento em python, citarei um pouco mais a respeito a seguir.
</p>

<h2>Inicializando o servidor normalmente</h2>

<p>
    Para inicializar o servidor escutando tudo, basta executar o seguinte comando:
    
    {% codeblock %}
    livereload
    {% endcodeblock %} 

    Em seguida deve-se acionar no botão da extensão {% img /images/posts/pic1.jpg Botão da extensão do LiveReload %} instalado no seu navegador. Caso seu navegador seja Google Chrome, e você estiver fazendo isto localmente, é necessário marcar o checkbox: Allow access to file URLs.
</p>

<p>
    {% img /images/posts/pic3.jpg Extensão LiveReload no Google Chrome %}
</p>

<p>
    Caso seu terminal fique semelhante como a figura abaixo, tudo deu certo, experimente alterar documentos que estão abertos no seu navegador para notar que as mudanças ocorrem imediatamente, sem necessidade de atualizar a página manualmente.
</p>

<p>
      {% img /images/posts/pic2.jpg Terminal com LiveReload rodando %}
</p>

<h2>Guardfile</h2>

<p>
    Desta maneira, o poder da ferramenta vai além do que foi citado até aqui. É possível criar funções para executar tarefas mais complexas, como por exemplo compilar seu script .less para .css antes que o navegador seja atualizado ou definir quais arquivos ou tipos serão escutados pelo servidor. Neste ponto, vale apena ler a <a href="http://livereload.readthedocs.org/en/latest/guardfile.html" target="_blank">documentação oficial</a> para maior compreendimento. Para maior aproveitamento é necessário conhecimento em python.
</p>


<p>
Para exemplo, iremos criar um guardfile em que apenas os documentos .html e .js serão escutados pelo servidor:

{% codeblock guardfile.py lang:python %}
#!/usr/bin/env python
from livereload.task import Task

Task.add('*.html')
Task.add('/static/js/*.js')
{% endcodeblock %}
<p>

<p>
Para inicializar o servidor com o guardfile, basta executar o como mostrado abaixo, ao invés da maneira anterior.

{% codeblock %}
livereload /caminho/do/meu/guardfile.py
{% endcodeblock %} 
</p>


