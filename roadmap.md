---
subtitle: Project Roadmap
---

RadBus has just gotten started.  It's current mission is to provide a useful abstraction on top of existing static and realtime transit API's, marrying that with user's personalized schedules.  But it has the potential to be so much more.

Following are a very high-level set of milestones for the project:

## [Public Launch](https://github.com/RadBus/api/milestones/public-launch) (fall 2014)

* **Pretty web client**  
The current [web client](https://www.radbus.io) is not much to look at and really may only appeal to app developers.  We're working on launching a much more user-friendly web client.

* **Client authentication**  
The API should require some sort of client authentication, at a minimum an API key, so we can distinguish and possibly control access.

## [Release 2](https://github.com/RadBus/api/milestones/release-2) (end of 2014)
* **Get static route data from Transit Data API**  
The [Transit Data API](http://dev.transitdata.io/) is a related transit API project that will provide [GTFS](https://developers.google.com/transit/gtfs/) data published by [MetroTransit](http://metrotransit.org) in an easy to consume web API.  The big benefit for RadBus is it will provide the full list of stops for each route and not just the ones provided by the Metro Transit NexTrip API.

* **Support for more OAuth2 providers**  
Currently the API only supports OAuth2 authentication tokens generated from Google ID's.  However, we'd like to enable more providers like Facebook.  The [Passport](http://passportjs.org) framework may be a good fit here.

* **Other tweaks/enhancements to make the API more useable**  
RadBus is only as useful as the apps it enabled.  Ideally it becomes something that the local app development community uses.  We'd love to see existing as well as new apps use it, which means we may need to make some tweaks for common use-cases that we're not addressing.

## [Release 3](https://github.com/RadBus/api/milestones/release-3) (mid 2015)

* **Big data aggregation possibilities**  
This is really the future value of RadBus and there are so many possibilities here.  One example is the possible use of GPS data of buses.  It's very likely that the GPS location of just about every bus on the grid will be available.  RadBus could use that data, along with the full set of static data provided by the [Transit Data API](http://dev.transitdata.io/) to intelligently tell users exactly when their next bus will arrive.  This is especially handy in the winter months when buses run late and nobody likes standing outside at the bus stop any longer than they have to.  Once we start collecting that data we could go a step further and layer predictions of buses based on how on-time they've been in the past.  Big data could go nuts with this.
