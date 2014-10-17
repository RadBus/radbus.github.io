---
subtitle: Architecture and Infrastructure
---

## Tech Stack

The RadBus API runs as a [Node.js](http://nodejs.org/) web application.  Node.js was chosen as the base platform as it lends itself very well to real-time HTTP web servers in terms of performance, flexibility, and ease of development.

Node.js also offers a wide variety of additional capabilities via its rich open source package ecosystem, otherwise known as [NPM](https://www.npmjs.org).  We're leveraging such packages as [Restify](http://mcavage.me/node-restify) for RESTful web service capabilities, [Q](https://github.com/kriskowal/q) for promise-based concurrency, and [Mongoose](http://mongoosejs.com) for data access to [MongoDB](http://www.mongodb.com/).

## Language

Currently RadBus is primarily written in [CoffeeScript](http://coffeescript.org), but not for any particular reason other than its an alternative language to the usual JavaScript when running Node.js.  And in fact, any file/module within the RadBus API could be written in either JavaScript or CoffeeScript.  If the community would rather everything be in JavaScript, especially when ECMAScript 6 is officially released, then it would be trivial to port it over.

## Design

The RadBus API has a very simple structure and design, one that tries to promote modularity and testability.  The primary entry point is the [app.js](https://github.com/RadBus/api/blob/master/app.js) file at the root of the project.  From there all functionality is delegated to script files that are contained within the following functional directories:

* [api](https://github.com/RadBus/api/tree/master/api): REST endpoints and resources.

* [data](https://github.com/RadBus/api/tree/master/data): Data access code to all data sources including databases and other external web services (like the [NexTrip API](http://svc.metrotransit.org/NexTrip/help)).

* [lib](https://github.com/RadBus/api/tree/master/lib): General libraries of functions used across the application.

* [models](https://github.com/RadBus/api/tree/master/models): [Mongoose](http://mongoosejs.com/) ORM models.

* [test](https://github.com/RadBus/api/tree/master/test): Automated tests that use the [Mocha](http://visionmedia.github.io/mocha) test framework as well as the [Chai](http://chaijs.com/) and [Chai as Promised](https://github.com/domenic/chai-as-promised/) assertion libraries.  Most tests against API resources are performed against the HTTP interface using the [super-request](https://github.com/doug-martin/super-request) library.

* [web](https://github.com/RadBus/api/tree/master/web): Web resources like HTTP redirects or images.

Seamless modularity with concurrent code is achieved primarily by using [promises](http://promisesaplus.com/).  Most functions exposed by internal modules within the RadBus API codebase return promises, which makes for easy composability and testibility.

## Infrastructure

Presently the RadBus API [production endpoints](https://api.radbus.io/v1) are hosted on the [Heroku](https://www.heroku.com/about) platform.  Heroku is a [Platform as a Service (Paas)](http://en.wikipedia.org/wiki/Platform_as_a_service) provider that makes it extremely easy to deploy and manage scalable apps and services to the cloud.  Likewise, RadBus's MongoDB backend is currently hosted with [MongoHQ](https://addons.heroku.com/mongohq), which is a Heroku add-on.

Commits to the RadBus API's shared [git repository](https://github.com/TargetRAD/radbus-api) kick off continuous integration builds with [CodeShip](https://www.codeship.io) that, when successful, automatically deploy the new version of the code to the production site.  Builds are run using the [Gulp.js](http://gulpjs.com/) framework, which executes all automated tests as well as [JSHint](http://www.jshint.com) and [CoffeeLint](http://www.coffeelint.org).
