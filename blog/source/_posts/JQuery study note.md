# jQuery study note

## What's jQuery?

* jQuery is a library for JavaScript, which significantly simplified coding for JS.
* jQuery includes lots of functions, including: 
  1. Selecting HTML elements
  2. Operating HTML elements
  3. Operating CSS
  4. Event handler functions
  5. Special effect and animation for JS
  6. HTML DOM traverse and revise
  7. AJAX
  8. Utilities
* jQuery is an open-source framework.

## jQuery CDN

1.  baidu: `https//apps.bdimg.com/libs/jQuery/2.1.4/jquery.min.js`
2. google: `https//ajax.googleapis.com/ajax/libs/jQuery/1.10.2/jquery.min.js`

## Fundamental grammar

```js
$(document).ready(function(){
	//jQuery code
});

// another form
$(function(){
    //jQuery code
})
```

> codes above display the Starting function of jQuery

## jQuery events

* ```js
  $("p").click(function(){
  	//code after the event happened
  })
  ```

  > `click` is a typical event of jQuery; function is executed after user clicked the mouse.

* other popular events

  1. dblclick(): double click the mouse
  2. mouseenter(): mouse moving over the element
  3. mouseleave(): mouse leaving the element
  4. hover(): combining event 2 & 3
  5. mouseup(),mousedown():pressing mouse and releasing mouse
  6.  focus(),blur(): when elements acquire/lose focus

## jQuery function

* ```js
  $("p").hide(speed,callback) /show(speed,callback)
  ```

  hiding/showing HTML elements.

  param: 

  > speed: hide/show speed; using 'fast', 'slow' or ms
  >
  > callback: callback executed after the function

  

* ```js
  $("p").toggle(speed,callback)
  ```

  switching between hide() and show().

  

* ```js
  $("div").fadeIn(speed,callback) / fadeOut(speed,callback)
  ```

  elements fading in / fading out.

  

* ```js
  $("div").fadeToggle(speed,callback)
  ```

  switching between fadeIn() and fadeOut().

  

* ```js
  $("div").fadeTo(speed,opacity,callback)
  ```

  appointing the opacity after fading.

  

* ```js
  $("div").slideUp(speed,callback) / slideDown(speed,callback)
  ```

  sliding the element up / down.

  

* ```js
  $("div").slideToggle(speed,callback)
  ```

  switching between slideUp() and slideDown().

  

* jQuery animate()

  ```js
  //After clicking the mouse, the div element moving 250px to the right
  $("button").click(function(){
  	$("div").animate({left: '250px'});
  });
  
  //With multiple attributes
  $("button").click(function(){
  	$("div").animate({
          left: '250px',
          opacity:'0.5',
          height: '150px'
          width: '150px'
      });
  });
  
  //Using relative values
  $("button").click(function(){
  	$("div").animate({
          width: '+=100px',
          height: '+=100px'
      });
  });
  
  //Using the param 'speed'
  $("button").click(function(){
  	$("div").animate({left: '250px'},"slow");
  });
  ```

  

* ```js
  $("div").stop(stopAll,goToEnd)
  ```

  Stopping the effects and animation.

  param:

  > stopAll: weather stopping all animation in queue or not. Default: false
  >
  > goToEnd: weather completing the animation immediately or not. Default: false



## jQuery chaining

This feature allows users to operate multiple function for single elements without querying many times.

e.g.  

```js
$("div").slideUp(2000).slideDown(2000)
//sliding up the element first, then sliding down the element
```



## jQuery DOM operation

* text() : Setting or return the text of selected element

* html() : Setting or return the text(including HTML label) of selected element

* val() : Acquiring the value of input

  e.g.

  ```html
  <input type ="text" id="one" value="Hello">
  
  <script>
  	$("#one").val(); //return "Hello"
  </script>
  ```

* attr() : Acquiring or setting the attributes of certain elements

  ```html
  <a href="www.google.com" class="search"></a>
  
  <!-- JS code -->
  <script>
      $(".search").attr("href") //return "www.google.com"
      $(".search").attr("href","www.baidu.com") //change 'href' to 'www.baidu.com'
  </script>
  ```

* callback function for `text(), html(), val() and attr()`

  ```html
  <p id="first">
      Hello World!
  </p>
  <p id="second">
      GoodBye World!
  </p>
  
  <script>
      $("#first").click(function(){
          $("#first").text(function(i,oriText){
              return `This is new p${i}, ${oriText} lol!`;
          });
      });
      // After clicked on the first 'p' label, text of it turned into 'This is new p0, Hello World! lol!'
  </script>
  ```

  

