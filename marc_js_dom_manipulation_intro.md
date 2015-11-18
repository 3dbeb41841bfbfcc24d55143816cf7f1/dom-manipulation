The DOM and the Web Browser
===========================

##Agenda
- Intro to DOM review
- Javascript vs the DOM vs the Web Browser
- Javascript for DOM manipulation
- Javascript for DOM tree transversal



<br>

[FEWD SLIDES](http://jrosebud.github.io/)

## Hook

Show them the [Kick-Ass](http://kickassapp.com/) to demo the DOM.

##Intro to the DOM

- Have a basic understanding of what the DOM is and how JavaScript interacts with it
- Access properties belonging to the document object
- Use document methods to access elements:

        getElementsByTagName
        getElementById
        getElementsByClassName
- Manipulate elements and styling using JavaScript 

<br>

## JavaScript vs the DOM

The **Document Object Model**, or DOM, is an application programming interface (API) for valid HTML that allows you to programmatically access and manipulate the contents of a web page (or document). It provides a structured, object-oriented representation of the individual elements and content in a page with methods for **retrieving** and **setting the properties** of those objects. It also provides methods for **adding** and **removing** such objects, allowing you to create dynamic content.

The DOM also provides an interface for dealing with events, **allowing you to capture and respond to user or browser actions**. 

In short, the DOM lets us do two things: 

- Manipulate the document, add, remove, retrieve, edit etc...
- Run code when things happen.

<br>

## Javascript vs the browser

 

JavaScript is not the same as the web browser. And the web browser is not the same as JavaScript. You can run your JavaScript code without a web browser. But it is a pain. 

Generally, we want to write stuff to run in the browser, (we use Chrome). 

<br>

##DOM Tree

![DOM Tree](http://www.webstepbook.com/supplements/slides/images/dom_tree.gif)



- Text nodes cannot have children. If an element contains text and another child element, the child element is not a child of the text node but rather a child of the containing element (em, li example).
- Attribute nodes are not children of the element that carries them, they are part of that element.

Activity (5 minutes):

**Draw a DOM Tree**

	<html>
		<head>
		  <title>Webpage</title>
		</head>		
		<body>		
			<div id="page">			
				<h1 id="header">List</h1>	
				<h2>Buy Groceries</h2>
				<ul>
					<li id="one" class="hot"><em>fresh</em> figs</li>
					<li id="two" class="hot">pine nuts</li>
					<li id="three" class="hot">honey</li>
					<li id="four">balsalmic vinegar</li>
				</ul>
				<script src="js/list.js"></script>
			</div>			
		</body>		
	</html>
	
	

###When is the DOM different than HTML?

If you have mistakes in your HTML, and the browser has fixed them for you.


If you have a table element and leave out the tbody (which is required). It'll exist in the DOM but not the HTML

<br>

##JavaScript can manipulate the DOM
[Pre-built Codepen.io](http://codepen.io/marcwright/pen/pJjPxq)

Imagine if you have an empty div element like this:

	<div id="container"></div>

Use JavaScript to change the #container value:

	<script>		
		var container = document.getElementById("container");
		container.innerHTML = "New Content";
		container.style.color = "red";
		container.setAttribute("class", "democlass");
	<script>
	
	<style>
		.democlass {
  			font-family: georgia;
  			font-size: 40px;
		}
	</style>
	
	or 
	
	document.getElementById("container").innerHTML = "New Content";


A variable may be good if you're reusing code. Which is different than your original HTML or what you would see in View Source!

<br>

##Traversing the DOM

JavaScript can change HTML


- Access properties belonging to the **document** object

```
document.body             // Returns the <body> element
document.URL              // Returns the complete URL of the document
document.lastModified     // Returns the date and time the document was updated

```

- Use document methods to access elements on [Atlanta Craigslist](http://atlanta.craigslist.org/)
	- getElementsByTagName
	- getElementById
	- getElementsByClassName
- If you're going to use an element more that once then use a variable. We use variables to save the location (or reference) of a DOM node. It's called 'caching'. It saves the browser from looking through the DOM tree to find the same element again.

####document.getElementsByTagName
```
var paragraphs = document.getElementsByTagName("p");
```

####document.getElementById
```
var topban = document.getElementById("topban");
```

####document.getElementsByClassName
```
var community = document.getElementsByClassName("community");
```

####Get the 'li' elements
```
document.getElementsByClassName('acitem')[0].getElementsByTagName('li')[0].innerHTML = "Changing  Albany"
```

####You can also use the method `item()`

```
document.getElementsByClassName('acitem').item(0).getElementsByTagName('li').item(0).innerHTML = "Changing  Albany"
```

- Manipulate elements and styling using JavaScript 

<br>

##Query Selectors
- gets the first of type: `document.querySelector('li')`
- gets all: `document.querySelectorAll('li')`
- To get the same result as above `document.querySelector('ul.acitem').querySelector('li').innerHTML = "Changing Albany"`

<br>

##Change innerHTML
```
document.getElementById('topban').innerHTML = "GA is hacking CL!";

var person = {name: "Marc"};

document.getElementById("topban").innerHTML = "Hello, " + person.name + " needs a futon!"

```

<br>

##Code Along - Change value of an attribute
[Pre-built starter codepen.io](http://codepen.io/marcwright/pen/waKdNj?editors=101)

Let's walk through some examples of using Javascript to change attributes of HTML elements.

```
#PICS - add a penguin gif to HTML:
<img id="penguin-image" src="http://i.imgur.com/WNUt75D.gif">

#Change it to Gerry's LI pic:
document.getElementById("penguin-image").src = "https://media.licdn.com/media/p/6/005/0aa/2f7/0f68cc4.jpg";

#LINKS - add a link to ESPN in HTML:

<a id="penguin-link" href="http://espn.go.com/">Here is a link</a>

#Change it to CL:

document.getElementById("penguin-link").href = "http://atlanta.craigslist.org/";
```

####Change styles of an element
```
document.getElementById("espn-link").style.color = "orange";
document.getElementById("espn-link").style.backgroundColor = "black";
document.getElementById("penguin-image").style.display = "block";
document.getElementById("penguin-image").style.padding = "40px";
```

<br>


##LAB #1 - JavaScript Jedi Academy

**Have the students pull the starter code from their repo**

Practice the things you learned today by modifying the Jedi Academy document in the console! (from LA lessons)

- Make the Luke and Obiwan lightsabers appear in the browser
`document.getElementById('luke').style.display= "block"`

- Change the text on the first 'p' tag
`document.getElementById("container").childNodes[3].innerHTML = “Changing text";`

- Change the color of the 'h1' 
`document.getElementById("container").childNodes[1].style.color = "red";`

- Change the length and/or color of a lightsaber (for Darth's saber):
`document.getElementsByClassName("blade")[0].style.width = "100px"`

or 

```
document.getElementsByClassName("blade")[0].setAttribute("id", "darth");

document.getElementById("darth").style.width = "700px"
```

- Change the font of a `p` tag

`document.getElementsByTagName("p")[0].style.fontFamily = "Impact,Charcoal,sans-serif";`

- Make Vader's handle blue.
`document.getElementById('vader').childNodes[1].style.backgroundColor = "blue"`


#####Note that you must get specific in most cases by calling an ID or getting a single instance of a class using an index.




<br>

##LAB #2

`js_dom_lab` starter code is in the classwork week7 folder. Show fully baked version first.

###Document.getElementById

- Create a paragraph with the words "Change me!"
- Use document.getElementById to change the paragraph's words to "I'm changed!"

###Document.getElementsByClassName
Name returns an array-like object of all child elements which have all of the given class name. 

Create 4 p tags with text inside each. When the button is clicked:

- p 1 - Change the text
- p 2 - Make the text bold
- p 3 - Make the text red
- p 4 - Add a 1px dashed blue border

###document.getElementsByTagName

Returns an HTMLCollection of elements with the given tag name. The complete document is searched, including the root node. 

The returned HTMLCollection is live, meaning that it updates itself automatically to stay in sync with the DOM tree without having to call

- Use getElementsByTagName to get the number of spans in the page

<br>

##LAB #3

Do the traffic light exercise. Show the fully baked version. Ask how many functions they think they'll need?

<br>