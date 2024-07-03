Install Express
```console
npm install express
```

Simple Code
```javascript
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

This app starts a server and listens on port 3000 for connections. The app responds with “Hello World!” for requests to the root URL (`/`) or _route_. For every other path, it will respond with a **404 Not Found**.

It also has **express-generator** library which generate project from template.

### Routing

_Routing_ determines how an application responds to a client request to a particular endpoint, which is a URI (or path) and a specific HTTP request method (GET, POST, and so on).

Each route can have one or more handler functions, which are executed when the route is matched.

Route definition takes the following structure

```javascript
app.METHOD(PATH, HANDLER)
```

Where:
- `app` is an instance of `express`.
- `METHOD` is an [HTTP request method](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods), in lowercase.
- `PATH` is a path on the server.
- `HANDLER` is the function executed when the route is matched.

```javascript
app.put('/user', (req, res) => {
  res.send('Got a PUT request at /user')
})
```

```javascript
app.delete('/user', (req, res) => {
  res.send('Got a DELETE request at /user')
})
```

#### Serve Static Files
the `express.static` built-in middleware function in Express.
```javascript
express.static(root, [options])
```

For example, use the following code to serve images, CSS files, and JavaScript files in a directory named `public`:

```javascript
app.use(express.static('public'))
```

Now, you can load the files that are in the `public` directory:

```plain-text
http://localhost:3000/images/kitten.jpg
http://localhost:3000/css/style.css
```

To create a virtual path prefix (where the path does not actually exist in the file system) for files that are served by the `express.static` function, [specify a mount path](https://expressjs.com/en/4x/api.html#app.use) for the static directory, as shown below:

```javascript
app.use('/static', express.static('public'))
```

Now, you can load the files that are in the `public` directory from the `/static` path prefix.

```plain-text
http://localhost:3000/static/images/kitten.jpg
http://localhost:3000/static/css/style.css
```

**Routing methods**

Express supports the following routing methods corresponding to the HTTP methods of the same names:

|   |   |   |
|---|---|---|
|- `checkout`<br>- `copy`<br>- `delete`<br>- `get`<br>- `head`<br>- `lock`<br>- `merge`<br>- `mkactivity`|- `mkcol`<br>- `move`<br>- `m-search`<br>- `notify`<br>- `options`<br>- `patch`<br>- `post`|- `purge`<br>- `put`<br>- `report`<br>- `search`<br>- `subscribe`<br>- `trace`<br>- `unlock`<br>- `unsubscribe`|

**app.all(path, callback [, callback ...])**
The following callback is executed for requests to `/secret` whether using GET, POST, PUT, DELETE, or any other HTTP request method:

```javascript
app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...')
  next() // pass control to the next handler
})
```

 it requires that all routes from that point on require authentication, and automatically load a user. Keep in mind that these callbacks do not have to act as end-points: `loadUser` can perform a task, then call `next()` to continue matching subsequent routes.

```javascript
app.all('*', requireAuthentication, loadUser)
```

#### Route paths

Route paths, in combination with a request method, define the endpoints at which requests can be made. Route paths can be strings, string patterns, or regular expressions.

Express uses [path-to-regexp](https://www.npmjs.com/package/path-to-regexp) for matching the route paths; see the path-to-regexp documentation for all the possibilities in defining route paths.

This route path will match requests to `/random.text`.

```javascript
app.get('/random.text', (req, res) => {
  res.send('random.text')
})
```

This route path will match `butterfly` and `dragonfly`, but not `butterflyman`, `dragonflyman`, and so on.

```javascript
app.get(/.*fly$/, (req, res) => {
  res.send('/.*fly$/')
})
```

#### Route parameters

Route parameters are named segments in the URL that capture values at their position. These values populate the `req.params` object with the route parameter name as their keys.

```
Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }
```

Since the hyphen (`-`) and the dot (`.`) are interpreted literally, they can be used along with route parameters for useful purposes.

```
Route path: /flights/:from-:to
Request URL: http://localhost:3000/flights/LAX-SFO
req.params: { "from": "LAX", "to": "SFO" }
```

```
Route path: /plantae/:genus.:species
Request URL: http://localhost:3000/plantae/Prunus.persica
req.params: { "genus": "Prunus", "species": "persica" }
```

#### Route handlers
You can use multiple callback functions as middleware for request handling, and they can invoke next('route') to skip remaining route callbacks. This allows imposing pre-conditions and passing control to subsequent routes when needed.

A single callback function can handle a route. For example:

```javascript
app.get('/example/a', (req, res) => {
  res.send('Hello from A!')
})
```

More than one callback function can handle a route (make sure you specify the `next` object). For example:

```javascript
app.get('/example/b', (req, res, next) => {
  console.log('the response will be sent by the next function ...')
  next()
}, (req, res) => {
  res.send('Hello from B!')
})
```

An array of callback functions can handle a route. For example:

```javascript
const cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

const cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

const cb2 = function (req, res) {
  res.send('Hello from C!')
}

app.get('/example/c', [cb0, cb1, cb2])
```

A combination of independent functions and arrays of functions can handle a route. For example:

```javascript
const cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

const cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

app.get('/example/d', [cb0, cb1], (req, res, next) => {
  console.log('the response will be sent by the next function ...')
  next()
}, (req, res) => {
  res.send('Hello from D!')
})
```

## Response methods

The methods on the response object (`res`) in the following table can send a response to the client, and terminate the request-response cycle. **If none of these methods are called from a route handler, the client request will be left hanging.**

|Method|Description|
|---|---|
|[res.download()](https://expressjs.com/en/4x/api.html#res.download)|Prompt a file to be downloaded.|
|[res.end()](https://expressjs.com/en/4x/api.html#res.end)|End the response process.|
|[res.json()](https://expressjs.com/en/4x/api.html#res.json)|Send a JSON response.|
|[res.jsonp()](https://expressjs.com/en/4x/api.html#res.jsonp)|Send a JSON response with JSONP support.|
|[res.redirect()](https://expressjs.com/en/4x/api.html#res.redirect)|Redirect a request.|
|[res.render()](https://expressjs.com/en/4x/api.html#res.render)|Render a view template.|
|[res.send()](https://expressjs.com/en/4x/api.html#res.send)|Send a response of various types.|
|[res.sendFile()](https://expressjs.com/en/4x/api.html#res.sendFile)|Send a file as an octet stream.|
|[res.sendStatus()](https://expressjs.com/en/4x/api.html#res.sendStatus)|Set the response status code and send its string representation as the response body.|


#### app.route()

You can create chainable route handlers for a route path by using `app.route()`. Because the path is specified at a single location, creating modular routes is helpful, as is reducing redundancy and typos.

Here is an example of chained route handlers that are defined by using `app.route()`.

```javascript
app.route('/book')
  .get((req, res) => {
    res.send('Get a random book')
  })
  .post((req, res) => {
    res.send('Add a book')
  })
  .put((req, res) => {
    res.send('Update the book')
  })
```

#### express.Router

Use the `express.Router` **class** to create modular, mountable route handlers. A `Router` instance is a complete middleware and routing system; for this reason, it is often referred to as a “mini-app”.

The following example creates a router as a module, loads a middleware function in it, defines some routes, and mounts the router module on a path in the main app.

Create a router file named `birds.js` in the app directory, with the following content:

```javascript
const express = require('express')
const router = express.Router()

// middleware that is specific to this router
router.use((req, res, next) => {
  console.log('Time: ', Date.now())
  next()
})
// define the home page route
router.get('/', (req, res) => {
  res.send('Birds home page')
})
// define the about route
router.get('/about', (req, res) => {
  res.send('About birds')
})

module.exports = router
```

Then, load the router module in the app:

```javascript
const birds = require('./birds')

// ...

app.use('/birds', birds)
```

The app will now be able to handle requests to `/birds` and `/birds/about`, as well as call the `timeLog` middleware function that is specific to the route.

### Writing middleware

Middleware functions access the req and res objects, along with the Express router's next function, which executes the succeeding middleware when invoked.

Middleware functions can perform the following tasks:
- Execute any code.
- Make changes to the request and the response objects.
- End the request-response cycle.
- Call the next middleware in the stack.

Note: If the current middleware function does not end the request-response cycle, it must call `next()` to pass control to the next middleware function. Otherwise, the request will be left hanging.

Starting with Express 5, middleware functions that return a Promise will call `next(value)` when they reject or throw an error. `next` will be called with either the rejected value or the thrown Error.

```javascript
const express = require('express')
const app = express()

