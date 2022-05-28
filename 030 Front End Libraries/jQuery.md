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



```html
<script>
  $(document).ready(function() {
  
<!--  select <button> element in html, and add a class name "animated bounce" -->
  $("button").addClass("animated bounce");   
  
<!--   target element with class name -->
  $(".class-name").addClass("animated shake");
  
<!--   target element with id -->
  $("#id-name").addClass("animated fadeOut");
  
  <!-- similar to addClass above, you can remove class -->

$("#id-name").removeClass("btn-default");
  
  });
</script>

```

### Change the CSS of an Element Using jQuery

This is slightly different from a normal CSS declaration, because the CSS property and its value are in quotes, and separated with a comma instead of a colon.

```html
<!-- change element with id "id"'s color to blue -->

$("#id").css("color", "blue");

```

### Disable an Element Using jQuery

You can also change the **non-CSS** properties of HTML elements with jQuery. 

jQuery has a function called `.prop()` that allows you to adjust the properties of elements.

```html

<!-- disable the button, it will become grayed-out and can no longer be clicked -->

$("button").prop("disabled", true);

```

### Change Text Inside an Element Using jQuery

Using jQuery, you can change the text between the start and end tags of an element. You can even change HTML markup.

jQuery has a function called .html() that lets you add HTML tags and text within an element. Any content previously within the element will be completely **replaced** with the content you provide using this function.

```html
<!-- h3 element will become <h3><em>jQuery Playground</em></h3>
 -->
$("h3").html("<em>jQuery Playground</em>");

```

jQuery also has a similar function called .text() that only alters text without adding tags. In other words, this function will not evaluate any HTML tags passed to it, but will instead treat it as the text you want to replace the existing content with.


### Remove an Element Using jQuery

jQuery has a function called .remove() that will remove an HTML element entirely.

```html
 $("#id").remove();
```

### Use `appendTo()` to Move Elements with jQuery

`appendTo()` allows you to select HTML elements and append them to another element. For example, move element from one `div` to another.

```html

<!-- move id1 element to after id2 -->
$("#id1").appendTo("#id2");
```

### Clone an Element Using jQuery

jQuery has a function called `clone()` that makes a copy of an element.

For example, if we wanted to copy `target2` from our `left-well` to our `right-well`, we would use:

```html
$("#target2").clone().appendTo("#right-well");
```

Did you notice this involves sticking two jQuery functions together? This is called ***function chaining*** and it's a convenient way to get things done with jQuery.

### Target the Parent of an Element Using jQuery

Every HTML element has a **parent** element from which it **inherits** properties.

For example, your `<h3>` element has the parent element of `<div class="container-fluid">`, which itself has the parent `<body>`.

jQuery has a function called `parent()` that allows you to access the parent of whichever element you've selected.

Here's an example of how you would use the `parent()` function if you wanted to give the parent element of the `left-well` element a background color of blue:

```html
$("#left-well").parent().css("background-color", "blue")
```

### Target the Children of an Element Using jQuery

When HTML elements are placed one level below another they are called children of that element. For example, the button elements in this challenge with the text `#target1`, `#target2`, and `#target3` are all children of the `<div class="well" id="left-well">` element.

jQuery has a function called `children()` that allows you to access the children of whichever element you've selected.

Here's an example of how you would use the `children()` function to give the children of your `left-well` element the color blue:

```html
$("#left-well").children().css("color", "blue")
```

### Target

#### Target nth child

jQuery uses CSS Selectors to target elements. The `target:nth-child(n)` CSS selector allows you to select all the nth elements with the target class or element type.

Here's how you would give the third element in each well the bounce class:

```html
$(".target:nth-child(3)").addClass("animated bounce");
```

#### Target Even/Odd Elements Using jQuery

You can also target elements based on their positions using `:odd` or `:even` selectors.

Note that jQuery is zero-indexed which means the first element in a selection has a position of 0. This can be a little confusing as, counter-intuitively, `:odd` selects the second element (position 1), fourth element (position 3), and so on.

Here's how you would target all the odd elements with class `target` and give them classes:

```html
$(".target:odd").addClass("animated shake");
```

### Use jQuery to Modify the Entire Page

jQuery can target the body element as well.

Here's how we would make the entire body fade out:

```html
$("body").addClass("animated fadeOut");

```


