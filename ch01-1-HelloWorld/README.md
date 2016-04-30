==================
Hello World
==================

Index.html
==========
1.load the JavaScript libraries we need; 
2.load our JavaScript files, (main.js needs app.component.js to be there first).
3.add the <my-app> tag in the <body>. This is where our app lives!


app/app.component.js
====================
The component is a class that controls a view template.

The Class definition object is where we implement the component itself
  .Class({
      constructor: function() {}
    });
The Component definition object takes a configuration object with two properties.
 ng.core.Component({
      selector: 'my-app',
      template: '<h1>Hello World</h1>'
    })

app/main.js
=========== 
we'll create a single global namespace for our application "app" and we'll add all of our code artifacts to this one global object. Within each file we surround the code in an IIFE ("Immediately Invoked Function Expression").

(function(app) {
})(window.app || (window.app = {}));

Modules rely on other modules. In JavaScript Angular apps, when we need something provided by another module, we get it from the app object. When another module needs to refer to AppComponent, it gets it from the app.AppComponent like this:

Bootstrap: Add a new file , main.js, to the app/ folder as follows:

(function(app) {
  document.addEventListener('DOMContentLoaded', function() {
    ng.platform.browser.bootstrap(app.AppComponent);
  });
})(window.app || (window.app = {}));

When Angular calls the bootstrap function in main.js, it reads the AppComponent metadata, finds the my-app selector, locates an element tag named my-app, and loads our application between those tags.

