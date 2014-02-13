## A scaffold tool for web applications

<img src="img/cover.png" />

Igor Ribeiro Lima @ [Avenue Code](http://www.avenuecode.com)

*ilima@avenuecode.com* <!-- .element: class="feature" -->

Feb 17th, 2014

---

## Agenda

 - About scaffolding
 - Scaffolding on some languages
 - Yeoman
 - Tools that work together with Yeoman
 - Finding a generator for a web application
 - An example
 - Challenge

---

## Prerequisites

- JavaScript beginner

---

## About scaffolding

- promoting a better learning
- aiding the student in his/her construction of new knowledge
- it may help the leaner immediately
- it makes learning more tangible
- also, it can help developers quickly build application

---

## If you come from Rails, these commands below may be familiar:

```
rails generate controller Greetings hello
```

```
rails generate scaffold HighScore game:String score:integer
```

----

## on Django

```
django-admin.py startproject mysite
```

----

## on Java Play Framework

```
play new myFirstApp
```

----

## on Maven

```
  mvn archetype:generate \
    -DarchetypeGroupId=org.apache.maven.archetypes \
    -DgroupId=com.mycompany.app \
    -DartifactId=my_app
```

----

## Why not do scaffolding using NodeJS?

That's why Yeoman comes up

---

## Yeoman

The web's scaffolding tool for modern webapps

----

## Yeoman works well with two great friends

- [Grunt](http://gruntjs.com/): used for automating tasks such as: minification, compilation, unit testing, linting, etc.
- [Bower](http://bower.io/): used for dependency management

----

## How to find the best generator

- [Official generators](http://yeoman.io/official-generators.html)
- [Community generators](http://yeoman.io/community-generators.html)

<br>
For our example we'll use the official generator named [webapp](https://github.com/yeoman/generator-webapp). Let's move on and do an example. Let's go?

---

## An example

This example was based from the [AngularJS tutorial](http://angularjs.org/)

----

## Installing the required tools

```
npm install -g yo                # install Yeoman
npm install -g grunt-cli         # install Grunt
npm install -g bower             # install Bower
npm install -g generator-webapp  # install a generator
```

----

## Scaffolding our example

```
yo webapp                    # scaffold out a skeleton webap project
grunt serve                  # preview the app example
```

----

## Adding a js dependency

```
bower install knockout-dist  # install KnockoutJs as a dependency
```
<br>
add the script in **./app/index.html**

<pre class="prettyprint">
<code class="lang-html">
<script src="bower_components/knockout-dist/knockout.js"></script>
</code>
</pre>

----

## Binding contexts

``./app/scripts/main.js``
<br>

```
(function(global, ko){
  global.generate_a_new_todo = function() {
    return {
      total: ko.observable(0),
      list:  ko.observableArray(),
      text:  ko.observable(''),
      add:   function() {
        var todo = this;
        todo.list.push({
          text: todo.text()
        });
        todo.text('');
        todo.total(todo.list().length);
      }
    };
  };

  ko.applyBindings(generate_a_new_todo());
}(window, ko));

```

----

## Adding a view

``./app/index.html``
<br>

<pre class="prettyprint">
<code class="lang-html"><p>
  <a class="btn btn-lg btn-success" href="#" data-bind="click: add">
    Splendid!
  </a>
</p>

<input type="text" data-bind="value: text" size="30"
  placeholder="add a new todo here">

<ul data-bind="foreach: list">
  <li><span data-bind="text: text"></span></li>
</ul>

<p class="lead">Total: <span data-bind="text: total"></span></p>
</code>
</pre>

---

## Conclusion

- Your life should be easier from now
- Scaffold any webapp you have in mind

---

## Learn more

1. [Yeoman](http://yeoman.io/)
1. [Grunt](http://gruntjs.com)
1. [Bower](http://bower.io/)

---

## Challenge

1. Scaffold an web application
1. Use a JS framework of your preference
  - AngularJS
  - Ember
  - Backbone
  - Mustache
  - Handlebars
  - So forth
1. Do the simpliest TO DO list application
