+++
title = 'template customization 2'
date = 2024-10-12T20:11:01+07:00
draft = false
tags = ['bug2', 'hugo', 'css']
authors = ['viridi']
url = '24j17'
+++
Second theme customization of a new Hugo site following initial setting.

<!--more-->

Modification of `main.css` and `hugo.toml` files are given here to complement previous post with title [template customization 1](../24j15). 

1. Modify `hugo.toml` as follow.
    ```
    baseURL = 'https://dudung.github.io/bug2'
    languageCode = 'en-us'
    title = 'bug 2'
    theme = 'default'

    enableEmoji = true

    ignoreErrors = ['error-missing-instagram-accesstoken']

    [taxonomies]
      author = "authors"
      tag = "tags"
      category = "categories"

    [[menu.main]]
      name = 'Home'
      weight = 2
      identifier = 'home'
      url = '/'

    [[menu.main]]
      name = 'Tags'
      weight = 1
      identifier = 'tags'
      url = '/tags'
    ```
2. Modify `assets\css\main.css` as follow.
    ```
    body {
      color: #222;
      font-family: sans-serif;
      line-height: 1.5;
      margin: 1rem;
      max-width: 768px;
      text-align: justify;
    }

    header {
      border-bottom: 1px solid #222;
      margin-bottom: 1rem;
    }

    /* to overwrite header border-bottom style */
    .homepage-header {
      border-bottom: 0px solid #222;
    }

    footer {
      border-top: 1px solid #222;
      margin-top: 1rem;
    }

    a {
      color: #00e;
      text-decoration: none;
      text-align: left;
      word-wrap: break-word;
      word-break: break-word;
      word-break: break-all;
      overflow-wrap: break-word;
      -ms-word-break: break-all;
    }

    pre {
      padding: 1em;
    }

    ul.menu-item li {
      display: inline-block;
      margin: 5px;
    }

    nav > ul > li {
      display: inline;
      padding-left: 0.5em;
    }

    nav {
      text-align: right;
    }

    .author {
      font-size:110%;
    }
    .readingtimedate {
      color: #999;
    }

    .footnotes {
      border-top: 0px solid #222;
      > hr {
         display: none;
       }
      > ol > li:not(:first-child):not(:last-child) {
        margin: -1em 0;
      }
    }

    // footnote link
    a[href^="#fn:"],
    // Back to footnote link
    a[href^="#fnref:"] {
      text-decoration: none;
      color: $orange;
      font-family: monospace;
    }
    a[href^="#fn:"]:before{ content: '[' }
    a[href^="#fn:"]:after{ content: ']' }


    div.tags {
      > ul > li {
        display: inline-block;
      }
      > ul > li:not(:last-child):after {
        content: ', ';
      }
      > ul {
        display: inline;
        border: 0px black solid;
        padding-left: 0px;
      }
    }

    /*
    ul.authors {
      > li {
        display: inline-block;
      }
      > li:not(:last-child):after {
        content: ', ';
      }
      display: inline;
      border: 0px black solid;
      padding-left: 0px;
    }
    */

    figure.authors {
      display: inline-block;
      border: 0px black solid;
      margin-left: 0px;
      > figcaption {
        border: 0px black solid;
        float: right;
        margin-left: 10px;
      }
    }

    .tocsec {
      display: inline;
      //margin-left: 10px;
      padding-left: 10px;
      //border-radius: 4px;
      //border-left: 2px solid green;
    }

    .tocseccol {
      color: #faa;
    }

    table {
      //width: 100%;
      border-collapse: collapse; /* Ensures there are no gaps between borders */
      border-spacing: 0; /* Removes any spacing between cells */
    }

    table th {
      border-top: 1px solid #000;
      border-bottom: 1px solid #000;
      padding: 8px;
      background-color: #f2f2f2;
    }

    table td {
      padding-right: 2em;
    }

    table tr:last-child td {
      border-bottom: 1px solid #000;
    }

    table tr:nth-child(odd) {
      background-color: #ffffff; /* White for even rows */
    }

    table tr:nth-child(even) {
      background-color: #f2f2f2; /* Light gray for odd rows */
    }
    ```

The CSS is from [bug](https://dudung.github.io/bug) and only slightly modified. Some comments and commented styles are still there. Following additional part

```css
nav > ul > li {
  display: inline;
  padding-left: 0.5em;
}

nav {
  text-align: right;
}
```

is for menu, Tags and Home, on the right top of each page.