# Bootstrap v5.1


> [Bootstrap documentation](https://getbootstrap.com/docs/5.1/getting-started/introduction/)
> 
> [fontawesome: icon gallery](https://fontawesome.com/)
> 
> [test for mobile-friendly](https://search.google.com/test/mobile-friendly)

> BootStap Examples
> - [Bootstrap examples](https://getbootstrap.com/docs/5.1/examples/)
> - [Bootsnip: Bootstrap elements gallery](https://bootsnipp.com) 
> - [BOOTSTRAPMADE: Bootstrap templates](https://bootstrapmade.com/)
> - [Creative Tim: Bootstrap Theme](https://www.creative-tim.com/bootstrap-themes/free)


## WireFrame - Step 1 of Web Design

- wireframe vs. mockup

  - Before writing any codes, we should get buy-in on the design and be able to iterate through your design process
  - wireframe is a low fidelity representation of your design, it meant to be fast to produce and a sketch of the basics(layout and structure) of your design
  - Mock-up is a high fidelity representation of your design, what you see is what you will get, in terms of detailed color,img, icon design.

> - first, take a look at other people's website for inspiration - eg.[awwwards](https://www.awwwards.com/websites/com/)
> - then, look at the [UI patterns](https://ui-patterns.com/patterns) to see what problems you are trying to solve.
> - anther great resource of other web designer's portfolio is [dribble](https://dribbble.com/search/website) and you can search by color
> - sketch online use [balsamiq](https://balsamiq.com/wireframes/)
> - or wireframe use pencil and paper and download template from [sneakpeekit](https://sneakpeekit.com)

## Use Bootsrap

- use Bootstrap for basic layout and structure design, then use css for fine-tuning and detailed design
- ie. in html, Boostrap sytlesheet should be above css stylesheet


```js
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
```

## Bootstrap elements

- Buttons
- Nav Bar
- Carasoul
- Grid
- Container
- Card
- etc...


## Responsiveness

- Responsiveness means how website present itself on different devices
- All bootstrap elements have basic responsiveness design
- For detailed responsiveness design, use css media query

#### CSS Media Query

- `@mdeia` to allow dynamic representation on vairous screen size


## Code Refactor

- CSS selector

  - `h1, .id {}` : `h1` element and elements with class name `id` have the same styles specified (multiple selector use `,`)
  - `h1 .id {}`: elements that within `h1` that has class name `id`, a parent child relationship
  - `h1.id {}`: a `h1` element that has class name `id`, if doesn't exist will raise an error.


- CSS selector ord of execution

  - id will overwrite class, class will overwrite html element
  - css in-line will overwrite external css, but should not be used (not best practice)


- Code Refactoring (from most important to least important)

  1. **Readability** - if other developer can easily understand your codes :**orgnize your code, clean your code, add necessary comments**

  2. Modulity - whether codes are reusable
  3. Efficiency - whether codes can run faster than other
  4. Length - whether shorter codes can achieve the same outcome







