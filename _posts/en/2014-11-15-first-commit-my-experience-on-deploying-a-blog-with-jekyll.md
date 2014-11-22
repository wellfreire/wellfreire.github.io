---
layout: post
lang: en
title: "First Commit: My Experience on Deploying a Blog with Jekyll"
name: first_commit
author: well_freire
categories: en
tags: [jekyll]
image:
  feature: jekyll_poster.jpg
logo: jekyll_logo.jpg
share: true
comments: true
editable: true
---

#I choose you, Jekyll!

As my very first post, talking about my experience on deploying a blog on top of Jekyll seems a fair good choice. However, as many others have already done that, I will not take too much time detailing that step-by-step -- once there is already [a lot of good content](https://www.google.com/webhp?sourceid=chrome-instant&ion=1&espv=2&ie=UTF-8#q=how%20to%20install%20jekyll){:target="_blank"} about that out there, and because I am a [DRY](http://en.wikipedia.org/wiki/Don't_repeat_yourself){:target="_blank"} enthusiast (as a broader concept too). Instead, I will only highlight some points I find interesting, mainly about turning the blog into multilingual (actually, only bilingual :P).

First of all, if you have never heard about [**Jekyll**](http://jekyllrb.com/){:target="_blank"} -- not the one of [Jekyll and Hyde](http://en.wikipedia.org/wiki/Strange_Case_of_Dr_Jekyll_and_Mr_Hyde){:target="_blank"}, as the image above playfully illustrates --, it is basically an engine that transforms some plain text into a static site or blog.

Jekyll is build up as a Ruby *gem*, which makes it easy to install, especially if you already have Ruby environment set up on your machine. Due to its ease of install and simplicity, Jekyll has been greatly adopted by a growing bunch of people looking for an alternative to other famous tools (as Wordpress, for instance). I am part of this crowd, and I'm really satisfied until now. Be happy you too, and come into the wonderful world of Jekyll!

#GitHub Integration

The very first attractive of Jekyll over me was knowing about its native integration with [GitHub Pages](https://pages.github.com/){:target="_blank"}. If you do not know, GitHub has a free hosting service for project/personal pages. The only thing you have to do is follow some conventions -- for instance, repository and branch names -- and then you get a free hosted static site (or blog) out of the box. Follow the highlighted link above and read a bit more about that (or refer to Jekyll's [documentation](http://jekyllrb.com/docs/github-pages/){:target="_blank"} on this topic).

#The themes

The first thing I did when decided to use Jekyll was looking for a suitable theme from its [catalog](https://github.com/jekyll/jekyll/wiki/Themes){:target="_blank"}. I went through all the themes in that list and picked up the [So Simple](https://github.com/mmistakes/so-simple-theme){:target="_blank"} as my starting point. In this particular case, I simply got a copy from the theme's repository on GitHub and then customized it for my needs.

I changed things such:

- titles colors
- behaviour of pages' and posts' top image and logo
- main navigation bar
- added bilingual support

In order to achieve that results, I only needed to go through some key configuration and files and change some code (html, template logic and markup, css). I strongly advise you on reading some key parts of Jekyll's documentation before going through these customizations. For example, learn how Jekyll manages [configuration](http://jekyllrb.com/docs/configuration/){:target="_blank"} and its [directory structure](http://jekyllrb.com/docs/structure/){:target="_blank"}. With these in mind, branch your repository and make your own customizations (if you have this need, of course).

The biggest difficulty I had when doing that was understanding Jekyll's template engine, the Shopify's [Liquid](https://github.com/Shopify/liquid/wiki){:target="_blank"}. Liquid is quite similar, in syntax at least, to Twig -- the [*flexible, fast, and secure
template engine for PHP*](http://twig.sensiolabs.org/){:target="_blank"} -- with which I was already quite familiar. However, when trying to change some logic in my blog's templates, I had such difficulties. Not such a big deal, but a deal yet :D.

#Going Bilingual: a half but enough solution

When I decided to start blogging, one of the prerequisites I put for myself was that I would write my posts both in Portuguese (since I'm Brazilian) and English. However, when I started researching about how to do that within Jekyll, I got kind of surprised. Jekyll does not have a native support for multi language. On this subject, I agree with some opinion I read about: this is a good thing indeed. Simplicity comes with a price, and this price for Jekyll is the lack of some features we find more easily in other tools.

Actually, there are some plugins that promise to do the job with no pain for you. However, during my researches on how to accomplish this task, I came about some warnings, especially:

- The "no pain" part is not so true. These multilingual plugins may present some downsides (according to the opinions I read about), particularly with regard to the use of other plugins. Although I was not using other plugins, I was afraid on plugging in these tools in my blog;

- The GitHub Pages *safe mode* directive has something to do against the use of these plugins. I have to admit I did not searched more about that, but it seemed as a bad downside, even if it is possible to hack this.

So, especially after going through [Sylvain Durand](http://sylvain.durand.tf/making-jekyll-multilingual/){:target="_blank"}'s post, I got courageous and decided to turn Jekyll into multilingual all by myself.

###My half solution

I have to confess I could not apply Durand's solution from top to bottom. Primarily because his step-by-step guide did not work for me completely (I had some difficulties in some parts) and then because his solution expects all posts' names/titles to always being different (at least I understood this) -- a post cannot have the same title for two different languages, even if one is the translation of the other. This last issue maybe is not such a barrier for you, but I wanted my posts to being capable of having the same title in both languages -- even if I never get into this situation :).

Why my solution is a half one? Mainly because I have not turned the blog in multilingual, but only bilingual. Second, even being bilingual, some parts are always in English (for instance, nav bar and dates). Third, the search plugin (the one which comes with Jekyll) do not search only for posts in English, or only for posts in Portuguese. Despite these:

- I do not intend writing posts in other language than English or Portuguese. I already choose English as a universal alternative to my mother language. Nevertheless, if I decide really going multilingual, this is yet possible within this same solution. I only have to make flexible some logic applied (instead of testing always with an if/else);

- The parts that are not bilingual are not so important: the nav bar links can be easily read by Portuguese readers; the dates too;

- Although the search plugin is not logically restricted by language, it is naturally restricted: most of the time the searched terms will be in the reader's language; if not, I'm okay on showing posts in both languages for search results.

Thus, although being a half-solution, I believe is a fair enough half-solution. Moreover, I'm not saying that this is better than Durand's solution or any other I came to read, but it's the one that worked for my needs. It encompasses the following features:

- A post can be available exclusively in one language or in both;
- The title of both translations can be exactly the same (although this is rare);
- A visitor can navigate both in English or Portuguese version;
- There is a switch button for going from one language to the other;
- Everything works without any other third-party plugin.

Read the step-by-step below and discover how you can do what I did.

###The summarized guide for going bilingual

Although I could not apply Durand's solution exactly how described by him, I have heavily used his ideas for getting Jekyll in the way we need to make it support more than one language. Basically, I needed to follow the steps below:

####1st. Use subfolders

In order to be able to have the same page (or post) in both languages, I needed to create a subdirectory for each of them inside the existing pages' and posts's folders. So, my directories structure now seems like this:

{% highlight text %}
...
--_posts
  --en
     sample_post_in_english.md
  --pt
     sample_post_in_portuguese.md
...
--about
  --en
     index.md
  --pt
     index.md
...
{% endhighlight %}

As showed above, the <code>_posts</code> directory now has two subfolders: <code>/en</code> and <code>/pt</code>. The same *sample post* goes inside each of them with its own translated name. For pages, taking the <code>about</code> page as example, we need an <code>index.md</code> for each language too.

####2nd. Identify pages and posts

Since Jekyll does not support it natively, we need to indicate for each page and post in which language it is. For this, we create a new attribute <code>lang</code> that is put in the page/post's [Front Matter](http://jekyllrb.com/docs/frontmatter/){:target="_blank"}. Besides that, only for posts, we need to include it in a fake category that represents its language. This is done by including the language as a category in the <code>categories</code> attribute. Thus, we have the following format for our posts' front matter:

{% highlight text %}
---
layout: post
title: "First Commit: My Experience on Deploying a Blog with Jekyll"
name: first_commit
lang: en
categories: en

// other attributes

---
{% endhighlight %}

The <code>lang</code> attribute will be used in templates for referencing the current page/post language, whereas the *category* setting serves only for Jekyll knows how to find a post referenced by a url beginning with its language short name (for instance, <code>/en/my-post</code>).

Besides language identification, we create another attribute for relating a post to its translations. As Durand did, I called this new attribute <code>name</code> and its value need to be unique: **all the translations of a post need to share a common *and unique* name**. This name can be set to whatever value you want, you just need to ensure its uniqueness -- in the steps below you will better understand this need.

####3rd. Categories in post permalink

In order Jekyll can find a post referenced by its lanaguage, as told previously, we need to configure posts' permalinks to include categories. This is done by changing the <code>permalink</code> attribute (generally set globally in the <code>_config.yml</code> file):

{% highlight yaml %}
# Jekyll configuration

permalink:   /:categories/:title/
{% endhighlight %}

####4th. Filtering posts by language

When we access the page that lists posts, ideally we want to show only the posts for the language that the reader is interest -- the current page language. This is done by hacking the logic for listing posts and adding a condition that verifies the post language. In the page containing that logic -- for this blog, the page is <code>posts</code> itself, and the code is in a include file used both by <code>/posts/en/index.md</code> and by <code>/posts/pt/index.md</code> -- we need to do something like:

{% highlight liquid %}
# _includes/posts.html

{{ "{% assign posts = site.posts | where: 'lang', page.lang"}} %}
<ul class="post-list">
    {{ "{% for post in posts "}} %} 
        <li><a href="{{ "{{ site.url "}}}}{{ "{{ post.url "}}}}">{{ "{{ post.title "}}}}</a></li>
    {{ "{% endfor "}} %}
</ul>

{% endhighlight %}

Note that, before we iterate through all posts, we assign <code>site.posts</code> to a new <code>posts</code> variable using the current <code>page.lang</code> as a filtering condition. That way, only the posts in the current page's language will be listed.

Thus, a similar solution can be used whenever we need to filter current page content according to its language.

####5th. Navigation

The main navigation bar needs to get its links pointing to the current language pages -- remember that I decided to change only the links in the main nav bar, the labels remain all in English whatever language the page is. First, you need to elect a default language. As I chose English, I needed to do the following in the <code>_/data/navigation.yml</code> file:

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

This way, the blog defaults to the English version of the <code>index</code> of each page. When a visitor loads a page, the following piece of code decides between pointing the links to one of the two languages:

{% highlight liquid %}
# _includes/navigation.html

...

# inside the loop for creating main nav links
{{ "{% assign link_url = link.url | replace_first: 'en', page.lang "}} %}

...

{% endhighlight %}

Note that the decision is made only by replacing the first occurrence of <code>en</code> -- the short name for English -- in the link URL by the current page language short name when iterating over all links defined in <code>_data/navigation.yml</code>. Once the default language is English, if the page is in English itself nothing will change; on the other hand, if page in is Portuguese, all the link URLs will be changed accordingly.

####6th. Switching between languages

This blog has English as its default language. So, what happens if someone wants to navigate in its Portuguese version? The answer is that we need a way that such a visitor can switch to its desired language. My solution was a button in the right top of the blog, where a flag and label allows a visitor to switch to the other available language. The solution is pretty straightforward -- making use of pages' <code>lang</code> and <code>name</code> attributes we talked about earlier --, and its only trick is the differentiation between common pages and post pages. Since this is the most important feature for the bilingual support, below is transcripted the complete code I used for creating the switch button:

{% highlight liquid %}
# _includes/switch_lang.html

# here we capture the language to switch to (the opposite to the current one)
{{ "{% capture switch_lang "}}%}{{ "{% if page.lang == 'en' "}}%}pt{{ "{% else "}}%}en{{ "{% endif "}}%}{{ "{% endcapture "}}%}

