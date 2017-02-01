# Create your first HTML template for a web map application

Our first web map application will contain a map div and a button. When clicking on second, the background color from the first would change from dark blue to red.

1. Go to [Plunker](https://plnkr.co/)
2. Sign in with GitHub
3. Edit the `README.md` file using Markdown syntax:
 
  * Add a header with something like this: "My first web map application".
  * Add a basic description. You can add links, bullet points and so on.

4. Edit the `index.html` file using HTML, CSS and JavaScript:

  * _Structure_ - HTML: 

    - add a title element within the <head> with something like "My first web map",
    - add jQuery library on a script element, you can use `"https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"` as the `src` attribute,
    - add a style element, you can specify the type of language, in this case CSS,
    - add a div element with the id of "map" within the <body>,
    - add a button element with the id of "red-button", you can add some text within the tags such as "Red",
    - add a script element, you can specify the type of language, in this case Javascript.

  * _Design_ - CSS: 

    - set `html`, `body` and `#map` selectors' background color and height to `#162945` (Navy Blue) and `100%`,
    - set `button` selector's position, top, left, width, background color and cursor to `absolute`, `20px`, `20px`, `50px`, `#f24440` (Location Red) and `pointer`

  * _Interactions_ - Javascript: 

    - add a global funcion called `main`,
    - within the `main` function create two variables, the first called `redButton`, and the second, `map` that gets the button and map elements (use jQuery!),
    - add `click` method to `redButton` variable, thus adding a anonymous function that triggers when clicking,
    - use jQuery to change the background color of the map variable to `#f24440` (you can use `console.log` to show some useful message).

You can check the solution [here](https://plnkr.co/edit/XqKsvc0JJMeTco1PBVf5?p=preview).