* Adding elements

  1. append() / prepend()

     ```js
     $("p").append("adding text at the end of the element(still inside the element)");
     
     $("p").prepend("adding text at the beginning of the element(still inside the element)");
     
     //Attention: Both function can add multiple text by using multiple param
     ```

  2. after() / before()

     ```js
     $("p").after("adding text after the element(outside the element)");
     
     $("p").before("adding text before the element(outside the element)");
     
     //Attention: Both function can add multiple text by using multiple param
     ```

* Deleting elements

  1. remove()

     ```js
     $("div").remove();
     //Deleting selected element and its children elements
     
     $("div").remove(".one")
     //Only operating on 'div' with class 'one'
     ```

  2. empty()

     ```js
     $("div").empty();
     //Deleting children elements of selected element(without selected element)
     ```



## jQuery CSS

1. Operating on class of CSS

   * addClass() / removeClass()

     ```js
     $("p").addClass("big long");
     //Adding class 'big' and 'long'
     
     $("p").removeClass("big long");
     //Aremoving class 'big' and 'long'
     ```

   * toggleClass()

     Switching between `addClass()` and `removeClass()`

2. css()

   ```js
   $("p").css("color");
   // return value of selected attribute
   
   $("p").css("color","white");
   // setting value of selected attribute
   
   $("p").css("color":"white","font-size":"14px");
   // setting multiple value of selected attribute
   ```

3. Sizing

   * width() / height()

     > exclude padding, border and margin

   * innerWidth() / innerHeight()

     > exclude border and margin

   * outerWidth() / outerHeight()

     > exclude margin

   * outerWidth(true) / outerHeight(true)

     > include padding, border and margin



## jQuery Traverse

1. Ancestor

   * parent() / parents()

     ```js
     $("p").parent();
     //return father element of 'p'
     
     $("p").parents();
     //return all ancestor element of 'p'
     
     $("p").parents("div");
     //return all ancestor 'div' element of 'p'
     ```

   * parentsUntil()

     ```js
     $("p").parentsUntil("div");
     //return elements between label 'p' and 'div'
     ```

2. Offspring

   * children()

     Return children elements of selected label.

   * find()

     Return all offspring elements of selected label.

3. Siblings

   * siblings()

     Return all siblings elements of selected label.

   * next() / nextAll()

     ```js
     $("p").next();
     //return the next siblings element of 'p'
     
     $("p").nextAll();
     //return all siblings elements following 'p'
     ```

   * nextUntil()

     ```js
     $("p").nextUntil("h2");
     //return all siblings elements between label 'p' and 'h2'
     ```

   > prev(), prevAll() & prevUntil() are similar to functions above, only with reverse direction

4. Filter

   ```js
   $("div p").first();
   //select the first 'p' of first 'div'
   
   $("div p").last();
   //select the last 'p' of last 'div'
   
   $("p").eq(1);
   //select element by index(starting from 0)
   
   $("p").filter(".good");
   //select 'p' element with class 'good'
   
   $("p").not(".good");
   //select 'p' element without class 'good'
   ```




## jQuery AJAX

1. load()

   `load()` can load data from servers, and put the data into selected element.

   e.g. This is the content of a 'txt' file 'demo.txt':

   ```html
   <p id="first">Hello my world</p>
   <p id="second">GoodBye world</p>
   ```

   ```html
   <div id="one">
       <span>origin</span>
   </div>
   
   <script>
       $("#one").load("demo.txt"); // After executed, 'span' will be replaced by both 'p' in 'demo.txt'
       $("#one").load("demo.txt #first"); // After executed, 'span' will be replaced by 'p' with id 'first' in 'demo.txt'
       $("#one").load("demo_.txt",function(responseTxt,statusTxt,xhr){
       if(statusTxt=="success")
         alert("外部内容加载成功!");
       if(statusTxt=="error")
         alert("Error: "+xhr.status+": "+xhr.statusText);
     }); // callback function is also available
   </script>
   ```

2. $.get(URL,function(data,status))

   > First param: request URL
   >
   > Second param: callback function; first param refers to content of request page, second param refers to request status

3. $.post(URL,data,function(data,status))

   >First param: request URL
   >
   >Second param: data request to send
   >
   >Third param: callback function; first param refers to content of request page, second param refers to request status