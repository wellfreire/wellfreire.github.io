---
layout: post
lang: pt
title: "First Commit: Minha Experiência Implementando Um Blog Com Jekyll"
name: first_commit
author: well_freire
categories: pt
tags: [jekyll]
image:
  feature: jekyll_poster.jpg
  credit: wikipedia
  creditlink: http://upload.wikimedia.org/wikipedia/commons/7/78/Dr_Jekyll_and_Mr_Hyde_poster_edit2.jpg
logo: jekyll_logo.jpg
share: true
comments: true
editable: true
---

#Eu escolho você, Jekyll!

Como primeiríssmo post, falar da minha experiência implementando um blog com o Jekyll parece bastante justo. No entanto, como tantos outros já o fizeram, eu não vou tomar muito tempo detalhando o passo-a-passo de como fazer isso -- uma vez que já tem [um monte de conteúdo](https://www.google.com.br/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=como%20instalar%20o%20jekyll){:target="_blank"} sobre o assunto por aí, e também porque eu sou um entusiasta do [DRY](http://pt.wikipedia.org/wiki/Don%27t_repeat_yourself){:target="_blank"} (como um conceito mais amplo também). Vou apenas destacar alguns pontos que acho interessantes, principalmente sobre como tranformar o blog em multilíngue (na verdade, apenas bilíngue :P).

Em primeiro lugar, se você nunca ouviu falar do [**Jekyll**](http://jekyllrb.com/){:target="_blank"} -- não esse da imagem de [Jekyll and Hyde](http://pt.wikipedia.org/wiki/Strange_Case_of_Dr_Jekyll_and_Mr_Hyde){:target="_blank"} no topo, que eu coloquei de brinks --, ele é basicamente uma ferramenta que tranforma texto em um site estático (ou blog).

O Jekyll é construído como uma *gem* do Ruby, o que o torna fácil de instalar, principalmente se você já tem o ambiente Ruby instalado na sua máquina. Devido a essa facilidade de instalação e simplicidade, ele tem sido amplamente adotado por um crescente número de *gentes* que procuram por uma alternativa a outras famosas ferramentas (como o Wordpress, por exemplo). Eu sou uma dessas pessoas, e estou bastante satisfeito até agora. Seja feliz você também e venha para o maravilhoso mundo do Jekyll!

#Integração com o GitHub

O primeiro atrativo do Jekyll pra mim foi saber da sua integração nativa com o [GitHub Pages](https://pages.github.com/){:target="_blank"}. Caso você não saiba, o GitHub tem um serviço de hospedagem na faixa para páginas pessoais ou de projetos. A única coisa que você precisa fazer é seguir algumas convenções -- por exemplo, o nome do repositório e dos *branches* -- e  então você tem o seu site (ou blog) 'digrátis' de maneira bem simples. Acesse o link destacado acima e leia um pouco mais sobre (ou vá até a [documentação](http://jekyllrb.com/docs/github-pages/){:target="_blank"} do Jekyll sobre esse tópico).

#Os temas

A primeira coisa que eu fiz quando decidi utilizar o Jekyll foi procurar por um tema do meu gosto lá no [catálogo](https://github.com/jekyll/jekyll/wiki/Themes){:target="_blank"} que tem no repositório. Eu vasculhei todos os temas na lista e escolhi o [So Simple](https://github.com/mmistakes/so-simple-theme){:target="_blank"} como ponto de partida. Neste caso, em particular, eu precisei apenas copiar o repositório do tema no GitHub e personalizá-lo de acordo com as minhas necessidades.

Eu alterei coisas como:

- cores dos títulos
- comportamento da imagem e logotipo do topo das páginas e posts
- menu de navegação principal
- adição de suporte bilíngue

Pra alcançar estes resultados, eu precisei apenas brincar com alguns arquivos e configurações importantes, alterando algumas partes do código (html, lógica e marcação nos templates, css). Eu recomendo fortemente que você dê uma olhada em algumas partes importantes da documentação do Jekyll antes de fazer estão alterações. Por exemplo, aprenda como o Jekyll gerencia [configurações](http://jekyllrb.com/docs/configuration/){:target="_blank"} e sua [estrutura de diretórios](http://jekyllrb.com/docs/structure/){:target="_blank"}. Com isso em mente, abra um novo *branch* no repositório do tema que você escolheu e faça suas próprias personalizações (se você precisar, é claro).

A maior dificuldade que tive foi em entender a ferramenta de template utilizada pelo Jekyll, o [Liquid](https://github.com/Shopify/liquid/wiki){:target="_blank"} da Shopify. O Liquid é bastante similar, pelo menos em sintaxe, ao Twig -- [*the flexible, fast, and secure template engine for PHP*](http://twig.sensiolabs.org/){:target="_blank"} -- com o qual eu já era bastante familiar. No entanto, quando eu fui alterar algumas partes da lógica nos templates do blog, eu tive alguma dificuldade. Nada de exagerado, mas ainda assim alguma dificuldade.

#Rumo ao blog bilíngue: uma meia-solução, mas suficiente

Quando decidi começar a blogar, um dos pré-requisitos que estabeleci pra mim mesmo foi que eu escreveria os posts tanto em português ([*já que sou brasileiro*](https://www.youtube.com/watch?v=KwcK7vF2t0A){:target="_blank"}) e inglês. No entanto, quando comecei a pesquisar sobre como fazer isso, fiquei um pouco surpreso. O Jekyll não tem suporte nativo multilíngue. Sobre isso, aliás, concordo com algumas opiniões que acabei lendo à respeito: isso é algo bom no fim das contas. Simplicidade tem o seu preço e, no caso Jekyll, o preço é a falta de algumas funcionalidades que encontramos com maior facilidade em outras ferramentas.

Na verdade, existem alguns plugins que prometem fazer o trabalho sujo de maneira indolor pra você. No entanto, durante as minhas pesquisas de como realizar essa tarefa, eu acabei lendo alguns avisos sobre o uso dos plugins, com destaque para:

- A parte do "indolor" não é tão verdade assim. Esses plugins multilíngues podem ter algumas partes ruins (de acordo com o que eu li), particularmente no que se refere ao uso de outros plugins em conjunto. Apesar de não estar utilizando outros plugins, fiquei receoso em utilizar estas ferramentas no meu blog;

- A diretiva de  *safe mode* do GitHub Pages tem alguma coisa contra o uso de plugins. Admito que não fui pesquisar muito a fundo sobre o assunto, mas me pareceu um "boa" parte ruim, mesmo que seja possível contornar isso.

Assim, principalmente depois de dar uma olhada no [post](http://sylvaindurand.org/making-jekyll-multilingual/){:target="_blank"} do Sylvain Durand, eu tomei coragem e decidi fazer por conta própria o Jekyll aceitar mais de uma língua.

###Minha meia-solução

Preciso confessar que não consegui aplicar de maneira estrita a solução do blog do Durand. Primeiramente, porque o passo-a-passo dele não funcionou muito bem pra mim (eu tive dificuldades com algumas partes) e, "segundamente", porque a solução dele espera que os posts tenham sempre nomes diferentes (pelo menos foi isso que entendi) -- um post não pode ter o mesmo título para duas línguas diferentes, mesmo quando um é tradução do outro. Essa pode não ser uma barreira de grande importância pra você, mas eu queria que meus posts pudessem ter o mesmo título para as duas línguas -- mesmo que nunca precise disso :).

Por quê a minha solução é incompleta? Principalmente porque eu não implementei suporte multilíngue de verdade, apenas bilíngue. Segundo, mesmo sendo bilíngue, algumas partes estão sempre em inglês (por exemplo, o menu principal e as datas). Terceiro, o plugin de busca (aquele que vem junto com o Jekyll) não permite busca apenas por posts em inglês, ou em português. Apesar disso tudo:

- Eu não pretendo escrever posts em outra língua que não seja inglês ou português. Eu já escolhi o inglês justamente por ser uma alternativa universal a minha língua materna. Além do mais, se eu decidir depois que preciso que seja multilíngue, ainda é possível fazer isso usando essa mesma solução. Precisaria apenas flexibilizar a lógica aplicada (ao invés de utilizar apenas if/else);

- As partes que não são bilíngues não são tão importantes: o menu principal pode ser facilmente lido por quem fala português; as datas também;

- Apesar de o plugin de busca não ser restrito por língua logicamente falando, ele é restrito naturalmente: na maioria das vezes os termos buscados estarão na língua de interesse do leitor; se não estiver, não me preocupo em exibir os posts em ambas as línguas como resultado das buscas.

Assim, apesar de ser uma meia-solução, eu acredito que seja uma meia-solução bastante justa. Além disso, não estou dizendo que a solução que apliquei aqui seja melhor que a do Durand ou de qualquer outra que tenha visto, mas é a que melhor funcionou pra atender minhas necessidades. Ela engloba as seguintes características:

- Um post pode existir em apenas uma língua ou em ambas;
- O título de ambas as traduções pode ser exatamente o mesmo (apesar de ser difícil acontecer);
- Um visitante pode navegar na versão em inglês ou português;
- Existe um botão pra trocar de um língua pra outra;
- Tudo isso funciona sem a necessidade de utilizar qualquer plugin de terceiro.

Leia o passo-a-passo abaixo e descubra como você pode fazer o que eu fiz.

###Guia resumido rumo ao suporte bilíngue

Apesar de não ter conseguido aplicar exatamente a solução descrita pelo Durand, eu usei fortemente as ideias dele para conseguir levar o Jekyll pelo caminho que precisamos para que que tenha suporte a mais de uma língua. Basicamente, tive que seguir os passos abaixo:

####1o. Utilizar subpastas

À fim de ser possível ter a mesma página (ou post) em ambas as línguas eu precisei criar um subdiretório para cada uma delas dentro da pasta já existente da página/post. Assim, minha estrutura de diretórios ficou algo como:

{% highlight text %}
...
--_posts
  --en
     post_de_exemplo_em_ingles.md
  --pt
     post_de_exemplo_em_portugues.md
...
--about
  --en
     index.md
  --pt
     index.md
...
{% endhighlight %}

Como mostrado acima, o diretório <code>_posts</code> agora tem duas subpastas: <code>/en</code> e <code>/pt</code>. O mesmo *post_de_exemplo* vai dentro de cada um deles como com seu próprio nome traduzido. Para páginas, tomando a página <code>about</code> como exemplo, nós precisamos de um <code>index.md</code> para cada uma das línguas também.

####2o. Identificar páginas e posts

Já que o Jekyll não suporta isso nativamente, precisamos indicar para cada página e post em que língua está. Para isso, nós criamos um novo atributo <code>lang</code> que é colocado no [Front Matter](http://jekyllrb.com/docs/frontmatter/){:target="_blank"} dá página/post. Além disso, apenas para posts, precisamos incluí-lo em uma falsa categoria que representa a língua em que está. Isso é feito incluindo a língua como uma categoria no atributo <code>categories</code>. Assim, temos o seguinte formato para o *front matter* do nosso post:

{% highlight text %}
---
layout: post
title: "First Commit: Minha Experiência Implementando Um Blog Com Jekyll"
name: first_commit
lang: pt
categories: pt

// demais atributos

---
{% endhighlight %}

O atributo <code>lang</code> será utilizado nos templates para fazer refrência à língua da página/post atual, enquanto a configuração de categoria serve apenas para que o Jekyll saiba como encontrar um post que comece com a abreviação da língua em que o mesmo se encontra (por exemplo, <code>/pt/meu-post-em-portugues</code>).

Além da identificação da língua, nós criamos um outro atributo para relacionar um post as suas traduções. Conforme feito pelo Durand, eu chamei esse novo atributo de <code>name</code> e o seu valor precisa ser único: **todas as traduções de um post precisam compartilhar um nome em comum e *único***. Este nome pode ser o que você achar melhor, você precisa apenas garantir sua unicidade -- nos passos abaixo você irá entender melhor essa necessidade.

####3o. Categoria no *permalink* dos posts

Para que o Jekyll possa encontrar um post referenciado pela língua em que está escrito, conforme dito anteriormente, nós precisamos configurar o *permalink* dos posts para incluir categorias. Isso é feito alterando o atributo <code>permalink</code> (geralmente configurado globalmente no arquivo <code>_config.yml</code>):

{% highlight yaml %}
# configuração do Jekyll

permalink:   /:categories/:title/
{% endhighlight %}

####4o. Filtrando posts por língua

Quando acessamos a página que lista os posts do blog, idealmente nós queremos exibir apenas os posts escritos na língua de interesse do leitor -- a língua da página em que se encontra. Isso é feito alterando a lógica de listagem de posts e adicionando uma condição que verifica o atributo <code>lang</code> de cada post. Na página que contém essa lógica -- no caso desse blog, a página é <code>posts</code> mesmo, e o código está em um arquivo de *include* utilizado tanto por <code>/posts/en/index.md</code> quanto por <code>/posts/pt/index.md</code> -- nós precisamos fazer algo como:

{% highlight liquid %}
# _includes/posts.html

{{ "{% assign posts = site.posts | where: 'lang', page.lang"}} %}
<ul class="post-list">
    {{ "{% for post in posts "}} %} 
        <li><a href="{{ "{{ site.url "}}}}{{ "{{ post.url "}}}}">{{ "{{ post.title "}}}}</a></li>
    {{ "{% endfor "}} %}
</ul>

{% endhighlight %}

Perceba que, antes de iterar por todos os posts , nós atribuímos o conteúdo de <code>site.posts</code> para uma nova variável <code>posts</code> utilizando o valor de <code>page.lang</code> (a língua da página atual) como filtro. Deste modo, apenas os posts escritos na mesma língua que a página atual serão listados.

Logo, uma solução similar pode ser utilizada sempre que for necessário filtrar o conteúdo de uma determinada página de acordo com a língua da mesma.

####5o. Navegação

O menu principal de navegação precisa que seus links apontem para páginas na mesma língua que a página atual -- lembre-se que eu decidi alterar apenas os links propriamente ditos, sendo que os nomes das páginas continuam sempre os mesmos, independentemente da língua da página atual. Primeiro, você precisa escolher um língua como sendo a principal. Como eu escolhi o inglês, eu precisei fazer o seguinte no arquivo <code>_/data/navigation.yml</code>:

{% highlight yaml %}
# _data/navigation.yml

- title: Home
  url: /en/

- title: About
  url: /about/en/

- title: Posts
  url: /posts/en/

- title: Tags
  url: /tags/en/
{% endhighlight %}

Dessa maneira, o blog fica com a versão em inglês de <code>index.md</code> como padrão para cada página. Quando um visitante carregar um página, o seguinte fragmento de código decide para qual das suas línguas os links irão apontar:

{% highlight liquid %}
# _includes/navigation.html

...

# dentro do laço que cria os links do menu principal
{{ "{% assign link_url = link.url | replace_first: 'en', page.lang "}} %}

...

{% endhighlight %}

Note que a decisão é feita apenas substituindo a primeira ocorrência de <code>en</code> -- a abreviação de *english* -- na URL do link pela abreviação da língua da página atual ao iterar todos os links definidos em <code>_data/navigation.yml</code>. Uma vez que a língua padrão é o inglês, se a página atual estiver em inglês nada irá mudar; por outro lado, se a página estiver em português, todas as URLs serão alteradas de acordo.

####6o. Alternando entre as línguas (ui!)

Este blog possui o inglês como língua padrão. Então, o que acontece quando alguém quer navegar na versão em em português? A resposta é que precisamos de uma maneira para que tal visitante possa alternar para a língua de sua preferência. Minha solução foi um botão no topo, à direita do blog, onde uma *flag* permite ao leitor fazer essa alternação conforme necessário. A solução é bastante direta -- fazendo uso dos atributos <code>lang</code> e <code>name</code> que criamos para as páginas e posts anteriormente --, e o único truque é a diferenciação entre páginas comuns e páginas de posts. Considerando que essa é a parte mais importante da funcionalidade do suporte bilíngue, abaixo fiz a transcrição completa do código que usei para criar o tal botão:

{% highlight liquid %}
# _includes/switch_lang.html

# aqui obtemos a língua para a qual irá alternar (a oposta à da página atual)
{{ "{% capture switch_lang "}}%}{{ "{% if page.lang == 'en' "}}%}pt{{ "{% else "}}%}en{{ "{% endif "}}%}{{ "{% endcapture "}}%}

# diferenciamos o comportamento do botão de acordo com o layout da página
{{ "{% if page.layout == 'page' "}}%}

    {{ "{% assign switch_lang_url = page.dir | replace_first: page_lang, switch_lang "}}%}

    # este é um hack para garantir o funcionamento correto quando a página for acessada
    # através da url principal do site, que não possui a abreviação da língua no final
    {{ "{% if switch_lang_url == '/' and page.dir == '/' "}}%}
        {{ "{% assign switch_lang_url = '/pt' "}}%}
    {{ "{% endif "}}%}

