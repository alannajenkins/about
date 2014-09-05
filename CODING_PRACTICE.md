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
* To tidy up test files, json objects passed into a test should be stored separately in a `fixtures` directory and json objects checking expected outcomes shoudl be stored in an `expected` directory.

### Version control

When making a change to code, you should always increment the version in the ```package.json``` according to the guidelines set out in [http://semver.org/](http://semver.org/).

#### Tagging

When deploying code, we should always tag to create a *snapshot* (see [http://git-scm.com/book/en/Git-Basics-Tagging](http://git-scm.com/book/en/Git-Basics-Tagging).
This way, we are always able to include our packages at a specific state, eg:

```
"dependencies": {
	"elephant": "git+ssh://git@bitbucket.org/hxshortbreaks/elephant.git#0.0.1",
	"lodash": "^2.4.1",
	"q": "^1.0.1"
}
```
