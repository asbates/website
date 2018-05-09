---
title: How to Customize A Blogdown Website
author: ''
date: '2018-05-09'
slug: customize-blogdown-theme
categories: []
tags: []
---


In this post I would like to explain how I personalized my site by customizing the default blogdown theme. This was the most intimidating part for me because I know virtually nothing about `html` and `css`. I thought I would share what I did in case others want to edit a theme to make it more their own.

Of all the themes recommended in the [blogdown book](https://bookdown.org/yihui/blogdown/), I liked the default theme the best. Some of the others were a bit too minimal and I didn't want to search for a Hugo theme and then find out it doesn't play nice with Latex and R. So I went with the default theme ([Hugo Lithium](https://github.com/yihui/hugo-lithium)).

But, there were a few things I wanted to change to make it my own. As suggested in the blogdown book, modifying the Hugo theme directly is probably not a good idea. So instead I copied the `themes/hugo-lithium-theme/layouts` and `themes/hugo-lithium-theme/static` folders to the main directory of the site and edited those. I'm not entirely sure if this is the best way to do things but that's what I gathered from the [Custom Layouts](https://bookdown.org/yihui/blogdown/custom-layouts.html) section of the blogdown book. Just in case I wanted to revert things back to the original, I didn't delete any of the code in the files. Instead, I commented out the lines I didn't want and added comments to the lines I changed so I could keep track of what I did. This should also make it easier for you to see exactly where I made the changes if you want to look at the files in the GitHub repository for [this site](https://github.com/asbates/asbates).

The first change I made was to remove the logo from the navigation bar. I had no idea what I would put there so I decided to not have it. This was done by going to the `/layouts/partials/nav.html` file and removing the portion corresponding to the logo:

```html
<nav class="nav">
  <!-- remove logo
  <a href="{{ "/" | relURL }}" class="nav-logo">
    <img src="{{ print "images/" .Site.Params.logo.url | relURL }}"
         width="{{ .Site.Params.logo.width }}"
         height="{{ .Site.Params.logo.height }}"
         alt="{{ .Site.Params.logo.alt }}">
  </a> --> 

  <ul class="nav-links">
    {{ range .Site.Menus.main }}
    <li><a href="{{ .URL }}">{{ .Name }}</a></li>
    {{ end }}
  </ul>
</nav>
```
I also removed the RSS feed link in the `footer.html` file in the same directory. I liked how there was a reference to Hugo in the footer but I also wanted to give credit to blogdown so I found a [blogdown logo](https://yihui.name/en/2017/10/the-blogdown-logo/), copied the code in `footer.html` corresponding to the Hugo reference, and edited it to add the blogdown logo:
```html
      <footer class="footer">
        <ul class="footer-links">
          <!-- remove RSS
          <li>
            <a href="{{ .Site.RSSLink | relURL }}" type="application/rss+xml" target="_blank">RSS feed</a>
          </li> -->
          <li>
            <a href="https://gohugo.io/" class="footer-links-kudos">Made with <img src="{{ "images/hugo-logo.png" | relURL }}" width="22" height="22"></a>
            
            <!-- add blogdown logo --> 
            <a href="https://bookdown.org/yihui/blogdown/" class="footer-links-kudos">Via <img src="{{ "images/blogdown-logo.png" | relURL }}" width="22" height="22"></a>
          </li>
          
        </ul>
      </footer>

    </div>
    {{ partial "footer_highlightjs" . }}
    {{ partial "footer_mathjax" . }}
    {{ template "_internal/google_analytics.html" . }}
  </body>
</html>
```
Note that the image is in the `/static/images` folder.

Changing the color scheme was fairly easy. I did a Google search for 'css colors', found one I liked, and changed the relevant portions in the `/static/css/main.css` file. For example, the color for headers is defined within the first few lines of the file. I changed color to `#00CED1`:

```css
html,
body {
  margin: 0;
  padding: 0;
  position: relative;
}

body {
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -moz-font-feature-settings: "liga" on;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  color: #00CED1; /* my change */
}
```

The last thing I did was to add pages and links to the navigation bar. This was done in the `config.toml` file. For example, I added a projects page to describe some of my current/previous projects:

```toml
[[menu.main]]
    name = "Projects"
    url = "/projects/"
```
After creating the link in `config.toml`, I added the `projects.md` to the `/content` folder.

I did make a few more changes but the ones I discussed here should give you an idea of how you can customize your own site. Again, it might be helpful to go [here](https://github.com/asbates/asbates) and see the changes for yourself by looking at the files and folders I mentioned. I hope after reading this you see that it's not too difficult to customize a blogdown site even if you don't really know anything about `html` and `css`.



