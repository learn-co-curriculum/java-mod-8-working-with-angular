# Working with Angular

## Learning Goals

- Install and use the Angular CLI.
- Create an Angular app.
- Describe the basic structure of an Angular app.

## Introduction

As a framework, Angular also provides a "Command Line Interface (CLI)", which we
can use to create and manage projects.

To install the Angular CLI, run the following command in your project:

`npm install -g @angular/cli`

To create a new Angular project, run the following command:

`ng new flatiron-angular`

When you execute this command, the Angular CLI will ask you a few questions and
then create a base project with a default configuration that corresponds to the
options you selected. Here are the questions you will be asked, and how you
should answer them for now:

1. "Would you like to add Angular routing?": Angular routing is to manage the
   navigation between different parts of your SPA.
   - Answer no to this question, as our initial set up will not concern itself
     with navigation just yet.
2. "Which stylesheet format would you like to use?": Just like JavaScript is
   native to the web and the browser, so is CSS, and just like JavaScript has
   unfortunate limitations that make it a sometimes difficult language to work
   with, so does CSS. So there are a few other ways to handle styling that, just
   like TypeScript translates into JavaScript, also translate into CSS. For now,
   however, we will stick to native CSS.
   - Just hit enter here to choose the default CSS option

The CLI has now created a folder for you named `flatiron-angular`, which has in
it the right folder structure and all the configuration files we need in order
to run a basic Angular project. As we progress in this course, we will explain
the various aspects of this configuration, but for now, let's simply "run" our
Angular project:

1. First, change to the folder where your project was created:
   `cd flatiron-angular` if you're in the directory from which you ran the
   `ng new` command.
2. Second, run the `ng serve` command, which:
   - Compiles and bundles your project files to get them ready for the browser
   - Starts a small web server to allow you to see your application running
     "locally"
   - Start a file watcher that looks for changes in your project files and
     automatically re-packages your app for the browser when you make changes.
     This means you will see your source changes automatically in the browser,
     as long as you keep the `ng serve` process running.

After running `ng serve`, the application you just created will be available in
the browser at the following URL: `http://localhost:4200/`. Open up your browser
and pulling up that URL should give you something similar to this:

![Angular Default App Welcome](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-default-app-welcome.png)

Congratulations, you've just created a basic Angular application.

## The baseline project

The default page that `ng new` puts together for us is actually more complex
than we would like, so we're going to simplify it.

Also note that this simplified "base version" of an Angular project is one that
we're going to return to as we progress through the course, so we can regularly
start with a "clean" project and focus on the specific aspect of Angular that we
want to study in a particular section.

The page you saw in the previous section comes from the following file:
`flatiron-angular/src/app/app.component.html`. To use a more basic version of
this file, open it in your favorite editor and replace its content with the
following:

```html
<div style="text-align:center">
  <h1>Welcome to {{ title }}!</h1>
  <img
    width="300"
    alt="Angular Logo"
    src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNTAgMjUwIj4KICAgIDxwYXRoIGZpbGw9IiNERDAwMzEiIGQ9Ik0xMjUgMzBMMzEuOSA2My4ybDE0LjIgMTIzLjFMMTI1IDIzMGw3OC45LTQzLjcgMTQuMi0xMjMuMXoiIC8+CiAgICA8cGF0aCBmaWxsPSIjQzMwMDJGIiBkPSJNMTI1IDMwdjIyLjItLjFWMjMwbDc4LjktNDMuNyAxNC4yLTEyMy4xTDEyNSAzMHoiIC8+CiAgICA8cGF0aCAgZmlsbD0iI0ZGRkZGRiIgZD0iTTEyNSA1Mi4xTDY2LjggMTgyLjZoMjEuN2wxMS43LTI5LjJoNDkuNGwxMS43IDI5LjJIMTgzTDEyNSA1Mi4xem0xNyA4My4zaC0zNGwxNy00MC45IDE3IDQwLjl6IiAvPgogIDwvc3ZnPg=="
  />
</div>
<h2>Here are some links to help you start:</h2>
<ul>
  <li>
    <h2>
      <a target="_blank" rel="noopener" href="https://angular.io/tutorial"
        >Tour of Heroes</a
      >
    </h2>
  </li>
  <li>
    <h2>
      <a target="_blank" rel="noopener" href="https://angular.io/cli"
        >CLI Documentation</a
      >
    </h2>
  </li>
  <li>
    <h2>
      <a target="_blank" rel="noopener" href="https://blog.angular.io/"
        >Angular blog</a
      >
    </h2>
  </li>
</ul>
```

> You can use any editor to edit your Angular project files, but we recommend an
> editor that knows TypeScript and can help you with compile-time errors during
> development time. Options include VS Code (free) and WebStorm (paid). Once you
> choose an IDE, we recommend opening the entire folder for your project rather
> than opening every single file one by one. Opening the entire folder will give
> you quick access to any of your project file using the IDE's file browsing
> view.

We went from a file with almost 500 lines of code to a file with less than 20
lines of code. This simplicity will help us focus on the specifics thing we want
to cover when we start making modifications to this project.

Now that you're replaced the content of `app.component.html`, your application
should look like this:

![Angular Simplified Welcome](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-simplified-welcome.png)

## Basic styling with Bootstrap

Bootstrap is a CSS framework that provides basic CSS styles to customize an
application with standard elements, such as buttons, form elements and HTML
structure.

You can install Bootstrap for any Angular project using the following command:

```
npm install --save bootstrap
```

In order for your project to use Bootstrap styles seamlessly, we need to change
its configuration as follows:

- Look for the `angular.json` file in the base directory of your project:
  `<project-root>/angular.json`
- Look for the following entry:
  `projects->flatiron-angular->architect->build->options->styles`

