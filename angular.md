# AngularJS

<p align="center">
  <br><br>
  <img src="https://github.com/Jyotsna-Singh/Jyotsna-Singh/blob/master/assets/img/angular.png">
</p>

## What Angular2 is:

<ul>
<li>javaScript client side framework for creating powerful web applications.
<li>Created and maintained by Google
<li>Most popular JS framework to date
<li>What HTML could be if it were created for dynamic applications
</ul>

## What Angular2 is NOT

<ul>
<li>NOT a server side framework/technology
<li>NOT a JS library (jQuery/React)
<li>NOT a design pattern (MVC)
<li>NOT a platform/language (.Net/Java)
<li>NOT a plugin/extension
</ul>

## What Angular2 offers
<ul>
<li>Dynamic HTML 
<li>Forms & input handling
<li>Event Handling
<li>Routing
<li>Powerful Templates
<li>Fast Rendering
<li>HTTP services
<li>latest JS standards (ES2015/ES6)
<li>Component Encapsulation
</ul>

## What’s new from Angular 1?
<ul>
<li>No more controllers & scope
<li>Components/reusable code
<li>Reduces learning curve
<li>TypeScript & ES2015/ES6
<li>Better mobile Support
<li>RxJS & Observables
</ul>


## What is TypeScript?
<ul>
<li>A Strict superset of javaScript with added features.
<li>Maintained by microSoft
<li>Optional static typing
<li>Class based object oriented programming
<li>Resembles java, C/C++
</ul>

## What are Components in AngularJS?
<ul>
<li>Components are the main way to build and specify elements and logic on the page.
<li>Components are the basic building block of the UI.
<li>An angular application is a tree of Angular Components
</ul>

## What are Decorators in AngularJS?
Decorators allow us to mark a class as an Angular Component & provide metadata that determines how the component should be processed, instantiated & used at runtime.


## Example

    Import {Component} from ‘@angular/core’;
    
    @Component({
	  Selector: ‘my-component’,
	  Template: ‘<div> hello my name is {{name}}.<button(click)=”sayMyName()”>Say My name</button></div>’
    })
    
    export class MyComponent{
	   constructor(){
	  this.name = ‘Jyotsna’
    }
    
    sayMyName(){
	  console.log(‘My Name is’, this.name)
    	}
    }

## Services in AngularJS
<ul>
<li>Services are used for reusable data services to share between components throughout and application.
<li>Refactoring data access to a separate service keeps the component lean and focused on supporting the view
<li>Services are asynchronous. We can return data as a promise or an absolute using RxJS
</ul>

## Angular2 Installation Methods
<ul>
<li>From Scratch
<li>Using quickstart – github.com/angular/quickstart
<li>Angular CLI Tool
<li>Npm install –g angular-cli
<li>Requirements: Node.js, NPM, Git
</ul>

## New project in AngularJS
<ol>
<li> Git bash into your folder
<li> git clone https://github.com/angular/quickstart my-app
<li> cd my-app
<li> Open project in Atom Editor or Visual Studio
<li> All angular dependencies are listed in package.json
<li> npm install
<li> Create something awesome!
</ol>



