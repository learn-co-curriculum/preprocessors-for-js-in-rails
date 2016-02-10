# Asset Preprocessors in Rails

## Outline
The Asset Pipeline is very powerful. We have seen this with just asset concatentation alone. Imagine having to manually combine dozens of JS and CSS files and updating the layouts everytime we want to make a change and deploy our application. The Asset Pipeling just does this for us. On top of that, it also allows us to use preprocessors like [Coffeescript](http://coffeescript.org/) and [SASS](http://sass-lang.com/). But what is a preprocessor?

## Preprocessors
CSS and JavaScript have been around awhile. They do a good job styling our pages and creating cool client-side behavior. They aren't always the easiest to work with though. There has been a lot of improvements to these langauges but because those upgrades require people to upgrade their browsers, we can't always use them. Wouldn't it be great if we could write CSS and JS the way we wanted and have a program turn it into the correct syntax? This is why we have preprocessors.

Because the asset pipeline parses all of our asset files, we are able to write CSS and JS in a langauge that isn't exactly CSS and JS. By using file extensions, asset pipeline can recognize these files as not normal CSS and JS and run it through a preprocessor which creates CSS and JS. If the Asset Pipeline sees `main.js.coffee` it knows this is a Coffeescript file and will run it through the Coffeescript preprocessor.

## Coffeescript
If you have written any JavaScript, you know it has many quirks. For example, the difference between `==` vs `===` when testing equality or how to use [Inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain). Coffeescript takes all of these things that make using JavaScript hard and abstracts them away. What we are left with is a very Ruby like syntax. Take the following pulled from the Coffeescript documentation.

```coffeescript
launch() if ignition is on

volume = 10 if band isnt SpinalTap

letTheWildRumpusBegin() unless answer is no

if car.speed < limit then accelerate()

winner = yes if pick in [47, 92, 13]

print inspect "My name is #{@name}"
```

If you look closely you can see this syntax looks a lot like Ruby. Once we run it through the preproccesor, we get to following.

```javascript
var volume, winner;

if (ignition === true) {
  launch();
}

if (band !== SpinalTap) {
  volume = 10;
}

if (answer !== false) {
  letTheWildRumpusBegin();
}

if (car.speed < limit) {
  accelerate();
}

if (pick === 47 || pick === 92 || pick === 13) {
  winner = true;
}

print(inspect("My name is " + this.name));
```

That's plain old JS with all of it's quirks but we didn't have to write it.

## SASS
While CSS might not be as complex as JavaScript, it still has it's problems. Without language features like selector nesting, basic inheritance and variables it can be hard to keep CSS manageable. CSS3 promises to provide much needed enhancements to the aging CSS 2.1 standard but just like JS, we can only use these new features once browsers support them and a majority of people upgrade to that browser version. This is where SASS comes in. SASS is a sort of enhanced CSS that once ran through the preprocessor, turns into plain CSS.

Here is a simple example of nesting which SASS provides.

```css
.error {
  a {
    color: red;
    text-decoration: none;
  }
  span {
    color: #ff1a1a;
    text-decoration: underline;
  }
}
```

The code above will turn into the following once ran through the preprocessor.

```css
.error a {
  color: red;
  text-decoration: none;
}
.error span {
  color: #ff1a1a;
  text-decoration: underline;
}
```

Notice how we avoided having to repeat `.error`. In SASS, if we need to change `.error` to `.error-text` we only have to change it in one place. In big applications that can save us from making a lot of mistakes.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/asset-preprocessors-in-rails' title='asset-preprocessors-in-rails'>asset-preprocessors-in-rails</a> on Learn.co and start learning to code for free.</p>
