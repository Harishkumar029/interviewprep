# Angular
Angular is a javaScript framework used for building single-page client ***(SPA)*** applications using HTML and TypeScript.

### Features of Angular: 
1. Component-based structure
2. Two-way data binding
3. Dependency injection.
4. Routing
5. Angular Forms & HTTP Module

# what is Components
### The Component contains the data and user interaction logic that define how the View(HTML) looks and behaves
The Component is responsible for providing the data to the View. Angular uses data binding to get the data from the Component to the View and vice versa

The Angular Components are plain JavaScript classes defined using the @Component Decorator.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-example',
  template: `
    <h1>{{ title }}</h1>
    <button (click)="sayHello()">Say Hello</button>
  `
})
export class ExampleComponent {
  title = 'Hello, Angular!';

  sayHello() {
    console.log('Hello!');
  }
}
```
Component metadata properties
1. Selector
2. Providers
3. Directives
4. Styles/styleUrls
5. template/templateUrl

## 2. What is Angular Data Binding

Data binding is a technique, where the data stays in sync between the component and the view.

 Whenever the user updates the data in the view, Angular updates the component. When the component gets new data, the Angular updates the view.

### Data Binding in Angular types

The data binding in Angular can be broadly classified into two groups. One way binding or two-way binding

### 1. One way binding

### From Component to View
1. Interpolation {{ }}: : ***{{ templateExpression }}***
2. Property binding  [ ]: ***<img [src]="imageUrl" alt="Image">***




### From View to Component

1. Event binding :
Event binding allows you to handle events triggered by user interactions in the template and perform actions in the component class. Here's an example: 

```typescript 
export class ExampleComponent {
  handleClick() {
    console.log('Button clicked!');
  }
}

<button (click)="handleClick()">Click me</button>
```

### 1. Two way binding

2. ngModel

Two-way binding ([( )]): Two-way binding allows for both property binding and event binding together. It enables synchronization of data between the component and the template in both directions. Here's an example using ngModel directive:

```typescript
export class ExampleComponent {
  name = 'John Doe';
}
```

```html
<input [(ngModel)]="name" placeholder="Enter your name">
<p>Your name is: {{ name }}</p>
```


# Directives
# Pipes
# Component Communication
# Component Life Cycle Hook
# Angular Forms
# Services & Dependency Injection
# Angular Forms Validation
# HTTP 
# Angular Router
# Angular Module
# Advanced Components
# Observable in Angular
# Configuration
# Handling Errors
# Angular CLI
# SEO & Angular

## Misc


1. @ViewChild and @ContentChild
2. statefull application and stateless apllication
3. Reactive forms vs reactive forms
4. dirty pristine touch
5. Routing can activate
6. @Inject vs @Injectable
7. ngtemplate vs ngcontent vs ngcontainer
8. Lazy loading
9. pagination


