---
layout: "../../layouts/BlogPost.astro"
title: Create an NPM module
description: The beauty of Node modules is that they allow anyone to create and share small, self-contained blocks of code. And it's actually super easy to create your own!
date: "2023-4-14"
categories:
  - sveltekit
  - svelte
published: true
code: "npm init\nnpm login\nnpm publish"
---

## 1. Create an account on NPM

Sign up for an account on npmjs.com. After you've created an account, open the terminal, type npm login and fill in the login details you just created 2. Create a package.json

## 2. Create a package.json

Use npm init to create your package.json, or create it manually. It should at least contain a title and version number, so something like this will do for now:

```bash
{
"name": "@username/hello",
"version": "1.0.0"
}
```

Note that the name of the package should start with your NPM username, followed by the module name (in this case 'hello'). This way we don't have to worry if our package name already exists. 3. We need code, no?

## 3. We need code, no?

Well ironically, we don't need any code at all! The above package.json is all that's required for your module to get accepted by NPM. But that wouldn't be very useful, would it? Let's add some code! Let's, for example, say hi to a friend, or even better: let's say hello to the world! ;-)

```js
const Hello = "Hello World";
module.exports = Hello;
```

## 4. Publish!

Now we have our code and package.json in place, let's publish our module to NPM!

To do so, just run npm publish --access=public

If you visit your profile on NPM, you'll see your bright shiny new module listed! 5. Test it

## 5. Test it

To test if your module works, create a new folder and run npm i @username/hello. You should see the familiar node_modules folder, but this time it contains your own module! Let's try it out: create an index.js with the following code:

```js
const Hello = require("@username/hello");
console.log(Hello);
```

If you now run node index.js it should print "Hello World".

## Improvements

Apart from actually writing a module that does something more useful than printing 'hello world', there are a number of improvements we can make to make the module more useable. We could add a README.md that explains what the module does and how to use it, add a link to our Github repo in the package.json file, or add tests.

If you've made any changes, you should first bump up the version number by running npm version major|minor|patch where 'patch' bumps up the last number (e.g. 1.0.0 to 1.0.1), 'minor' the second number and 'major' the first number. Then run npm publish again.
Example

For an example of a very simple NPM Module, check out my S3 JSON DB.