![Bootstrap Configuration](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-basics-bootstrap-config.png)

- Add the following entry before the existing `src/styles.css`:
  - `node_modules/bootstrap/dist/css/bootstrap.min.css`
- Now you can use `styles.css` in your HTML just like you did before and Angular
  will resolve that to the entry you just configured in the `angular.json`
  configuration file

## High level structure of our Angular app

As we've seen in the previous section, you can start your application by running
`ng serve` on the command line, in the folder for your project. Then you can
point your browser to `http://localhost:4200` and you will see a basic HTML
page.

We discussed that that HTML content you see in the browser comes from the
`app.component.html` file in your application source code. You were able to
confirm this for yourself by replacing the default content of this file with a
much simplified version and see what it did to the home page when we refreshed
it.

There is a line of code in the HTML that should have caught your attention
though:

```html
<h1>Welcome to {{ title }}!</h1>
```

This corresponding to the following text when we view the application in the
browser:

![Angular Basics Welcome Text](https://curriculum-content.s3.amazonaws.com/java-mod-8/ng-basics-welcome-text.png)

The text "flatiron-angular" does not appear anywhere in the file
`app.component.html`, even though that file is otherwise exactly the same
context as our page in the browser.

This is our first introduction to "data binding" in Angular - the text inside
the open curly braces `{{` and the close curly braces `}}` is a reference to a
variable that Angular can look up for us. In this case, the name of that
variable is `title`.

The variable `title` is defined in another file in our `src/app` folder named
`app.component.ts` - this is an Angular TypeScript file that specifies the
source code associated with our Angular application component. We'll go over
Angular Components in more detail later, but for now notice the following lines
in that file:

```typescript
export class AppComponent {
  title = "flatiron-angular";
}
```

That's where the text in the browser comes from. Change the value of the `title`
variable in the `AppComponent` class and see it change in your browser as well
(as long as you still have `ng serve` running in your terminal).

Let's recap:

1. Angular provides functionality that allows us to define a "component" in
   multiple files and have the content be shown in a web-based application
2. The "content" for our basic component is in `src/app/app.component.html`
3. The "content" can get values from actual TypeScript code, which is in
   `src/app/app.component.ts`
4. The "content" can use the `{{ variable-name }}` notation to refer to any of
   variables defined in the TypeScript code for that component

That's starting to connect the dots, but there is still one important basic item
missing. If you view source on the web page in the browser (right click on any
blank space on the page and select the "View Page Source" option), the source
you will see looks nothing like the source in `app.component.html`. As a matter
of fact, the text you see in the application is nowhere to be found in the
source the browser shows you.

Instead, you will see something like this:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <title>FlatironAngular</title>
    <base href="/" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <link rel="icon" type="image/x-icon" href="favicon.ico" />
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <app-root></app-root>

    <script src="runtime.js" type="module"></script>
    <script src="polyfills.js" type="module"></script>
    <script src="styles.js" defer></script>
    <script src="vendor.js" type="module"></script>
    <script src="main.js" type="module"></script>
  </body>
</html>
```

That's because Angular is a SPA framework, as we discussed earlier. So the page
that the browser sees will stay the same, even as the user interacts with and
navigates your web application. So instead of putting the content of your web
application directly in the static source code for the browser, Angular tells
the browser that there will be an Angular component on this page with the
following line:

```html
<app-root></app-root>
```

And then Angular injects the content of the application into that tag at
runtime. So when that content changes, Angular can continue to inject the
updated content accordingly, without asking the browser to refresh the entire
page.

Going back to `app.component.ts`, you will see a "selector" in the `@Component`
definition:

```typescript
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
```

The "selector" is telling your Angular component what element of the DOM it
should target with its content.

Change the selector to a different value, and you will see that the HTML for
your component no longer shows in the browser.

> Remember that if you leave `ng serve` running while you're making (and saving)
> these changes, you will be able to see the changes reflected in the browser
> without a) having to re-compile and re-package the application and b) having
> to refresh the browser. Note your browser may not refresh automatically if the
> changes you make are to static files, such as CSS and HTML files - in that
> case, simply refresh your browser to see your updated changes.

We've connected a few dots - let's recap:

- When you point your browser to `http://localhost:4200`, your browser requests
  your application's `index.html` file
- That file is `src/index.html` and only contains a skeleton for Angular to get
  started:
  - Default stylesheet
  - JavaScript code to load Angular and your application code (as packaged by
    the Angular CLI)
  - An HTML element that your Angular component will be able to target with its
    content
- The Angular framework then loads your component code and:
  - Finds the target `selector` to use
  - Finds the HTML file to use for your component "view"
  - Finds the variables that should be available for your "model"
  - Parses the HTML file and replaces all references to your variables with
    their actual value

In the recap above, we just introduced 2 terms that merit further definition:

1. View: the "view", in this context, is the part of your application that is
   directly responsible for displaying the content that the user sees. In our
   very basic example, the view is made up of simply the HTML of our simple
   page.
2. Model: the "model", in this context, is the data that the view accesses in
   order to display non-static data. In our very basic example, the model is
   simply made up of the `title` variable.

> Note that even though the general concepts of a "view" and a "model" are
> useful in understanding how the various aspects of Angular come together,
> Angular 2 is not a Model View Controller (MVC) framework in the technical
> sense of the term.

There are many other files in your default Angular project - most of them are
configuration files that we will not need to edit for a while because the
defaults work just fine. Some standouts are:

1. `package.json` configures the dependencies for our Angular project, including
   Angular itself
2. The `node_modules` folder is where those dependencies are saved
3. The `src` folder is where we can put our custom source code for our
   application and where the files we've been working with so far are located
