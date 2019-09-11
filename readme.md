# Angular Notes By Ajinkya

If you are a new web developer, then remember web development is not a one-day/one framework thing. It’s a field that you learn gradually like art (painting, singing) and things also change rapidly as well. 

Angular presents you not only the tools but also the design patterns to build your project in a maintainable way. 

Angular is JavaScript framework that allow to create modern Single page application. 

## Lets get started by installing the following:
-Node
-npm [Node Package Manager]
-Angular CLI
-IDE

## Create and Run new App
To create new app (boiler plate), go to terminal and reach your desired folder and enter the following command. 
```ng new <Enter your app name>```
The ng new command prompts you for information about features to include in the initial app project. Accept the defaults by pressing the Enter or Return key.

Now to make it run enter the following command
```
cd dribbler
﻿ng serve --open
```
 This command will start the app and open in the output in a browser.  Short notation for --open is -o

##Getting Started
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

##Change Title Name
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

##Create and Run New Component
Type the below code in terminal (at your application folder)
```ng generate component component_name```
Ex:```ng generate component players```

The CLI creates a new folder, src/app/players and generates the three files of the players.
The  PlayersComponent class (players.component.ts) code looks like below:
﻿```
import { Component, OnInit } from '@angular/core';
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


## Interpolation / Binding
Interpolation allows you to incorporate calculated strings into the text between HTML element tags and within attribute assignments. Template expressions are what you use to calculate those strings.

The interpolation live example / download example demonstrates all of the syntax and code snippets described in this section.
```
<h2> Welcome {{name}} </h2>            //Where name is variable name in component 
<h2>{{2+2}}</h2>				       //Possible And gives answer as 4
<h2>{{"Welcome " + name}}</h2>         //tring Concatination
<h2>{{name.length})</h2>               //Basic attribute
<h2>{{name.toUpperCase()}}</h2>        // Basic funtions/filters
<h2>{{greetUser()}}</h2>               //Calling function present in Component
<h2>{{windown.href.loaction()}}</h2>   //Not allowed

```

## Interpolation vs Property Binding 

DOM is basically collection of objects (window,html,body, head and etc) which allows us to manipulate it. It means that HTML elements are contained in the DOM as objects.HTML elements have attributes which initilizes DOM properties.Once initilization process is done attributes job is done.
```
<input type=”text” value="5">
```
Given input element has type and value attributes.When HTML element is created its properties which have similar names to attributes (but not same thing) is created, too.After initilization given input element have properties such as type and 
value.Note that there is important difference between property and attribute:

— -Attribute value does not change: Change value of input element into 10.

Run getAttribute('value') for our input element.Result will be 5.
— -Properties does change.Change value of input element into 10.Run getElementByTagName('input').value for our input element.Result will be 10.
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

 








## Links To My profiles:

* [Linkedin](https://www.linkedin.com/in/ajinkya-bodade/)
* [Portfolio](https://ajinkyabodade.com/)