const myLogger = function (req, res, next) {
  console.log('LOGGED')
  next()
}

app.use(myLogger)

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(3000)
```

Every time the app receives a request, it prints the message “LOGGED” to the terminal.

The order of middleware loading is important: middleware functions that are loaded first are also executed first.

If `myLogger` is loaded after the route to the root path, the request never reaches it and the app doesn’t print “LOGGED”, because the route handler of the root path terminates the request-response cycle.

#### Middleware function requestTime

Next, we’ll create a middleware function called “requestTime” and add a property called `requestTime` to the request object.

```javascript
const requestTime = function (req, res, next) {
  req.requestTime = Date.now()
  next()
}
```

The app now uses the `requestTime` middleware function. Also, the callback function of the root path route uses the property that the middleware function adds to `req` (the request object).

```javascript
const express = require('express')
const app = express()

const requestTime = function (req, res, next) {
  req.requestTime = Date.now()
  next()
}

app.use(requestTime)

app.get('/', (req, res) => {
  let responseText = 'Hello World!<br>'
  responseText += `<small>Requested at: ${req.requestTime}</small>`
  res.send(responseText)
})

app.listen(3000)
```

When you make a request to the root of the app, the app now displays the timestamp of your request in the browser.

#### Middleware function validateCookies

Finally, we’ll create a middleware function that validates incoming cookies and sends a 400 response if cookies are invalid.

Here’s an example function that validates cookies with an external async service.

```javascript
async function cookieValidator (cookies) {
  try {
    await externallyValidateCookie(cookies.testCookie)
  } catch {
    throw new Error('Invalid cookies')
  }
}
```

Here we use the [`cookie-parser`](https://expressjs.com/resources/middleware/cookie-parser.html) middleware to parse incoming cookies off the `req` object and pass them to our `cookieValidator` function. The `validateCookies` middleware returns a Promise that upon rejection will automatically trigger our error handler.

```javascript
const express = require('express')
const cookieParser = require('cookie-parser')
const cookieValidator = require('./cookieValidator')

const app = express()

async function validateCookies (req, res, next) {
  await cookieValidator(req.cookies)
  next()
}

app.use(cookieParser())

app.use(validateCookies)

// error handler
app.use((err, req, res, next) => {
  res.status(400).send(err.message)
})

app.listen(3000)
```

### Using Middleware

> Express is a routing and middleware web framework that has minimal functionality of its own: An Express application is essentially a series of middleware function calls.

_Middleware_ functions are functions that have access to the [request object](https://expressjs.com/en/4x/api.html#req) (`req`), the [response object](https://expressjs.com/en/4x/api.html#res) (`res`), and the next middleware function in the application’s request-response cycle.

Middleware functions can perform the following tasks:

- Execute any code.
- Make changes to the request and the response objects.
- End the request-response cycle.
- Call the next middleware function in the stack.

An Express application can use the following types of middleware:

- [Application-level middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.application)
- [Router-level middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.router)
- [Error-handling middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.error-handling)
- [Built-in middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.built-in)
- [Third-party middleware](https://expressjs.com/en/guide/using-middleware.html#middleware.third-party)

You can load application-level and router-level middleware with an **optional mount path**. You can also load a series of middleware functions together, which creates a sub-stack of the middleware system at a mount point.

#### Application-level middleware

application-level middleware can be bind to app object using `app.use()` and `app.METHOD`

- This example shows a middleware function with no mount path. The function is executed every time the app receives a request.

```javascript
const express = require('express')
const app = express()

