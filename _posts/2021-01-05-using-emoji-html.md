---
title: How to use emojis on HTML
date: 2021-01-05 17:20:00 -0300
categories: [Programming, Web]
tags: [web, html, emoji, front-end, web-development]     # TAG names should always be lowercase
---
There are mainly two ways to display emojis on your web page, but first:

## HTML charset ##
---
To show the correct symbols, inform the web browser of the character set used on your page. Although the UFT-8 is the default character set, it's better to declare it explicitly to ensure the correct information is displayed.

So, in the HTML ```<head>``` tags, put:
```html
<meta charset="UTF-8>
```

## First mode: using the emoji Unicode ##
---
First, go to this [Unicode site page](https://unicode.org/emoji/charts/full-emoji-list.html) with the full emoji list. Find the emoji that you want to use. For example, I'll choose the smiley upside-down face. On the second column, you have the code for it. In this case, the code is **U+1F643**

![Image from unicode.org]({{ site.baseurl }}/images/html-emoji/unicode-table.png)
_Image from [unicode.org](https://unicode.org)_

Now replace the **U+** for **&#x**, adding and **;** at the end, and put it on your HTML code:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Lorem Ipsum</title>
  </head>
  <body> 
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
    <p>&#x1F643;</p>
  </body>
</html>
```

And the result will be:
![Page example]({{ site.baseurl }}/images/html-emoji/page-example.png)

## Second mode: copy and paste ##
---
Yes, exactly. You can copy and paste the emoji. Your code will be:
```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Lorem Ipsum</title>
  </head>
  <body> 
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>
    <p>🙃</p>
  </body>
</html>
```
And you will have the same result. But, be aware that it can result in some incompatibilities, **if you don't declare your charset on the ```<head>```**

That's it, I prefer the first mode, but both should work. Good luck with your coding!