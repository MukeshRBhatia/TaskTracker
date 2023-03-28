# TaskTracker

## Package.json:

Dependencies- core, forms, router, compiler, common, animations, rxjs (library that gives observables)
Dev dependencies - karma, jasmine,
scripts- serve, build, test, etc

## Tsconfig.json: typescript config

1. compilation error: "@Input() color: string;" > Property 'color' has no initializer and is not definitely assigned in the constructor.
   Solution: Add
   "compilerOptions": {
   "strictPropertyInitialization": false,
   ...
   }

## Angular.json:

More towards building the app, index file, output, style files
This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 15.2.4.

## index.html, main.ts, app.module.ts, style.css

Index.html is the single page that gets loaded (<app-root> selector)
Everything to display is generated with the javascript bundle
Main.ts is the main ts file and is the entry point to Angular. AppModule is passed to the bootstrapModule. App Module is actually the app.module.ts.
style.css has global styling

## src folder:

4 files generally for each component (ts, html, css, spec file for testing)

# Concepts:

## Components

-
- ng generate component components/header : generated and adds a header in the project at src/app/component

## Data binding

One way and two way

- String interpolation
- Property Binding
-

## @Input, @Output

## Lifecycle methods

## Constructor

## Directives

-ngStyle
-ngFor

## Events

- <button (click)="onClick()">Click</button> > add corresonding function in the .ts of the component. onClick() { console.log('clicked'); } > Emit this event and pass it to parent using @Output
- <fa-icon [ngStyle]="{'color':'red'}" [icon]="faTimes" (click)="onClickDelete(task)">
  and  
  onClickDelete(task: Task) {
  console.log(task);
  }

## Data models in Angular Apps, class vs interface

Interfaces are great when you only need the type checking whereas classes are great when you not only want the type checking, but you need some methods or require some other logic.

## Create a service.ts and import it in a ts component

- ng generate service services/task

- What is @Injectable?

- Import the service, add it as a constructor parameter, and maybe add it to ngOnInit

## Observables and async data

- Service.ts:
  import { Observable, of } from 'rxjs';
  . .
  getTasks(): Observable<Task[]> {
  const tasks = of(TASKS);
  return tasks;
  }

- And to use this elsewhere:
  this.service.getTasks().subscribe((tasks) => this.tasks = tasks);

## HttpClient

- In build provided by Angular unlike React
- Service.ts: import { HttpClient, HttpHeaders } from '@angular/common/http';
- App.module.ts:
  import { HttpClientModule } from '@angular/common/http';
  ...
  imports: [
  BrowserModule,
  . . .
  HttpClientModule
  ],
- Pass as parameter to the service constructor: constructor(private http:HttpClient) { }
- make a call:
  getTasks(): Observable<Task[]> {
  return this.http.get<Task[]>(this.apiUrl);
  }

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Angular font awesome

ng add @fortawesome/angular-fontawesome

## Dummy server

- npm i json-server
- check package.json for entry
- add a script in package.json "server": "json-server --watch db.json --port 5000"
- Create a db.json file with some data in the root

{
"posts": [
{ "id": 1, "title": "json-server", "author": "typicode" }
],
"comments": [
{ "id": 1, "body": "some comment", "postId": 1 }
],
"profile": { "name": "typicode" }
}

- npm run server
- http://localhost:5000/tasks

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
