# Marked

## What it is

Marked is a fast, lightweight Markdown compiler written in TypeScript. It turns
Markdown into HTML. It runs in Node.js, in browsers, and as a command line tool.
It follows the CommonMark and GitHub Flavored Markdown (GFM) specifications, has
no runtime dependencies, and does not sanitize its output.

## Features

- Parses CommonMark and GFM Markdown into HTML, with speed as the top priority.
- Works from Node.js, in the browser (UMD or ES module), and from the CLI.
- Extensible through `marked.use({ extensions, renderer, tokenizer, walkTokens, hooks })`.
- Link, image and reference-link text keeps backslashes inside code spans, so
  `` [`\]`](url) `` renders `<code>\]</code>`. Escaped brackets outside code spans
  are still unescaped.
- Does not sanitize HTML. Pass the output through a sanitizer such as DOMPurify.

## How to use

Node.js:

```js
import { marked } from 'marked';
const html = marked.parse('# Marked in Node.js');
```

CLI:

```sh
npm install -g marked
marked -o hello.html
```

Browser:

```html
<script src="https://cdn.jsdelivr.net/npm/marked/lib/marked.umd.js"></script>
<script>
  document.getElementById('content').innerHTML = marked.parse('# Hello');
</script>
```

Always sanitize the output before inserting it into a page:

```js
DOMPurify.sanitize(marked.parse(markdown));
```

## History

- Keep code spans literal inside link, image and reference-link text, and end a link label at the real closing `]` when a code span in it contains a backtick.