app.use((req, res, next) => {
  console.log('Time:', Date.now())
  next()
})
```

- This example shows a middleware function mounted on the `/user/:id` path. The function is executed for any type of HTTP request on the `/user/:id` path.

```javascript
app.use('/user/:id', (req, res, next) => {
  console.log('Request Type:', req.method)
  next()
})
```

- This example shows a route and its handler function (middleware system). The function handles GET requests to the `/user/:id` path.

```javascript
app.get('/user/:id', (req, res, next) => {
  res.send('USER')
})
```

Here is an example of loading a series of middleware functions at a mount point, with a mount path.

```javascript
app.use('/user/:id', (req, res, next) => {
  console.log('Request URL:', req.originalUrl)
  next()
}, (req, res, next) => {
  console.log('Request Type:', req.method)
  next()
})
```

This example shows a middleware sub-stack that handles GET requests to the `/user/:id` path.

```javascript
app.get('/user/:id', (req, res, next) => {
  console.log('ID:', req.params.id)
  next()
}, (req, res, next) => {
  res.send('User Info')
})

// handler for the /user/:id path, which prints the user ID
app.get('/user/:id', (req, res, next) => {
  res.send(req.params.id)
})
```

To skip the rest of the middleware functions from a router middleware stack, call `next('route')` to pass control to the next route. **NOTE**: `next('route')` will work only in middleware functions that were loaded by using the `app.METHOD()` or `router.METHOD()` functions.

This example shows a middleware sub-stack that handles GET requests to the `/user/:id` path.

```javascript
app.get('/user/:id', (req, res, next) => {
  // if the user ID is 0, skip to the next route
  if (req.params.id === '0') next('route')
  // otherwise pass the control to the next middleware function in this stack
  else next()
}, (req, res, next) => {
  // send a regular response
  res.send('regular')
})

// handler for the /user/:id path, which sends a special response
app.get('/user/:id', (req, res, next) => {
  res.send('special')
})
```

**Middleware can also be declared in an array for reusability.**

```javascript
function logOriginalUrl (req, res, next) {
  console.log('Request URL:', req.originalUrl)
  next()
}

function logMethod (req, res, next) {
  console.log('Request Type:', req.method)
  next()
}

const logStuff = [logOriginalUrl, logMethod]
app.get('/user/:id', logStuff, (req, res, next) => {
  res.send('User Info')
})
```

#### Router-level middleware

>The order in which you define middleware with `router.use()` is very important. They are invoked sequentially, thus the order defines middleware precedence.

Router-level middleware works in the same way as application-level middleware, except it is bound to an instance of `express.Router()`.

```javascript
const router = express.Router()
```

Load router-level middleware by using the `router.use()` and `router.METHOD()` functions.
```javascript
const express = require('express')
const app = express()
const router = express.Router()

// a middleware function with no mount path. This code is executed for every request to the router
router.use((req, res, next) => {
  console.log('Time:', Date.now())
  next()
})

// a middleware sub-stack shows request info for any type of HTTP request to the /user/:id path
router.use('/user/:id', (req, res, next) => {
  console.log('Request URL:', req.originalUrl)
  next()
}, (req, res, next) => {
  console.log('Request Type:', req.method)
  next()
})

// a middleware sub-stack that handles GET requests to the /user/:id path
router.get('/user/:id', (req, res, next) => {
  // if the user ID is 0, skip to the next router
  if (req.params.id === '0') next('route')
  // otherwise pass control to the next middleware function in this stack
  else next()
}, (req, res, next) => {
  // render a regular page
  res.render('regular')
})

// handler for the /user/:id path, which renders a special page
router.get('/user/:id', (req, res, next) => {
  console.log(req.params.id)
  res.render('special')
})

// mount the router on the app
app.use('/', router)
```
#### Built-in middleware

Express has the following built-in middleware functions:

- [express.static](https://expressjs.com/en/4x/api.html#express.static) serves static assets such as HTML files, images, and so on.
- [express.json](https://expressjs.com/en/4x/api.html#express.json) parses incoming requests with JSON payloads.
- [express.urlencoded](https://expressjs.com/en/4x/api.html#express.urlencoded) parses incoming requests with URL-encoded payloads.

#### Third-party middleware
```console
$ npm install cookie-parser
```

```javascript
const express = require('express')
const app = express()
const cookieParser = require('cookie-parser')

