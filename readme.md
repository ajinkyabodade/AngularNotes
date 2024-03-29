<h1>Angular Notes By Ajinkya</h1>

If you are a new web developer, then remember web development is not a one-day/one framework thing. It’s a field that you learn gradually like art (painting, singing) and things also change rapidly as well. 

Angular presents you not only the tools but also the design patterns to build your project in a maintainable way. 

Angular is JavaScript framework that allow to create modern Single page application. 

<h2>Lets get started by installing the following:</h2>

-Node

-npm [Node Package Manager]

-Angular CLI

-IDE

<h2>Create and Run new App</h2>
To create new app (boiler plate), go to terminal and reach your desired folder and enter the following command. 

```
ng new <Enter your app name>
```
The ng new command prompts you for information about features to include in the initial app project. Accept the defaults by pressing the Enter or Return key.

Now to make it run enter the following command
```
cd dribbler
﻿ng serve --open
```
 This command will start the app and open in the output in a browser.  Short notation for --open is -o

<h2> Getting Started</h2>
To make changes to the app, we will work on src/app  folder mostly.

 It contains 2 types of files

 1.App Component

 2.App Module
 
 Consider App Component as a building blocks of your app.  It is defined with an HTML template, CSS stylesheet, and a unit test. Now only root component is present.  As the application evolves, root will become a tree of nested components.

 App Component consists of following files

 -app.component.ts the component class code, written in TypeScript 

 -app.component.html contains the template html code

 -app.component.css  contains the stylesheet for the component

 -app.component.spec.ts contains unit test written in TypeScript

 Module defines how to assemble the application. Now the code base contains only root module. 

 Initially it contains only declaration for AppComponent and later more components will be added.

<h2> Change Title Name</h2>
Lets change the title of the app first. Go to component class code app.component.ts  and change the title

```
export class AppComponent {
 title = 'Dribbler';
}
```

To see the changes write the following code in app.component.html

```
<div style="text-align:center">
 <h1>
  {{title}}
 </h1>
</div>
```
Note {{title}}   with a {{..}} notation, is used to data bind title defined in AppComponent class(app.component.ts)

<h2> Create and Run New Component</h2>
Type the below code in terminal (at your application folder)

```
ng generate component component_name
```

Ex:

```
ng generate component players
```

The CLI creates a new folder, src/app/players and generates the three files of the players.
The  PlayersComponent class (players.component.ts) code looks like below:

```
﻿import { Component, OnInit } from '@angular/core';
@Component({
  selector: 'html-input',
  templateUrl: './html-input.component.html',
  styleUrls: ['./html-input.component.css']
})
export class htmlInputComponent implements OnInit {
 constructor() { }
 ngOnInit() {
 }
}
```

The  PlayersComponent @Component contains three meta data as follows:

1.selector— the component's CSS element selector

2.templateUrl— the location of the component's template file.

3.styleUrls— the location of the component's private CSS styles.

Now that, htmlInput component is created, how to link this component in the root component ?

Insert this component using selector html-input  inside AppComponent template (app.component.html)

```
<html-input></html-input>
```

Also Import htmlInput Component in app.module.ts


<h2> Interpolation / Binding</h2>
Interpolation allows you to incorporate calculated strings into the text between HTML element tags and within attribute assignments. Template expressions are what you use to calculate those strings.

The interpolation live example / download example demonstrates all of the syntax and code snippets described in this section.

```
Welcome {{name}}            //Where name is variable name in component 

{{2+2}}			       //Possible And gives answer as 4

{{"Welcome " + name}}        //tring Concatination

{{name.length})              //Basic attribute

{{name.toUpperCase()}}       // Basic funtions/filters

{{greetUser()}}              //Calling function present in Component

{{windown.href.loaction()}}   //Not allowed
```


<h2> Interpolation vs Property Binding </h2>

DOM is basically collection of objects (window,html,body, head and etc) which allows us to manipulate it. It means that HTML elements are contained in the DOM as objects.HTML elements have attributes which initilizes DOM properties.Once initilization process is done attributes job is done.

```
<input type=”text” value="5">
```

Given input element has type and value attributes.When HTML element is created its properties which have similar names to attributes (but not same thing) is created, too.After initilization given input element have properties such as type and 
value.Note that there is important difference between property and attribute:

