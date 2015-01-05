## Coding Practice

### Testing

When writing in node.js, testing should use the following tools framework.

* Tests should be written using [mocha](https://github.com/visionmedia/mocha).
* Assertions should be done in a BDD format using the [chai](https://github.com/chaijs/chai) library and the [should](http://chaijs.com/guide/styles/) style.
* When testing promise based software you should use [chai-as-promised](https://github.com/domenic/chai-as-promised/).
* When testing external APIs (either 3rd party or our own) the reply should be mocked out using [nock](https://github.com/pgte/nock).
* When describing a block of tests which interrogate a specific function the describe definition should have a hash followed by the function name like this:
```
describe( '#myFunction', function() {
```

* If you want to mock, stub or spy on your test subjects use [sinon](sinonjs.org)
* To tidy up test files, json objects passed into a test should be stored separately in a `fixtures` directory and json objects checking expected outcomes shoudl be stored in an `expected` directory.

### Version control

When making a change to code, you should always increment the version in the ```package.json``` according to the guidelines set out in [http://semver.org/](http://semver.org/).

You should also update (or create) a **CHANGELOG.md**, with the same version number, eg;

```
## **0.0.0**
- [**issueNumber**](http://issue.link) Description of single change 
- [**issueNumber**](http://issue.link)
    - description of change
    - another change description
```

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
###Promises
Where possible we should use promises instead of callbacks and should separate each item in the promise chain onto a new line, eg;

```
myPromiseReturningFunction()
.then( doSomethingElse )
.then( doAnotherThing )
.fail( handleTheError );
``` 

This is also true for all types of promise chains;

```
Q.allSettled( promiseArray )
.spread( doSomethingWithResults)
```

### Sql

#### Some hard and fast rules for now

* Both table and column names shall be camel case.
* Columns should be singlular
* Table names should be plural
* Enum should be capitals
* Any columns within a table should be contextual i.e.

Table: products  
Columns: id, name, createdAt  
Not columns: product_id, product_name, created

* Any datetime or timestamp type columns should be suffixed with 'At' or suffixed with 'Date', i.e. createdAt, modifiedDate
* Any boolean/tinyInt type columns should be prefixed with 'is' i.e. isMale, isBackward

* When not using an ORM such as Idiorm/Sequelize, sql clauses should be written capitalising the keywords and broken on to multiple lines as follows:

```
SELECT id, name, isMale, createdAt
FROM products
WHERE name = 'test'
	AND isMale = 1
ORDER BY id ASC
LIMIT 10
```
