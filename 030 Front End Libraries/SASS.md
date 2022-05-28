# SASS

Sass, or "Syntactically Awesome StyleSheets", is a language extension of CSS. It adds features that aren't available in basic CSS, which make it easier for you to simplify and maintain the style sheets for your projects.

### Sass Variables

One feature of Sass that's different than CSS is it uses variables. They are declared and set to store data.

In Sass, variables start with a `$` followed by the variable name.

```css

$main-fonts: Arial, sans-serif;
$headings-color: green;

/*And to use the variables: */

h1 {
  font-family: $main-fonts;
  color: $headings-color;
}
```
One example where variables are useful is when a number of elements need to be the same color. If that color is changed, the only place to edit the code is the variable value.

### Nest CSS with Sass

Sass allows nesting of CSS rules, which is a useful way of organizing a style sheet.

For a large project, the CSS file will have many lines and rules. This is where nesting can help organize your code by placing **child** style rules within the respective **parent** elements:

```html

<style type='text/sass'>

<!--   h1 and p are children of .blog post -->
  
  .blog-post { 
    h1 {
     text-align: center;
     color: blue;
    }
    p {
        font-size: 20px;
    } 
  }  
</style>
```

Another example:

```css
nav {
  background-color: red;
}

nav ul {
  list-style: none;
}

nav ul li {
  display: inline-block;
}

/*can be nested like below:*/

nav {
  background-color: red;

  ul {
    list-style: none;

    li {
      display: inline-block;
    }
  }
}
```

### Create Reusable CSS with Mixins












