— -Attribute value does not change: Change value of input element into 10.

Run getAttribute('value') for our input element.Result will be 5.

— -Properties does change. Change value of input element into 10. 

Run getElementByTagName('input').value

 for our input element.Result will be 10.

For a given DOM node object, properties are the properties of that object, and attributes are the elements of the attributes property of that object.

There are several methods to bind data in Angular:

Interpolation: Lets assume we have created “imagePath” variable in our class. 

We can bind this value to src property of img element:
```
<img src=”{{imagePath}}”>
```

If we want to add some action and do something like:
```
<img src=”image.google.com/{{imagePath}}”>
```

It still will work with interpolation

Property Binding: Lets assume we want assign if button is disabled or not and we have got isDisabled variable in our class:
```
<button [disabled]=’isDisabled’>Click</button>
```

If we want to assign non string value to the property we need to use property binding.

Attribute Binding:Normally Angular recommends to use property binding but if there is not any corresponding property to attribute (for example ‘colspan’).

Lets assume we have got colSpan variable in our class:
```
<th colspan=’{{colSpan}}’> — ->Result will be error.To bind attribute
<th attr.colspan=’{{colSpan}}’> OR → <th [attr.colspan]=’colSpan’>No Error
```

Two Way Data Binding: Lets assume we have got name=’Vader’ in our class.== 
```
<input [value]=”name” (input)=’name=$event.target.value’>.
```

By this method we can create two way data binding or else we can use input [(ngModel)]=’name’>
(Source):(https://bit.ly/2kqMiL0)

<h2>Class Binding</h2>

It's easy to bind CSS classes to elements in your Angular templates. You provide a class name with class.className between brackets in your templates and then an expression on the right that should evaluate to true or false to determine if the class should be applied. Here's how you would bind a single and multiple class using NgClass for example:

```
@Component({
	selector: 'app-test',

	template: `
	<h2>Welcome {{name}} </h2> 
	<h2 class="text-success"> Ajinkya </h2> 
	<h2 [class]="successClass"> Ajinkya </h2>
	<h2 class="text-special" [class]="successClass"> Ajinkya </h2> 
	<h2 [class.text-danger]="hasError"> Ajinkya </h2>
	<h2 [ngclass]="messageClasses"> Ajinkya </h2>
	`,

	styles: [`
	.text-success {
		color: green;
	}
	.text-danger {
		color: red;
	}
	.text-special {
		font-style: italic;
	}
	`]
})

export class htmlInputComponent implements OnInit {

	public name = "Ajinkya";
	public successClass = "text-success"; 
	public hasError = false;
	public isSpecial = true; 
	public messageclasses = {
		"text-success": !this.hasError,
		"text-danger": this.has Error, 
		"text-special": this.isSpecial
	}

 constructor() { }
 ngOnInit() {
 }
}

```

From above code we have 5 examples as follows:

<h4>1</h4>

```
<h2 class="text-success"> Ajinkya </h2> 
```
In above example the text Ajinkya will simple turn to green as "text-success" class is applied to it directly.

<h4>2</h4>

```
<h2 [class]="successClass"> Ajinkya </h2>
```
In above example the text Ajinkya will turn to green as "successClass" property is binded to the html element.

<h4>3</h4>

```
<h2 class="text-special" [class]="successClass"> Ajinkya </h2> 
```
In above example the class "text-special" will be ovveride by the property "successClass", As the higher priority will be given to property binding and normal class will be discarded.
Therefore the color of the text Ajinkya will be greeen and it will not be Italic.


<h4>4</h4>

```
<h2 [class.text-danger]="hasError"> Ajinkya </h2>
```
Above example shows how we can apply a class based on the condition of an property.
Therefore the "text-danger" class will be applied to h2 tag when property "hasError" is true.

<h4>5</h4>

```
<h2 [ngclass]="messageClasses"> Ajinkya </h2>
```
Above example shows how to apply multiple classes with conditions using [ngClass] directive





<h2> Links To My profiles:</h2>

* [Linkedin](https://www.linkedin.com/in/ajinkya-bodade/)
* [Portfolio](https://ajinkyabodade.com/)

