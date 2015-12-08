---
layout: post
title: Dr. Jekyll, got any comments?
categories: jekyll disqus
---

I feel that writing blog posts with Jekill is empowering.  
It's close to the metal, so you have lots of control over the resulting HTML. It's flexible, so it is easy to think about the design in terms of independent modules.

I will describe how I added comments to the posts on this blog and touch on a few Jekyll features in the process.

## Don't reinvent the wheel
No need to reinvent the wheel if free, well-rounded wheels are avaliable.
I settled on [Disqus](https://disqus.com/) as the provider for comments infrastructure. 

I created an account then went to the admin page -> 'Installing Disqus' -> 'Universal Code' and was presented with a piece of embeddable HTML+JS.

## Install this bad boy
Let's find the template for posts.  
Depending on the Jekyll theme you chose, YMMV, but it's safe to assume that it will be under the `/_layouts` folder. 

My template for posts happens to be `/_layouts/post.html`

The first thing I did was dump the Disqus snippet near the end of the template to see if it renders correctly. (It did.)

But I like to keep unrelated things separate, so it's time to refactor the snippet into its own file.  **S**ingle **R**esponsibliity **P**rinciple for HTML, baby! 

In the post template file, I replaced the Disqus snippet with a single line: 

{% raw %} 
    {% include comments.html %}
{% endraw %} 

I have then created `/_includes/comments.html` and pasted the Disqus code there. 

Note that it originally contained two macros that need to be replaced by the user: `PAGE_URL` and `PAGE_IDENTIFIER`.  
I have replaced them with the coreesponding Jekyll variables:

- PAGE_URL : {% raw %} `{{ site.url }}/{{ page.url }}` {% endraw %} 
- PAGE_IDENTIFIER : {% raw %} `{{ page.id }}` {% endraw %} 

The double curlies syntax should be familiar to anyone that worked with Angular or JS templating engines like Mustache or Handlebars. The *value* of the contents is rendered directly in the final HTML.

Here is the complete snippet:

```html

<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    
{% raw %} 
    var disqus_config = function () {
        this.page.url = '{{ site.url }}/{{ page.url }}';  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = '{{ page.id }}'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
{% endraw %}     
    (function() {  // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
        var d = document, s = d.createElement('script');
        
        s.src = '//diaconesq.disqus.com/embed.js';  // IMPORTANT: Replace EXAMPLE with your forum shortname!
        
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>

``` 


## Cherry-picking posts with comments

I want to be able to enable/disable comments on specific blog posts.  
Jekyll *conditional tags* to the rescue!

I wrapped the whole comments snippet with this: 

{% raw %} 
    {% if page.comments %}
    ...
    {% endif %}`
{% endraw %}
 
For now, `page.comments` isn't defined anywhere, so this effectively disables comments globally.
There are now two ways to decide which posts get comments: opt-in and opt-out.

The **opt-in** method is trivial: for a given post, define the variable `comments` with a value of `true` in the front matter:

    ---
    layout: post
    title: The title
    comments: true
    ---

The **opt-out** option, where comments are *enabled* by default unless otherwise specified, is just a little trickier. 

For this to work, I need to define a default value for Jekyll's `comment` variable.

This is powerful, since you can define different defaults for different parts of the site -- but it's not quite as straight-forward as the first option.

Default property values, like all other global settings, are defined in `/_config.yml`. 

What I need is the property `comments` with a default value of `true` for *all* pages of type `post`. Here's how to do define this filter:

    defaults:
      -
        scope:
          path: ""
          type: "posts"
        values:
          comments: true

Now all my pages of type `post` automatically get the correct property.

If I want to **disable** comments for a particular post, I will redefine the property in the post's front matter with a value of `false` :

    ---
    layout: post
    title: The title
    comments: false
    ---

That's it! I now have cleanly-separated comments that are easy to switch on or off. 

Now how about making some use of them? Got a suggestion? A Jekyll trick you want to share? Go make some noise and, you know... *learn and let learn*!
