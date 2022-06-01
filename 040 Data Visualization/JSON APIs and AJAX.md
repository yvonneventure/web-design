# JSON APIs and AJAX

APIs (Application Programming Interfaces) help programs interact with other programs. APIs are tools that computers use to communicate with one another, in part to send and receive data.

Programmers often use **AJAX (Asynchronous JavaScript and XML)** when working with APIs. AJAX refers to a group of technologies that make asynchronous requests to a server to transfer data, then load any returned data into the page. And the data transferred between the browser and server is often in a format called **JSON (JavaScript Object Notation)**.

### Handle Click Events with JavaScript using the onclick property

You want your code to execute only once your page has finished loading. For that purpose, you can attach a JavaScript event to the document called `DOMContentLoaded`. 

You can implement event handlers that go inside of the `DOMContentLoaded` function. You can implement an `onclick` event handler which triggers when the user clicks on the element with id `getMessage`.

```html
<script>
  document.addEventListener('DOMContentLoaded', function(){

    // within the function, added below
  // onece button clicked, the console will log "clicked"

document.getElementById('getMessage').onclick = function(){

  console.log("clicked");

}
  });

</script>
<h1>Cat Photo Finder</h1>
<p class="message box">
  The message will go here
</p>
<p>
  <button id="getMessage">
    Get Message
  </button>
</p>
```

### Change Text with click Events

When the click event happens, you can use JavaScript to update an HTML element.

```html

<script>
  document.addEventListener('DOMContentLoaded', function(){
    document.getElementById('getMessage').onclick = function(){
  
      // when a user clicks the Get Message button, it changes the text of the element with the class message to say Here is the message
  
document.getElementsByClassName("message")[0].textContent = "Here is the message"

    }
  });
</script>
```

### Get JSON with the JavaScript XMLHttpRequest Method

JSON syntax looks very similar to JavaScript object literal notation. JSON has object properties and their current values, sandwiched between a `{` and a `}`. These properties and their values are often referred to as "key-value pairs".

However, JSON transmitted by APIs are sent as `bytes`, and your application receives it as a `string`. These can be converted into JavaScript objects, but they are not JavaScript objects by default. 

The `JSON.parse` method parses the string and constructs the JavaScript object described by it.

```

Here's the code you can put in your click event to do this:

```html

<script>
  document.addEventListener('DOMContentLoaded',function(){
    document.getElementById('getMessage').onclick=function(){
      // Requst code within your onclick event
      const req = new XMLHttpRequest();
      req.open('GET', '/json/cats.json', true);
      req.send();
      req.onload = function(){
        const json=JSON.parse(req.responseText);
        document.getElementsByClassName('message')[0].innerHTML = JSON.stringify(json)
      }
     
    };
  });
</script>
```

Here's a review of what each piece is doing. 

1. First, an instance of the `XMLHttpRequest` object is created and saved in the `req` variable. 

2. Next, the `open` method initializes a request - this example is requesting data from an API, therefore is a `GET` request. The second argument for open is the `URL` of the API you are requesting data from. The third argument is a Boolean value where `true` makes it an asynchronous request.

3. The send method sends the request. 

4. Finally, the `onload` event handler parses the returned data and applies the `JSON.stringify` method to convert the JavaScript object into a string. This string is then inserted as the message text.

### Get JSON with the JavaScript `fetch` method

Another way to request external data is to use the JavaScript `fetch()` method. It is equivalent to `XMLHttpRequest`, but the syntax is considered easier to understand.

```js
fetch('/json/cats.json')
	.then(response => response.json())
	.then(data => {
		document.getElementById('message').innerHTML = JSON.stringify(data);
	})

