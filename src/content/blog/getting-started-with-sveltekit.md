---
title: Getting started with Sveltekit
description: "SvelteKit is a powerful framework built on top of Svelte, designed to make it easier to build fast and efficient web applications. With features like Server-Side Rendering (SSR), static site generation, and the robustness of Svelte’s reactive framework, SvelteKit is a compelling choice for both new and experienced developers."
date: "2023-4-16"
categories:
  - sveltekit
  - svelte
published: true
code: "npm create svelte@latest my-app\ncd my-app\nnpm install\nnpm run dev -- --open"
---

## Prerequisites

To get started with SvelteKit, you should have the following installed on your computer:

- Node.js (Version 14.x or later)
- npm (Node Package Manager)

## Setting Up Your SvelteKit Project

To create a new SvelteKit project, open a terminal and run the following command:

```bash
npm init svelte@next my-sveltekit-app
```

After answering the initialization questions, navigate into your project folder:

```bash
cd my-sveltekit-app
```

Now, install the project dependencies:

```bash
npm install
```

Start the development server:

```bash
npm run dev
```

Open your browser and go to `http://localhost:3000`. You should see the default SvelteKit starter page.

## Understanding the File Structure

Your SvelteKit project will have the following main folders and files:

- `src/`: Where your Svelte components and routes live.
  - `routes/`: Each Svelte file here corresponds to a route in your application.
  - `$layout.svelte`: A layout file that wraps around your route components.
- `svelte.config.js`: SvelteKit configuration file.
- `package.json`: Lists the project dependencies and scripts.

## Building a Simple SvelteKit App

Let's build a simple app that displays a list of items and allows you to add new items to the list.

### Create a New Route

Create a new Svelte file `Items.svelte` in the `src/routes` directory and add the following code:

```svelte
<script>
  let items = ['Item 1', 'Item 2'];
  let newItem = '';

  function addItem() {
    items = [...items, newItem];
    newItem = '';
  }
</script>

<h1>My Items</h1>

<ul>
  {#each items as item}
    <li>{item}</li>
  {/each}
</ul>

<input type="text" bind:value={newItem} placeholder="New item" />
<button on:click={addItem}>Add Item</button>
```

### Update the Layout

You can update the `$layout.svelte` file in the `src/routes` directory to include a navigation menu:

```svelte
<script>
  import { link } from '$app/navigation';
</script>

<nav>
  <a href="/" use:link>Home</a>
  <a href="/items" use:link>Items</a>
</nav>

<main>
  <slot></slot>
</main>
```

## Deploying Your SvelteKit App

### Build the App

To build your SvelteKit application for production, run:

```bash
npm run build
```

This will generate a `build/` directory with the optimized version of your app.

### Deploy with Vercel or Netlify

SvelteKit has built-in adapters for various hosting providers. To deploy your application to Vercel or Netlify, you can follow their respective documentation.

## Conclusion

SvelteKit makes it easy to build fast and efficient web apps with a lot less boilerplate. With features like SSR, static site generation, and the power of Svelte, it's an excellent choice for modern web development.