// load the cookie-parsing middleware
app.use(cookieParser())
```

#### Error-handling middleware

Error-handling middleware always takes _four_ arguments. You must provide four arguments to identify it as an error-handling middleware function. Even if you don’t need to use the `next` object, you must specify it to maintain the signature. Otherwise, the `next` object will be interpreted as regular middleware and will fail to handle errors.

```javascript
app.use((err, req, res, next) => {
  console.error(err.stack)
  res.status(500).send('Something broke!')
})
```

> Express comes with a default error handler so you don’t need to write your own to get started.

Errors that occur in synchronous code inside route handlers and middleware require no extra work. If synchronous code throws an error, then Express will catch and process it. For example:

```javascript
app.get('/', (req, res) => {
  throw new Error('BROKEN') // Express will catch this on its own.
})
```

Starting with Express 5, route handlers and middleware that return a Promise will call `next(value)` automatically when they reject or throw an error. For example:

```javascript
app.get('/user/:id', async (req, res, next) => {
  const user = await getUserById(req.params.id)
  res.send(user)
})
```

If `getUserById` throws an error or rejects, `next` will be called with either the thrown error or the rejected value. If no rejected value is provided, `next` will be called with a default Error object provided by the Express router.

Note: If you pass anything to the `next()` function (except the string `'route'`), Express regards the current request as being an error and will skip any remaining non-error handling routing and middleware functions.

**The default error handler**

Express comes with a built-in error handler that takes care of any errors that might be encountered in the app. This default error-handling middleware function is added at the end of the middleware function stack.

If you pass an error to `next()` and you do not handle it in a custom error handler, it will be handled by the built-in error handler; the error will be written to the client with the stack trace. The stack trace is not included in the production environment.

> Set the environment variable `NODE_ENV` to `production`, to run the app in production mode.

When an error is written, the following information is added to the response:

- The `res.statusCode` is set from `err.status` (or `err.statusCode`). If this value is outside the 4xx or 5xx range, it will be set to 500.
- The `res.statusMessage` is set according to the status code.
- The body will be the HTML of the status code message when in production environment, otherwise will be `err.stack`.
- Any headers specified in an `err.headers` object.

If you call next() with an error after starting the response (e.g., during streaming), Express's default error handler closes the connection and fails the request. When adding a custom error handler, delegate to the default Express handler if headers are sent to the client.

```javascript
function errorHandler (err, req, res, next) {
  if (res.headersSent) {
    return next(err)
  }
  res.status(500)
  res.render('error', { error: err })
}
```

For organizational (and higher-level framework) purposes, you can define several error-handling middleware functions, much as you would with regular middleware functions. For example, to define an error-handler for requests made by using `XHR` and those without:

```javascript
const bodyParser = require('body-parser')
const methodOverride = require('method-override')

app.use(bodyParser.urlencoded({
  extended: true
}))
app.use(bodyParser.json())
app.use(methodOverride())
app.use(logErrors)
app.use(clientErrorHandler)
app.use(errorHandler)
```

In this example, the generic `logErrors` might write request and error information to `stderr`, for example:

```javascript
function logErrors (err, req, res, next) {
  console.error(err.stack)
  next(err)
}
```

Also in this example, `clientErrorHandler` is defined as follows; in this case, the error is explicitly passed along to the next one.

Notice that when _not_ calling “next” in an error-handling function, you are responsible for writing (and ending) the response. Otherwise those requests will “hang” and will not be eligible for garbage collection.

```javascript
function clientErrorHandler (err, req, res, next) {
  if (req.xhr) {
    res.status(500).send({ error: 'Something failed!' })
  } else {
    next(err)
  }
}
```

Implement the “catch-all” `errorHandler` function as follows (for example):

```javascript
function errorHandler (err, req, res, next) {
  res.status(500)
  res.render('error', { error: err })
}
```

### Debugging Express

Express uses the [debug](https://www.npmjs.com/package/debug) module internally to log information about route matches, middleware functions that are in use, application mode, and the flow of the request-response cycle.

>`debug` is like an augmented version of `console.log`, but unlike `console.log`, you don’t have to comment out `debug` logs in production code. Logging is turned off by default and can be conditionally turned on by using the `DEBUG` environment variable.

To see all the internal logs used in Express, set the `DEBUG` environment variable to `express:*` when launching your app.

```console
$ DEBUG=express:* node index.js
```

