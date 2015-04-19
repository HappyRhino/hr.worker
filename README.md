hr.worker [![Build Status](https://travis-ci.org/HappyRhino/hr.worker.png?branch=master)](https://travis-ci.org/HappyRhino/hr.worker)
=============================

> Utility for web-worker communication

## Installation

```
$ npm install hr.worker
```

### Documentation

Create a web-worker "myworker.js" using:

```js
var TaskWorker = require("hr.worker");

var worker = new TaskWorker();

// Register some methods
worker.register({
	// Task can be sync
	hello: function() {
		return "World";
	},

	// Or async:
	testAsync: function() {
		return doSomethingSync()
		.then(function() {
			// it should return a promise
		});
	}
});

// Run the worker
worker.run();
```

And in your application, access the web-worker using:

```js
var worker = new TaskWorker({
	script: "myworker.js"
});


// Call a method
worker.callMethod("hello")
.then(function(msg) {

});

// Or create a binded nethod:
var testAsync = worker.method("testAsync");
```