```

The first line is the one that makes the request. So, `fetch(URL)` makes a `GET` request to the URL specified. The method returns a Promise.

After a Promise is returned, if the request was successful, the `then` method is executed, which takes the response and converts it to JSON format.

The `then` method also returns a Promise, which is handled by the next `then` method. The argument in the second `then` is the JSON object you are looking for!

Now, it selects the element that will receive the data by using `document.getElementById()`. Then it modifies the HTML code of the element by inserting a string created from the JSON object returned from the request.

### Convert JSON Data to HTML

Here is some example JSON:

```
[
  {
    "id":0,
      "imageLink":"https://funny-cat.jpg",
      "altText":"A white cat wearing a green helmet shaped melon on its head. ",
      "codeNames":[ "Juggernaut", "Mrs. Wallace", "Buttercup"
    ]
  }
]
```

You can use a `forEach` method to loop through the data since the cat photo objects are held in an `array`. As you get to each item, you can modify the HTML elements.

First, declare an html variable with `let html = "";`.

Then, loop through the JSON, adding HTML to the variable that wraps the key names in `strong` tags, followed by the value. When the loop is finished, you render it.

```html
<script >
  document.addEventListener('DOMContentLoaded', function() {
    document.getElementById('getMessage').onclick = function() {
      req = new XMLHttpRequest();
      req.open("GET", '/json/cats.json', true);
      req.send();
      req.onload = function() {
        json = JSON.parse(req.responseText);
        let html = "";
  
  // pre-filter the data you want
        json = json.filter(function(val) {
          return (val.id !== 1);
        });
  
        // Convert json data to html

        json.forEach(function(val) {

          // Adding each object keys
          const keys = Object.keys(val);
  
          // Generating new html
          html += "<div class = 'cat'>"; 
        
        //render images
        html += "<img src = '" + val.imageLink + "' " + "alt='" + val.altText + "'>";
  
          // Adding the custom html to each key
          keys.map(function(key) {

            html += "<strong>" + key + "</strong>: " + val[key] + "<br>";

          });

          html += "</div><br>";

        });

        
        document.getElementsByClassName('message')[0].innerHTML = html;
      };
    };
  });
</script>
```

### Get Geolocation Data to Find A User's GPS Coordinates

Every browser has a built in navigator that can give you information of your user's current location.The navigator will get the user's current longitude and latitude.

You will see a prompt to allow or block this site from knowing your current location. The challenge can be completed either way, as long as the code is correct.

By selecting allow, you will see the text on the output phone change to your latitude and longitude.

Here's code that does this:

```js
if (navigator.geolocation){
  navigator.geolocation.getCurrentPosition(function(position) {
    document.getElementById('data').innerHTML="latitude: " + position.coords.latitude + "<br>longitude: " + position.coords.longitude;
  });
}
```

First, it checks if the `navigator.geolocation` object exists. If it does, the `getCurrentPosition` method on that object is called, which initiates an asynchronous request for the user's position. If the request is successful, the callback function in the method runs. This function accesses the `position` object's values for latitude and longitude using dot notation and updates the HTML.

### Post Data with the JavaScript XMLHttpRequest Method

You can also send data to an external resource, as long as that resource supports AJAX requests and you know the URL. JavaScript's `XMLHttpRequest` method is also used to post data to a server. Here's an example:

```html
<script>
  document.addEventListener('DOMContentLoaded', function(){
    document.getElementById('sendMessage').onclick = function(){

      const userName = document.getElementById('name').value;
      const url = 'https://posts';

  //---------------------------POST Request---------------
const xhr = new XMLHttpRequest();
xhr.open('POST', url, true);
xhr.setRequestHeader('Content-Type', 'application/json; charset=UTF-8');
xhr.onreadystatechange = function () {
  if (xhr.readyState === 4 && xhr.status === 201){
    const serverResponse = JSON.parse(xhr.response);
    document.getElementsByClassName('message')[0].textContent = serverResponse.userName + serverResponse.suffix;
  }
};
const body = JSON.stringify({ userName: userName, suffix: ' loves cats!' });
xhr.send(body);
    };
  });
</script>
```

 Here the `open` method initializes the request as a `POST` to the given URL of the external resource, and uses the `true` Boolean to make it asynchronous. The `setRequestHeader` method sets the value of an HTTP request header, which contains information about the sender and the request. It must be called after the `open` method, but before the `send` method. The two parameters are the name of the header and the value to set as the body of that header.
 
 Next, the `onreadystatechange` event listener handles a change in the state of the request. A `readyState` of `4` means the operation is complete, and a `status` of `201` means it was a successful request. The document's HTML can be updated. 
 
 Finally, the `send` method sends the request with the `body` value, which the `userName` key was given by the user in the input field.






































