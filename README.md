# Scrabble Score — Vue via CDN

A tiny Vue 3 app that scores a word using Scrabble letter values. Type a word and you'll see one tile per letter plus the total score, and both update as you type.

The point of this example is that there is **no build step**. Vue loads from a CDN with a single `<script>` tag. You don't need npm, `node_modules`, or a bundler. Everything is in [index.html](index.html), and the styles are in [styles/scrabble.css](styles/scrabble.css).

## What it demonstrates

| Concept | Where to look |
| --- | --- |
| Loading Vue from a CDN | `<script src="https://unpkg.com/vue@3.5.45/...">` in `<head>` |
| Reactive state with `ref()` | `const word = ref('')` |
| Derived state with `computed()` | `letters` and `score` |
| Two-way binding with `v-model` | the `<input>` |
| Conditional rendering with `v-if` / `v-else` | the hint vs. the tiles |
| Lists with `v-for` and `:key` | one `<span class="tile">` per letter |
| Attribute binding with `:class` | high-value tiles (8+ points) get the `high` class |

Compare this with a "vanilla" JavaScript version. Here there is no `querySelector`, no `addEventListener`, and no `innerHTML`. You describe what the UI should look like for a given state, and Vue keeps the page in sync with it.

## Running it with VS Code Live Server

1. **Install the extension.** In VS Code, open the Extensions view (`Cmd+Shift+X` on Mac, `Ctrl+Shift+X` on Windows/Linux). Search for **Live Server** (by Ritwick Dey) and click **Install**.
2. **Open the folder.** Choose **File → Open Folder…** and select the `scrabble-vue-cdn` folder. Open the folder itself, not just the file, so the relative path to `styles/` resolves correctly.
3. **Start the server.** Do one of the following:
   - Right-click `index.html` in the Explorer and choose **Open with Live Server**, or
   - Click **Go Live** in the status bar at the bottom right of the window.
4. **View the app.** Your browser opens to something like `http://127.0.0.1:5500/index.html`.
5. **Edit and save.** When you save `index.html` or the CSS, the page reloads automatically.
6. **Stop the server.** Click **Port: 5500** in the status bar (where **Go Live** was).

> **Note:** You need an internet connection, because Vue is downloaded from unpkg.com when the page loads. If the page shows raw `{{ l }}` text or nothing happens when you type, open the browser's DevTools console and check whether the Vue script failed to load.

## Try it yourself

There is a `TRY IT` comment in `index.html` that walks you through adding a **double word score** checkbox:

1. Add `const doubleWord = ref(false)` and return it from `setup()`.
2. Add `<input type="checkbox" v-model="doubleWord">` to the template.
3. Update the `score` computed to return `doubleWord.value ? total * 2 : total`.
