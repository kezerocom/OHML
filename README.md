<h3>OHML <sup><a href="#">O</a>rion <a href="#">H</a>yperText <a href="#">M</a>arkdown <a href="#">L</a>anguage</sup></h3>


</br>

> ### Syntax

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

> ### Template

<sub>Template.ohml (OHML)</sub>

```cs
<%export(template):
  <html:
    <head:
      <title:
        <%virtual(title): default title>
      >
      <meta name="description" content="template description":>
      <link rel="stylesheet" href="styles.css":>
    >
    <body:
      <%virtual(body):
        <p class="message": it's default body>
      >
    >
  >
>
```

<sub>Page.ohml (OHML)</sub>

```cs
<%import(template):
  <%override(title): updated title>
  <%override(body):
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

<br>

> ### Bind Value

<sub>Page.ohml (OHML)</sub>

```cs
<%import(template):
  <%override(title): <%%(myTitle):>>
  <%override(body):
    <h1 class="title": <%%(myBodyTitle):>>
    <p class="message": <%%(myMessageText):>>
  >
>
```

<sub>PageRender.example (Any Language Supported)</sub>

```ts
// TypeScript example
import { OHML } from "ohml";

const ohmlData = {
  'myTitle': 'My Custom Title',
  'myBodyTitle': 'My Custom Body Title',
  'myMessageText' 'I am a message': 
}

const templateOhml = MagicClass.Load("template.ohml") as string;
const pageOhml = MagicClass.Load("page.ohml") as string;

const html = OTML.Render(ohmlData, pageOhml, [templateOhml, <others dependencies "strings", ...>]) as string;
```

-  <sup>PageRenderer.example (RESULT)</sup>
    ```html
    <!doctype html>
    <html>
      <head>
          <title>My Custom Title</title>
          <meta name="description" content="template description">
          <link rel="stylesheet" href="styles.css">
      </head>
      <body>
          <h1 class="title">My Custom Body Title</h1>
          <p class="message">I am a message</p>
      </body>
    </html>
    ```

> ### Loops and Basic condiction
> 
<sub>Page.ohml (OHML)</sub>

```cs
<%import(template):
  <%override(title): <%%(myTitle):>>
  <%override(body):
    <h1 class="title": <%%(myBodyTitle):>>

    <%comment( testing for loop to repeat 3x ):>
    <%for(int i = 0; i < 3; i++):
      <p class="message": <%%(myMessageText):> [ For LOOP <%%(i+1):>]>
    >

    <%comment( testing for foreach to repeat 3x ):>
    <%foreach(number in %range(1, 3)):
      <p class="message": <%%(myMessageText):> [ Foreach LOOP <%%(number-1):>]>
    >

    <%comment( title conditions ):>
    <%if(myTitle):
      <p class="message": myTitle exist>
    >
    <%else(myTitle):
      <p class="message": myTitle don't exist>
    >
  
    <%comment( sub title conditions ):>
    <%if(mySubTitle):
      <p class="message": mySubTitle exist>
    >
    <%else(mySubTitle):
      <p class="message": mySubTitle don't exist>
    >
    <%comment( other supports: ):>
    <%comment( 1 > 2 ):>
    <%comment( 1 < 2 ):>
    <%comment( 1 >= 2 ):>
    <%comment( 1 <= 2 ):>
    <%comment( 1 == 2 ):>
    <%comment( 1 != 2 ):>
    <%comment( %sizeof(ArrayOrStringCharIs) >= 1 ):>
  >
>
```

<sub>Page.html (HTML)</sub>

```html
<!doctype html>
<html>
  <head>
      <title>My Custom Title</title>
      <meta name="description" content="template description">
      <link rel="stylesheet" href="styles.css">
  </head>
  <body>
      <h1 class="title">My Custom Body Title</h1>
      <p class="message">I am a message [For LOOP 1]</p>
      <p class="message">I am a message [For LOOP 2]</p>
      <p class="message">I am a message [For LOOP 3]</p>
      <p class="message">I am a message [Foreach LOOP 1]</p>
      <p class="message">I am a message [Foreach LOOP 2]</p>
      <p class="message">I am a message [Foreach LOOP 3]</p>
      <p class="message">myTitle exist</p>
      <p class="message">mySubTitle don't exist</p>
  </body>
</html>
```
