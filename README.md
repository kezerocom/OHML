<h3>OHML <sup><a href="#">O</a>rion <a href="#">H</a>yperText <a href="#">M</a>arkdown <a href="#">L</a>anguage</sup></h3>


</br>

> #### Syntax

<sub>OHML</sub>

```cs
<html:
  <head:
    <title: hello world page>
    <meta name="description" content="hello world page description":>
    <link rel="stylesheet" href="styles.css":>
  >
  <body:
    <p class="message": hello world!>
  >
>
```

<sub>HTML</sub>

```html
<!doctype html>
<html>
    <head>
        <title>hello world page</title>
        <meta name="description" content="hello world page description">
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <p class="message">hello world!</p>
    </body>
</html>
```

<br>

> #### Template

<sub>Template.ohml (OHML)</sub>

```cs
<% export="template":>
<html:
  <head:
    <title:
      <% virtual="title": default title>
    >
    <meta name="description" content="template description":>
    <link rel="stylesheet" href="styles.css":>
  >
  <body:
    <% virtual="body":
      <p class="message": it's default body>
    >
  >
>
```

<sub>Page.ohml (OHML)</sub>

```cs
<% import="template":
  <% override="title": updated title>
  <% override="body":
    <h1 class="title": updated body>
    <p class="message": i'm override>
  >
>
```

<sub>Page.html (HTML)</sub>

```html
<!doctype html>
<html>
    <head>
        <title>updated title</title>
        <meta name="description" content="template description">
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <h1 class="title">updated body</h1>
        <p class="message">i'm override</p>
    </body>
</html>
```


