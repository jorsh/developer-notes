# Angular 2

## Modules
An Angular module is a class with an NgModule decorator.

Its purpose:
- Organize the pieces of our application
- Arrange them into blocks
- Extend our application with capabilities from external libraries
- Provide a template resolution environment
- Aggregate and re-export

Its most important properties:
- **declarations** - the view classes that belong to this module. Angular has three kinds of view classes: components, directives, and pipes.
- **exports** - the subset of declarations that should be visible and usable in the component templates of other modules.
- **imports** - other modules whose exported classes are needed by component templates declared in this module.
- **providers** - creators of services that this module contributes to the global collection of services; they become accessible in all parts of the app.
- **bootstrap** - the main application view, called the root component, that hosts all other app views. Only the root module should set this bootstrap property.

Example of a module:
```typescript
@NgModule({
  imports: [BrowserModule, AppRoutingModule],
  exports: [MyModule],
  declarations: [AppComponent, OtherComponents],
  providers: [HeroService],
  bootstrap: [AppComponent]
})
export class AppModule {}
```


### Bootstrap Array
- Every application must bootstrap at least one component, the root application component
- The bootstrap array should only be used in the root application module, AppModule

### Declarations Array
- Every component, directive, and pipe we create must belong to one and only oneAngular module
- Only declare components, directives and pipes
- Never re-declare components, directives, or pipes that belong to another module
- All declared components, directives, and pipes are private by default
- The Angular module provides the template resolution environment for its component templates

### Exports Array
- Export any component, directive, or pipe if another components need it
- Re-export modules to re-export their components, directives, and pipes
- We can re-export something without importing it first
- Never export a service

### Imports Array
- Importing a module makes available any exportedcomponents, directives, and pipes from that module
- Only import what this module needs
- Importing a module does NOT provide access to its imported modules

### Providers Array
- Any service provider added to the providers array is registered at the rootof the application
- Don't add services to the providers array of a shared module
- Consider building a CoreModulefor services and importing it once in the AppModule
- Routing guards must be added to the providers array of an Angular module


## Decorators
Decorators are what turn our plain TypeScript classes into Components

## Components
Basic building blocks of any Angular application.
```typescript
@Component({
	selector: 'my-app',
	template: `<tag>Content</tag>`,
	styles: [`selector { property: value}`],  //this is an array
	templateUrl: 'template.html',
	styleUrls: ['styles.css']
})
export class AppComponent {}
```

*Note: If it is the main component the exported class should be called AppComponent*


## Directives
A directive is how we add dynamic behavior to HTML.

There are three different kinds of directives:
- **Component**: These are directives with a template
- **Structural**: Alters layout by adding, removing, or replacing HTML elements
- **Attribute**: An Attribute directive changes the appearance or behavior of a DOM element

### Structural Directives
```typescript
import { Directive, ElementRef } from '@angular/core';

@Directive({ selector: '[myHighlight]' })
export class HighlightDirective {
    constructor(el: ElementRef) {
       el.nativeElement.style.backgroundColor = 'yellow';
    }
}
```
and it is activated like this
```html
<p myHighlight>Highlight me!</p>
```

Do not forget to declare it in the corresponding module
```typescript
@NgModule({
  declarations: [
    HighlightDirective
  ]
```

#### Respond to user events
```typescript
```


### Structural directives
Examples of Structural Directives are \*ngFor and \*ngIf

## Pipes
A pipe takes in data as input and transforms it to a desired output.

```
<h1>{{target | pipeName : params}}</h1>
```
Available pipes:
- Async
- Currency
- Date
- Decimal
- I18nPlural
- I18nSelect
- Json
- LowerCase
- Percent
- Slice
- UpperCase

### Custom Pipes
```typescript
import {Pipe, PipeTransform} from '@angular/core';

@Pipe({
    name: pow
})
export class PowPipe implements PipeTransform {
    transform(value: number, exponent: string): number {
        return Math.pow(value, exp)
    };
}
```

and in the template we do:
```
<p>Expo: {{2 | pow: 4}}</p>
```

do not forget to declare it:
```typescript
import {PowPipe} from './pow.pipe';

@NgModule({
    declarations: [PowPipe]
})
```

## Data Binding
### Interpolation
Allows us to insert interpolated strings from the component to the DOM
```
{{pageTitle}}
```

### Property Binding
Allow us to glue component properties to DOM element properties.
```
<img [src]="prop.image">
```

### Class Binding
Allow us to specify a CSS class to add to a DOM element if a component property is true.
```
<div [class.name] = "property"></div>
```

### Event Binding
Allows us to listen to any DOM event and call a component method when it's triggered.
```
<button (click)="componentMethod(arg)">Action</button>
```
- To listen to any event, we need to remove the "on" in front of the word, wrap it in parentheses, and specify a component method to call.
- If we need to access the event object, we can pass it into our component method with $event e.g. `<button (click)="componentMethod($event)">Action</button>`
- We can also call event.preventDefault(); to prevent a clicked link from being followed or a firm from being submitted.

### Two-way Binding
It allows us to specify a component property that will use two-way binding.
It means that if the component property is modified inside the component (JavaScript) or inside our web page (HTML), it will stay in sync.

## Services
Services are used to organize and share code across the app, and they're usually where you create your data access methods.

*Note*: Use PascalCasing for naming services

