# canvas
Canvas API for **[Deno](https://deno.land)**. This is a fork of **[deno-canvas](https://github.com/DjDeveloperr/deno-canvas)**.

## Installation
Import from https://deno.land/x/canvaseno/mod.ts or just import from raw GitHub URL, https://raw.githubusercontent.com/DevSnowflake/canvaseno/main/mod.ts.

## Usage
`mod.ts` provides a default export exposing the complete CanvasKit API, and other exports from the file are types and util functions.

```ts
import Canvas from 'https://deno.land/x/canvaseno/mod.ts'
import { serve } from "https://deno.land/std@0.78.0/http/server.ts";

const canvas = Canvas.createCanvas(200, 200);
const ctx = canvas.getContext('2d');

ctx.fillStyle = '#4d5e94';
ctx.fillRect(10, 10, canvas.width - 20, canvas.height - 20);

const server = serve({ hostname: "0.0.0.0", port: 8080 });
console.log(`HTTP webserver running. Access it at: http://localhost:8080/`);

for await (const request of server) {
  request.respond({ status: 200, body: canvas.toBuffer() });
}
```

And run with `deno run --allow-net filename.ts`.

# Images
For using images, use `loadImage` method exported from `mod.ts`.

```ts
const image = await loadImage(myURL);
ctx.drawImage(image, x, y);
```

## Working image formats (tested formats)
- png
- jpeg
- webp
- gif