{{ "{% else "}}%}

    # aqui nós obtemos os posts cujo nome é o mesmo do post atual
    {{ "{% assign same_name_posts = site.posts | where:'name', page.name "}}%}

    # nós atribuímos um valor para switch_url apenas se existir uma tradução para o post atual
    {{ "{% if same_name_posts.size == 2 "}}%}
        {{ "{% for _post in same_name_posts "}}%}
            {{ "{% if _post.lang == switch_lang "}}%}
                {{ "{% capture switch_lang_url "}}%}{{ "{{ _post.url "}}}}{{ "{% endcapture "}}%}
            {{ "{% endif "}}%}
        {{ "{% endfor "}}%}
    {{ "{% endif "}}%}

{{ "{% endif "}}%}

# se a página/post atual possui uma tradução, nós exibimos o botão de switch
{{ "{% if switch_lang_url "}}%}
    {{ "{% capture lang_label "}}%}{{ "{% if page.lang == 'en' "}}%}ver em português{{ "{% else "}}%}read in english{{ "{% endif "}}%}{{ "{% endcapture "}}%}
    <ul class="lang-switch">
        <li>
            <a href="{{ "{{ switch_lang_url "}}}}">
                <img src="{{ "{{ site.url "}}}}/images/ico-lang_{{ "{{ switch_lang "}}}}.png">&nbsp;&nbsp;{{ "{{ lang_label "}}}}
            </a>
        </li>
    </ul>
{{ "{% endif "}}%}

{% endhighlight %}

#Conclusão

O Jekyll é sem dúvidas uma ferramenta simples e direta para implementar o seu website estático ou blog. Sua instalação é bastante fácil e, mesmo se você não se agradar completamente de um dos temas *open source* disponíveis, é possível botar a mão na massa e fazer as suas alterações sem muito esforço.

Considerando que minha maior dificuldade foi encontrar uma boa maneira de fazer com que o Jekyll suportasse mais de uma língua, passei a maior parte do post tentando explicar como consegui cumprir isso. No entanto, caso esteja faltando alguma peça importante ou detalhe do qual você precise neste passo-a-passo, por favor fique à vontade para dar uma olhada (ou mesmo fazer um *fork*) deste [repositório público](https://github.com/wellfreire/wellfreire.github.io){:target="_blank"} no GitHub e procurar pelo que precisa. Você pode também entrar em contato comigo através de uma das formas existentes no rodapé deste blog.
