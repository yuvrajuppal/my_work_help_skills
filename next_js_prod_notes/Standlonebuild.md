# Next.js standalone production build

## 1. Enable standalone output

Add this to `frontend/next.config.ts`. The `output: "standalone"` setting tells Next.js to generate a production server and its traced dependencies in `.next/standalone`. [Next.js standalone output docs](https://nextjs.org/docs/app/api-reference/config/next-config-js/output)

```ts
import type { NextConfig } from "next";

const nextConfig: NextConfig = {
  output: "standalone",
  /* config options here */
  reactCompiler: true,
};

export default nextConfig;
```

React Compiler is optional. If you enable it, install `babel-plugin-react-compiler` as a dev dependency. [Next.js React Compiler docs](https://nextjs.org/docs/app/api-reference/config/next-config-js/reactCompiler)

## 2. Add the packaging script

Save this CommonJS script as `frontend/script/Standlonebuild.js`. It copies `public` and `.next/static` into the standalone bundle, then packages it in `frontend/output`. The script expects a `public` directory, which can be empty.

```js
const fs = require("node:fs");
const path = require("node:path");

const projectRoot = path.resolve(__dirname, "..");
const publicDir = path.join(projectRoot, "public");
const nextDir = path.join(projectRoot, ".next");
const standaloneDir = path.join(nextDir, "standalone");
const staticDir = path.join(nextDir, "static");
const outputDir = path.join(projectRoot, "output");
const stagingDir = path.join(projectRoot, ".output-standalone-staging");

function ensureDirectory(directory, description) {
  if (!fs.existsSync(directory) || !fs.statSync(directory).isDirectory()) {
    throw new Error(`${description} was not found at ${directory}. Run npm run build first.`);
  }
}

try {
  ensureDirectory(standaloneDir, "Next.js standalone build");
  ensureDirectory(publicDir, "Public assets directory");
  ensureDirectory(staticDir, "Next.js static assets");

  const serverFile = path.join(standaloneDir, "server.js");
  if (!fs.existsSync(serverFile)) {
    throw new Error(`Standalone server.js was not found at ${serverFile}. Run npm run build first.`);
  }

  const standalonePublicDir = path.join(standaloneDir, "public");
  const standaloneStaticDir = path.join(standaloneDir, ".next", "static");

  fs.rmSync(standalonePublicDir, { recursive: true, force: true });
  fs.cpSync(publicDir, standalonePublicDir, { recursive: true });

  fs.rmSync(standaloneStaticDir, { recursive: true, force: true });
  fs.mkdirSync(path.dirname(standaloneStaticDir), { recursive: true });
  fs.cpSync(staticDir, standaloneStaticDir, { recursive: true });

  fs.rmSync(stagingDir, { recursive: true, force: true });
  fs.cpSync(standaloneDir, stagingDir, { recursive: true });
  fs.rmSync(outputDir, { recursive: true, force: true });
  fs.renameSync(stagingDir, outputDir);

  console.log(`Standalone build copied to ${outputDir}`);
} catch (error) {
  fs.rmSync(stagingDir, { recursive: true, force: true });
  console.error(error instanceof Error ? error.message : error);
  process.exitCode = 1;
}
```

## 3. Add the npm commands

Merge these entries into the `scripts` object in `frontend/package.json`.

```json
{
  "scripts": {
    "build": "next build",
    "build2": "node script/Standlonebuild.js"
  }
}
```

## 4. Build, package, and run

From `frontend`, run the build and packaging commands in order, then start the generated server.

```sh
npm run build && npm run build2
node output/server.js
```

Copy the entire `output` directory to the deployment host, including the hidden `.next` directory. On the host, run `node server.js` from inside that directory.

## 5. Prompt for AI Agent

```text
Set up a standalone production build for the existing Next.js app in frontend/.

1. Add output: "standalone" to the existing Next.js config. Keep its other settings, including the current React Compiler setting.
2. Create frontend/script/Standlonebuild.js using the packaging script in next_js_prod_notes/Standlonebuild.md. Keep the requested file path and make sure the script runs with the app's module configuration.
3. Add "build": "next build" and "build2": "node script/Standlonebuild.js" to frontend/package.json. Preserve the other npm scripts and dependencies.
4. Run npm run build and npm run build2 from frontend/. Check that output/server.js, output/public, and output/.next/static exist. Start the server and request a known route to verify it responds, then stop the server.
5. Summarize the files changed and report any verification steps that could not run.
```
