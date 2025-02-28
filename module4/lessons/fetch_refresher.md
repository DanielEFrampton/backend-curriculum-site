---
layout: page
title: Intro to Promises and Fetch
length: 120 minutes
---

## Learning Goals

By the end of this lesson, you will ...

- explain what a Promise is
- explain the advantages of using the Fetch API and Promises
- be able to write GET, POST, and DELETE requests using the Fetch API
- be familiar with patterns to organize/refactor fetch requests

## Promises

Promises allow us to kick off an asynchronous process in the background and respond to its result when it becomes available. Using a Promise typically looks like this:

```js
getProjectsForStudents(students)
  .then(projects => {
    renderDetailsForProjects(projects);
  })
  .catch(error => {
    console.log(error);
  });

doOtherThings();
noneOfTheseFunctions();
willBeBlocked();
fromExecuting();
whileWeWait();
forProjectsToBeRetrieved();
```

In this example, we call a function: `getProjectsForStudents`. Though this might look like a typical function, the developer who wrote it decided that it would return a Promise object. By returning a Promise object, this function does two very important things:

  1. It automatically becomes asynchronous, allowing it to run in the background and giving the rest of our code a chance to continue execution.
  2. It gives us access to two methods: `.then()` and `.catch()`.

If the function completes successfully, the Promise object is considered resolved, and our `.then()` block will execute. Within this block, we are automatically given a result that we can work with (e.g. data from an API endpoint). In this example, we are given project data for our students and we’ll render them to the DOM.

If the function fails for any reason, our Promise object is considered rejected, and our `.catch()` block will execute instead. Within this block, we are automatically given an error that we can use to notify the user that something went wrong.

> A Promise is an object that represents the eventual completion or failure of an asynchronous operation, and it's returning value.

3 states of Promises:

- Pending
- Resolved/Fulfilled (with a return value from your async operation)
- Rejected (with an error message from your async operation)

## What do Promises Give Us?

By using a Promise object, a function does two things:

1. It automatically becomes asynchronous, allowing it to run in the background and giving the rest of our code a chance to continue execution.
2. It gives us access to two methods - `.then` and `.catch`

