## Coding Practice

### Testing

When writing in node.js, testing should use the following tools framework.

* Tests should be written using [mocha](https://github.com/visionmedia/mocha).
* Assertions should be done in a BDD format using the [chai](https://github.com/chaijs/chai) library and the [should](http://chaijs.com/guide/styles/) style.
* When testing promise based software you should use [chai-as-promised](https://github.com/domenic/chai-as-promised/).
* When describing a block of tests which interrogate a specific function the describe definition should have a hash followed by the function name like this:
``` 
describe( '#myFunction', function() {
```

* If you want to mock, stub or spy on your test subjects use [sinon](sinonjs.org)
