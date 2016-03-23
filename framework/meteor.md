
# Meteor Reading notes

Notes from `Discover Meteor`

<!-- toc -->

## Intro

Directories
- Code in the `/server` directory only runs on the server. 
- Code in the `/client` directory only runs on the client. 
- Files in `/lib` are loaded before anything else.
- Any `main.*` file is loaded a er everything else.
- Your static assets (fonts, images, etc.) go in the `/public` directory.

## Template
The value of `this` (p.31)
> JS: a.hostname // return host name

## Git & Github

- `git checkout [commit/commit-tag]` to see history.
- Github file 
	- "history" (see commits to a certain file)
	- "blame" (who modify what line by line)

## Collection
- shared between all users
  
  `Posts = new Meteor.Collection('posts');` in `collections` directory for both client and server access.

- not using `var`: In Meteor, the `var` keyword limits the scope of an object to the current file. We want to make the `Posts` collection available to our whole app, which is why we're omitting that keyword here.

### Client-side collection
- declare `Posts = new Meteor.Collection('posts');` on client will create a *local*, *in-browser cache* of the real Mongo collection
	- subset of the database
	- documents stored in browser memory (`Posts.find` can be accessed instantly)

> Introducing MiniMongo
> 
> Meteor's client-side Mongo implementation is called MiniMongo. It's not a perfect implementation yet, and you may encounter occasional Mongo features that don't work in MiniMongo. Nevertheless, all the features we cover in this book work similarly in both Mongo and MiniMongo.

### Wiring data in helpers
> Find & Fetch
> 
> In Meteor, `find()` returns a cursor, which is a [reactive data source](http://docs.meteor.com/#/full/find). When we want to log its contents, we can then use `fetch()` on that cursor to transform it into an array.
> 
> Within an app, Meteor is smart enough to know how to iterate over cursors without having to explicitly convert them into arrays first. This is why you won't see fetch() that o en in actual Meteor code (and why we didn't use it in the above example).

### Publications and Subscriptions

#### Intro
- `autopublish`: each collection should be shared in its entirety to each connected client.
- Run `meteor remove autopublish` to remove

```javascript
// server/publications.js
Meteor.publish('posts', function() { 
	return Posts.find();
});
// client/main.js
Meteor.subscribe('posts');
```


#### The Meteor way vs. MVC frameworks
- A meteor app also runs on the client
- Database everywhere
	- Client receives the actual, raw data
	- Access the data instantaneously
> See p.58 for details.

#### More on Publish and Subscribe
- `Publish` only a subset of database.
- `Subscribe` to mirror the data on client at a particular moment
```javascript
// on the server
Meteor.publish('posts', function(author) {
	return Posts.find({flagged: false, author: author});
});
// on the client
Meteor.subscribe('posts', 'bob-smith');
```

#### Finding
- Find the subset from the client database
```javascript
// on the client
Template.posts.helpers({ posts: function(){
    return Posts.find(author: 'bob-smith', category: 'JavaScript'); }
});
```

## Routing
`iron-router` package.

> **Router Vocabulary**
- **Routes**: A route is the basic building block of routing. It's basically the set of instructions that tell the app where to go and what to do when it encounters a URL.
- **Paths**: A path is a URL within your app. It can be static (/terms_of_service) or dynamic (/posts/xyz), and even include query parameters (/search? keyword=meteor).
- **Segments**: The di erent parts of a path, delimited by forward slashes (/).
- **Hooks**: Hooks are actions that you'd like to perform before, a er, or even during the routing process. A typical example would be checking if the user has the proper rights before displaying a page.
- **Filters**: Filters are simply hooks that you define globally for one or more routes. Route
- **Templates**: Each route needs to point to a template. If you don't specify one,
the router will look for a template with the same name as the route by default.
- **Layouts**: You can think of layouts as one of those digital photo frames. They contain all the HTML code that wraps the current template, and will remain the same even if the template changes.
- **Controllers**: Sometimes, you'll realize that a lot of your templates are reusing the same parameters. Rather than duplicate your code, you can let all these routes inherit from a single routing controller which will contain all the routing logic.

- Routing Templates (p.74)
	- Create a layout template with `{&gt; yield}` 
	- Pass the target template by `name: template name` in `router.js`
- Named Routes (p.75)
	- `{pathFor 'postsList'}` in template HTML
- Waiting on Data (p.76)
	- A loading page supported by Iron Router
	- `waitOn()`
	- loading template:  `spin` package with `{&gt; spinner}`
- Routing To A Specific Post (p.78)
	- `path: posts/:_id`
	- `data` field to pass in corresponding data
- Using a Dynamic Named Route Helper
	- `{pathFor 'postPage'}`
	- pass the `_id` by `this` in the template
	- or specify the id: `{pathFor 'postPage' someOtherPost}`

> HTML5 pushState [what???] (p.83)

## Session
To store some ephemeral state that is only relevant to the current user's version of the application. 

- Reloading a page will start a new session, but HCR (Hot Code Reload) won't.
- Code
	- `Session.set('key', 'value');`
	- `Session.get('key');`

### Tracker
- Trigger every time a session changes.

> **Important lessons**
1. Always store user state in the Session or the URL so that users are minimally disrupted when a hot code reload happens.
2. Store any state that you want to be shareable between users within the URL itself.

## Adding Users
`accounts-ui` or `accounts-ui-bootstrap-dropdown` (only style different)
- Adding `accounts` package will create a `Meteor.users` collection.
- The accounts package does “auto-publish” the *currently* logged in user's basic account details no matter what.