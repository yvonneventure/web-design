# jQery

jQuery is one of the most widely used JavaScript libraries in the world.

jQuery simplified the process of writing client-side JavaScript, and also ensured that your code worked the same way in all browsers.


### `<script>` element

Your browser will run any JavaScript inside a `<script>` element, including jQuery.

❗️The important thing to know is that code you put inside this `function` will run as soon as your browser has loaded your page.

This is important because without your `document ready function`, your code may run before your HTML is rendered, which would cause bugs.

```html
<script>
  $(document).ready(function() {
  
  });
</script>
```

### Target HTML Elements with Selectors Using jQuery

All jQuery functions start with a `$`, jQuery often selects an HTML element with a selector, then does something to that element.

- `.addClass()`

```html
<script>
  $(document).ready(function() {
  
<!--  select <button> element in html, and add a class name "animated bounce" -->
  $("button").addClass("animated bounce");   
  
<!--   target element with class name -->
  $(".class-name").addClass("animated shake");
  
<!--   target element with id -->
  $("#id-name").addClass("animated fadeOut");
  
  });
</script>

- `.removeClass()`

```html
<!-- similar to addClass above -->

$("#id-name").removeClass("btn-default");

```