![inline](https://wtcindia.files.wordpress.com/2016/06/promises.png?w=605)

## Why Use Promises?

Promises allow you to multi-task a bit in JavaScript. They provide a cleaner and more standardized method of dealing with tasks that need to happen in sequence. With Promises, we have more control over what happens with the outcomes of our async processes.

## When to use Promises

The short answer: whenever you're handed a promise by an API you didn't write, where the author chose to use promises. This includes many modern web APIs such as `fetch`.

When you read the documentation for a library that uses promises, one of the first sentences will likely say 'this is a promise-based library'. There are some APIs that still use callbacks rather than promises (the `geolocation` API, for example). You'll want to read the documentation closely to see if the library expects you to use a promise or callback. So for once, we don't really have to be in charge of making a decision here -- we can let the tools and technologies we're using dictate whether or not we should be using promises.

### Advantages of Promises

So besides the obvious syntactical benefits, what are some of the others advantages of promises?

- You are getting an IOU that you're holding on to rather than giving your code away as you would with callbacks.
- Error handling is less broken. It's not a silver bullet. Synchronous functions either `return` or throw an error. In a similar vein, your promises will either become *resolved* by a value or become *rejected* with an error.
- You can catch errors along the way and deal with them in a way that is *similar* to synchronous code.
- Chaining promises is easy and does not result in callback hell.

But wait, there's more.

- `Promise.all` takes an array of promises and waits until all of the promises are resolved. This solves the nastiness involved in doing this with callbacks.
- `Promise.race` takes an array of promises and resolves as soon as any one of them fulfill. This would allow you to hit 3 API endpoints and then move on when we heard back from whichever one came back first.

## Promises with Fetch Requests

Every fetch request we make will return a Promise object that contains our response data. This allows us to easily react to the type of response we get once it's available.

Handling the response of a fetch request might look something like this:

```js
fetch('/api/v1/discussions')
  .then(response => response.json())
  .then(discussions => renderDiscussions(discussions))
  .catch((error) => console.error({ error }))
```

While we wait for the server to return our response, the rest of our application can continue executing other code in the meantime. Once the response object is available, our first `.then()` block will fire. The response object returns a lot of extra information that we don't necessarily need. All we want in this scenario is a JSON object of our discussions data which we can get by calling `response.json()`.

Converting the body to a JSON data structure with `response.json()` actually returns another Promise. (Converting the data to a particular type can take significant time, which is why we have this additional Promise step before we can begin working with out data.) Because we're getting another Promise object back, we can simply chain another `.then()` block where we actually receive our project data. We can then render it to the DOM with our imaginary `renderDiscussions()` function. Notice how we are using another `.then()` statement. This is called Promise Chaining. We do this because each `.then()` results in a new Promise.

If for any reason the request failed, the `.catch()` block will be fired and we will log the error to the console.

[Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

## A Typical Fetch Request

```js
const fetchDiscussions = () => {
  fetch('/api/v1/discussions')
  .then((response) => response.json())
  .then((rawDiscussions) => cleanDiscussions(rawDiscussions))
  .catch((error) => console.error({ error }));
}
```

```js
const postDiscussions = () => {
  fetch('/api/vi/discussions', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      discussionName: 'Movies',
      totalPoints: 100,
    });
  });
}
```

DISCUSS: What differences do you notice between a GET and POST?

`fetch()` takes TWO arguments:

- URL or API endpoint (always)
- object of configuration settings for the request. This may contain what kind of request we're making and any data we might need to pass along with it (optional)

## Hedgehog Party

Fork and clone down the [Hedgehog Party Repo](https://github.com/turingschool-examples/fetch-hedgehog-party).

**Step 1:** Choose a driver. Look through the JavaScript in `public/index.js` - we already have a get request up and running to get, then append, all the hedgies in the database onto the DOM. Make sure you open up the app in the browser and keep your Dev Tools open while working. Now, in `public/index.js`, anootate lines 4-7. Make sure you and your partner can explain the role of `appendHedgehogs` and `appendHedgehog`.

_We will pause here for a class discussion to make sure everyone fully understands how this GET request works._

**Step 2:** Now, write the request to POST a new hedgehog. See the README for info on what is expected in the request. An event listener has already been written for you on line 42.

**Step 3:** Now, the other partner should drive. Work together to write the request to DELETE a hedgehog from the invite list.

NOTE: Both tasks require network requests as well as DOM manipulation. This is good practice for Play😊

## Error Checking

Read about error handling [here](https://css-tricks.com/using-fetch/#article-header-id-3), then try to implement similar error handling in our GET request.

Check out the example below. Our second button makes an unsuccessful request with a 404 response so why does it seem to still succeed?

<p data-height="348" data-theme-id="0" data-slug-hash="aEvBvz" data-default-tab="js,result" data-user="kat3kasper" data-embed-version="2" data-pen-title="Fetch Error Handling" class="codepen">See the Pen <a href="https://codepen.io/kat3kasper/pen/aEvBvz/">Fetch Error Handling</a> by Katelyn Kasperowicz (<a href="https://codepen.io/kat3kasper">@kat3kasper</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

The promise returned from `fetch()` will only reject on network failure or if anything prevented the request from completing. This means it won't reject on a response of 404 or 500 from the server but will return a `status.ok` status set to false.

To handle responses that do not return a successful status, we can create a response handler. If the response is `ok` we continue processing the data as we did above. If it is not we use `Promise.reject` to trigger our catch handler and pass it an error object with the `status`, `statusCode` and any addition json information we get from the server.

```js
function handleResponse(response) {
  // Convert the readable stream to json
  return response.json()
    .then((json) => {
      if (!response.ok) {
        // if the response returns a status code outside of 200-299 throw an error
        const error = {
          status: response.status,
          statusText: response.statusText,
          json
        }
        return Promise.reject(error)
      }
      // if the response is ok return the json object
      return json
    })
}

fetch(`http://localhost:3000/api/v1/posts`)
  .then(handleResponse)
  .then((data) => {
    // Now data is in a format we are more used to i.e. {"posts": [{"title": "Fetch Refresher", "author": "Katelyn Kasperowicz"},..]}
  })
  .catch(error => {
    // When there is an error in the handleResponse function we can access the error object given to us by the Promise reject
  })
```

## Organizing Fetch Requests

In the examples above, the success or failure of our `fetch()` requests are handled by anonymous functions. By changing these, we can start to organize and DRY up our code.

I'd suggest grouping all of these to-be-named functions together (...hint, hint...in a file...).

Let's refactor this example:

```js
fetch('http://localhost:3000/api/v1/posts')
  .then(handleResponse)
  .then((posts) => {
    posts.forEach((post) => {
      $(".posts-box").append(post)
    })
  })
  .catch(error => {
    console.error(error)
  })
```

Say we created one function responsible for appending posts and another to log our error to the console:

```js
const appendPosts = (posts) => {
  posts.forEach((post) => {
    $(".posts-box").append(post)
  })
}

const errorLog = (error) => {
  console.error(error)
}
```

We could then slim down our `fetch()` call to just this:

```js
fetch('http://localhost:3000/api/v1/posts')
  .then(handleResponse)
  .then(appendPosts)
  .catch(errorLog)
```

Notice how we still need to handle the call with `.then()` and `.catch().`


### Going Further - Organizing Requests as Event Handlers

It's very likely you'll be using `fetch()` requests as event handlers.

For example, on submit of a form, we make a POST request with the form data.

Just like we organized our `fetch()` handlers above, we can organize our event handlers similarly.

If we were working with form data like this:

```js
$('form').on('submit', (event) => {
  event.preventDefault()
  return fetch('http://example.com/articles', {
    method: 'post',
    headers: {
      'Content-Type': 'application/json'
    },
    body: JSON.stringify(article)
  })
    .then(handleResponse)
    .then(appendArticle)
    .catch(errorLog)
})
```

We can refactor that so our event bindings live together, our `fetch()` calls live together, and our `fetch()` handlers live together.

```js
// event bindings live nicely as one liners
$('form').on('submit', postArticle)

const requestOptions = {
  method: 'post',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(article)
}

// Fetch call is nice and tidy on its own
const postArticle = (event) => {
  event.preventDefault()
  return fetch('http://example.com/articles', requestOptions)
    .then(handleResponse)
    .then(appendArticle)
    .catch(errorLog)
}
```

If you want to use _Postman_ to check your endpoints, be sure for the POST method that it looks like this:

![Postman POST Example](../lessons/assets/hedgie_post.png)


## Interview Questions

Pair up with your Play partner and practice answering the following interview questions:

* What are the advantages of using fetch?
* What are promises used for? Can you give an example of when you've used one?

Be ready to share you answer(s) with the class when we wrap up.


## Additional Resources
* [David Walsh fetch API](https://davidwalsh.name/fetch)
* [CSS Tricks Using Fetch](https://css-tricks.com/using-fetch/)

Be aware that AJAX can also be used to make client side request to a server. Fetch has become more popular in recent years as it is built into Javascript, works on almost all browsers, and doesn't require jQuery. If you want to learn more check out this old lesson [AJAX Refresher](./archive/ajax-refresher.md)
