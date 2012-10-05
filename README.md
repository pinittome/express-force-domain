Express Force Domain
===========

Force Express 3.x to use a specific domain. Good for adding or removing the www. from your web app and handling parked domains that redirect to your main domain. You just have to pass in the preferred url to your homepage (ie: http://www.example.com).

For test environments, you need to pass port as well if using something other than port 80. (ie: http://www.example.com:8080).

If example2.com points to the same IP as example1.com you can handle the redirect using express-force-domain.

Installing
----

	npm install express-force-domain --save

--save will add the package to your package.json file automatically.


Usage
----

Setup a middleware in app.js before all your other routes are defined, and pass the full url to the homepage as an argument: (including port if other than 80):

	var cfg = require('./config');
	app.all('*', require('./express-force-domain')(cfg.site_url) );

Alternative:

	var site_url = 'http://www.example.com'
	,	force = require('express-force-domain');

	app.all('*', force(site_url) );


or you can pass the url for the homepage manually, (four examples):

	app.all('*', require('./express-force-domain')('http://example.com') );
	app.all('*', require('./express-force-domain')('http://example.com:8080') );
	app.all('*', require('./express-force-domain')('http://www.example.com') );
	app.all('*', require('./express-force-domain')('http://www.example.com:8080') );


Parked domains, assuming example2.com points to the same ip as example.com, and you prefer your app live at http://www.example.com:

	app.all('*', require('./express-force-domain')('http://www.example.com') );

Requests for http://example2.com, http://www.example2.com, and http://example.com will all redirect to http://www.example.com.

More info
----

* http://nodejs.org/
* http://expressjs.com/
* http://npmjs.org/