1. Add the Injectable decorator
```typescript
@Injectable
export class MyService {
    myMethod() {
        return RESPONSE;
    }
}
```

2. Let our injector know about the service
```typescript
import {MyService} from './my.service';

@NgModule({
    providers: [MyService]
})
```

3. Injecting the dependency
```typescript
@Component({...})
export class MyComponent {
    constructor(private myService:  MyService) {}
}
```
## Interface
- A **specification** identifying a related set of properties and methods.
- A class commits to supporting the specification by **implementing** interface.
- Use the interface as **data type**

## Lifecycle Hooks
Angular creates it, renders it, creates and renders its children, checks it when its data-bound properties change, and destroys it before removing it from the DOM.

- `OnInit`: Perform component initialization, retrieve data.
- `OnChanges`: Perform action after changes to input properties.
- `OnDestroy`: Perform cleanup.

```typescript
import {Component, OnInit} from '@angular/core';

export class MyComponent implements OnInit {
    ngOnInit(): void {
        console.log('In OnInit');
    }
}
```

## Module Id
It contains the absolute URL of the component class module file
- It requires writing modules in CommonJS format
- And to use a module loader, such as SystemJS

```typescript
@Component({
    moduleId: module.id,

   // Without moduleId: '/app/products/products.component.html'
   templateUrl: 'products.component.html'
})
```````

## Nested Components
### Passing data to a nested component
- Use `@Input` decorator
- Attached to a property of any type
- Use property binding to pass data to the component

### Emit an event from the nested component
- Use the `@Output` decorator
- Attached to a property declared as a EventEmitter
- Use the generic argument to define the event payload type
- Use the new keyword to create an instance of the EventEmitter
- Use event binding to respond to events from the nested component
- Use `$event` to access the event payload passed from the nested component


## Routing

There are two ways to display components:

**Nest-able components**
- Define a selector
- Nest in another component
- No route

**Routed components**
- No selector
- Configure routes
- Tie routes to actions

### Register the router service
Import RouterModule and register it:
````typescript
import {RouterModule} from '@angular/router';
@NgModule({
  imports: [
    //forRoot() method checks if the routes we want are available. We pass in an array of rotes
    // forRoot([], {useHash: true}) if we want to use hash routes instead
    RouterModule.forRoot([])
    ]
})
````

### Configuring routes
````typescript
[
    {
    path: 'product', // Note it doesn't have a leading slash
    component: ProductComponent
    },
    {
    path: 'product/:id', //route with parameter
    component: ProductDetailComponent
    },
    {
    path: '',
    redirectTo: 'product', //redirect to a default route
    pathMatch: 'full'
    },
    {
    path: '**',
    component: 'product' //wildcard route. e.g. 404 or so.
    },
]
````

### Tying routes to actions

Add the RouterLink directive as an attribute of a clickable element.

````html
<a [routerLink]="['/product', product.productId]">{{product.productName}}</a>
````
The first element in the array is the route, and the remaining are parameters.



### Placing the views
Whenever a route is activated, the associated template is displayed in the `<router-outlet>` element.
````html
<router-outlet></router-outlet>
````

### Reading parameters from a route

Import the ActivatedRoute service and declare it in the constructor.
```typescript
import {ActivatedRoute} from '@angular/router';

//2. Declare it
constructor(private _route: ActivatedRoute) {}

//3. Assign it to a variable. Note the plus sign, this is to convert the id number to string
ngOnInit(): void {
  let id: string = +this._route.snapshot.params['id'];
}
```
There are two ways to obtain the parameter:
1. Use `snapshot` method to get the initial value of the parameter.
2. Use an Observable if you expect the parameter to change without leaving the page.

## Activating a route with code
````typescript
import {Router} from '@angular/router';

// And in the class do...
constructor(private _router: Router) {}

onBack(): void {
  this._router.navigate(['/products']);
}
````

## Protecting a route with Guards
- **CanActivate**: Guard navigation to a route
- **CanDeactivate**: Guard navigation from a route
- **Resolve**: Pre-fetch data before activating a route
- **CanLoad**: Prevent asynchronous routing

### Building a Guard:
````typescript
import {Injectable} from '@angular/core';
import {CanActivate} from '@angular/router';

@Injectable()
export class DetailGuard implements CanActivate {
  canActivate(): boolean {
    return true
  }
}
````

Since DetailGuard is a service, we need to declare it in the providers array at a **Module Level**.
````typescript
import {DetailGuard} from './detail-guard.service';

@NgModule({
  providers: [DetailGuard]
})
````
### Using a Guard
````typescript
    RouterModule.forRoot({
        path: 'product/:id',
        canActivate: [DetailGuard],
        component: ProductDetailComponent
    })
````

## Observables
Useful to manage asynchronous data. Treat events as a collection.

### Operators
- Methods on Observables that compose new Observables
- Some operators: map, filter, take, merge, delay, concat, buffer, distinct, first, last, zip, startWith, window, takeUntil, skip, scan, sample, amb, join, flatMap.
- They process each value as soon as it is emitted

### Promise vs Observable
|Promise| Observable|
|-------|-----------|
|Provides a single future value| Emits multiple values over time|
|Not lazy| Lazy|
|Not cancellable| Cancellable|
|-|Supports map, filter, reduce and similar operators|
