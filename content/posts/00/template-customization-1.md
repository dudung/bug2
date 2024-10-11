+++
title = 'template customization 1'
date = 2024-10-11T21:03:19+07:00
draft = false
tags = ['hugo']
authors = ['viridi']
url = '0001'
+++
First theme customization of a new Hugo site following initial setting.

<!--more-->

In previous post with title [first post again](../0000) customization is only in `layouts/partials/footer.html`. Here more customizations in various files are given.

1. Create content of `layouts/posts/single.html` is as follow.
    ```
    {{ define "main" }}
      <h1>{{ .Title }}</h1>

      {{ $dateMachine := .Date | time.Format "2006-01-02T15:04:05-07:00" }}
      {{ $dateHuman := .Date | time.Format ":date_long" }}
      
      {{- range .Params.authors }}
        {{- with $.Site.GetPage "taxonomyTerm" (printf "authors/%s" (urlize .)) }}
          <figure class='authors'>
            <!--img src="{{ .Params.photo }}" alt=""/ -->
            <figcaption>
              <a href="{{ .Permalink }}">{{ .Params.name }}</a>
            </figcaption>
          </figure>
        {{ end }}
      {{ end }}
      
      <div class='readingtimedate'>
        {{ partial "reading-time.html" . }} &middot;
        <time datetime="{{ $dateMachine }}">{{ $dateHuman }}</time>
      </div>
      
      {{ .Content }}
      {{ partial "terms.html" (dict "taxonomy" "tags" "page" .) }}
      
      {{ partial "posts/math.html" . }}
    {{ end }}
    ```
2. Create content of `layouts/partials/reading-time.html` is as follow.
    ```
    {{ .ReadingTime }} min{{ if (ne .ReadingTime 1) }}s{{ end }} read
    ```
3. Create content of `layouts/partials/posts/math.html` is as follow.
    ```
    {{- if or (.Params.math) (.Site.Params.math) (.Params.katex) (.Site.Params.katex) -}}

      <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.css"
        integrity="sha384-vKruj+a13U8yHIkAyGgK1J3ArTLzrFGBbBc0tDp4ad/EyewESeXE/Iv67Aj8gKZ0" crossorigin="anonymous">
      {{/* The loading of KaTeX is deferred to speed up page rendering */}}
      <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/katex.min.js"
        integrity="sha384-PwRUT/YqbnEjkZO0zZxNqcxACrXe+j766U2amXcgMg5457rve2Y7I6ZJSm2A0mS4" crossorigin="anonymous"></script>

    <!--
    url https://github.com/KaTeX/KaTeX/tree/main/contrib/mhchem [20240412]
    -->
    <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.10/dist/contrib/mhchem.min.js" integrity="sha384-ifpG+NlgMq0kvOSGqGQxW1mJKpjjMDmZdpKGq3tbvD3WPhyshCEEYClriK/wRVU0"  crossorigin="anonymous"></script>
    <!-- -->    
        
      <script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.4/dist/contrib/auto-render.min.js"
        integrity="sha384-+VBxd3r6XgURycqtZ117nYw44OOcIax56Z4dCRWbxyPt0Koah1uHoK0o4+/RRE05" crossorigin="anonymous"
        onload="renderMathInElement(document.body,
          {
            delimiters: [
              {left: '$$', right: '$$', display:true},
              {left: '$', right: '$', display:false},
              {left: '\\(', right: '\\)', display: false},
              {left: '\\[', right: '\\]', display: true}
            ]
          }
        );"></script>
    {{- end -}}
    ```
4. Create content of `layouts/_default/baseof.html` is as follow.
    ```
    <!DOCTYPE html>
    <html lang="{{ or site.Language.LanguageCode site.Language.Lang }}" dir="{{ or site.Language.LanguageDirection `ltr` }}">
    <head>
      {{ partial "head.html" . }}
    </head>
    <body>
      <header>
        {{ partial "header.html" . }}
        
        {{ if .HasShortcode "blank/scatter" }}
          {{ partial "script/inner.html" . }}
          {{ partial "script/chartjs.html" . }}
        {{ end }}

        {{ if .HasShortcode "blank/svgpath" }}
          {{ partial "script/inner.html" . }}
        {{ end }}
      </header>
      <main>
        {{ block "main" . }}{{ end }}
      </main>
      <footer>
        {{ partial "footer.html" . }}
      </footer>

      <!-- 20240111 support for Mermaid from Hugo Coder  -->
      {{ if .HasShortcode "mermaid" }}
      <script src="https://cdn.jsdelivr.net/npm/mermaid@9.3.0/dist/mermaid.min.js"
        integrity="sha256-QdTG1YTLLTwD3b95jLqFxpQX9uYuJMNAtVZgwKX4oYU=" crossorigin="anonymous"></script>
      <script>
        mermaid.initialize({ startOnLoad: true });
      </script>
      {{ end }}
    </body>
    </html>
    ```