# here we differentiate the switch button behavior according to the page layout
{{ "{% if page.layout == 'page' "}}%}

    {{ "{% assign switch_lang_url = page.dir | replace_first: page_lang, switch_lang "}}%}

    # this is a hack to ensure correct switching when the current page was accessed
    # via the main site url, which not terminates with the language short name
    {{ "{% if switch_lang_url == '/' and page.dir == '/' "}}%}
        {{ "{% assign switch_lang_url = '/pt' "}}%}
    {{ "{% endif "}}%}

{{ "{% else "}}%}

    # here we obtain the posts whose name is the same as the current one
    {{ "{% assign same_name_posts = site.posts | where:'name', page.name "}}%}

    # we assign a switch_url only if we have a translation for this post
    {{ "{% if same_name_posts.size == 2 "}}%}
        {{ "{% for _post in same_name_posts "}}%}
            {{ "{% if _post.lang == switch_lang "}}%}
                {{ "{% capture switch_lang_url "}}%}{{ "{{ _post.url "}}}}{{ "{% endcapture "}}%}
            {{ "{% endif "}}%}
        {{ "{% endfor "}}%}
    {{ "{% endif "}}%}

{{ "{% endif "}}%}

# if the current page (or post) has a translation, we show the switch button
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

#Final thoughts

Jekyll is undoubtedly a simple and straightforward tool for deploying your static website or blog. Its installation is pretty easy, and even if you don't entirely like one of the available open source themes you can put your hands on and make some customizations by your own with not much effort.

Considering I had most of the difficult on finding a good way for getting Jekyll to support more than one language, I spent most of the time trying to explain how I could accomplish that task. However, if this step-by-step is missing some key concept or detail you need, please feel free to visit (or even fork) this blog public [repository](https://github.com/wellfreire/wellfreire.github.io){:target="_blank"} on GitHub and search for that. Also, you can get in touch with me via some of the contact forms in this blog footer.