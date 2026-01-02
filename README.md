# syncpack-alpha-devcontainer-bug

This repo is a demo of a bug in [syncpack](https://github.com/JamieMason/syncpack) when using its alpha version 
in a devcontainer with bun.

## Steps to reproduce the bug

1. Clone the repo locally

2. Open the repo in a [VS Code devcontainer](https://code.visualstudio.com/docs/remote/containers). 

   - Install the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

   - Command palette -> "Dev Containers: Reopen in Container"

3. Run `bun install`

4. Run `bunx syncpack lint`

5. You will see the following error:

   ```
   ✗ Node.js/npx/tsx process failed with stderr: error: Cannot find module './cjs/index.cjs' from ''

   Bun v1.3.2 (Linux arm64)
   ```

## Additional information

The `bunx syncpack lint` runs successfully if you add a 
`.syncpackrc.json` file to the root of the project. 
For example, with the following content:
```json
{
  "$schema": "./node_modules/syncpack/dist/schema.json",
  "indent": "    "
}
```

## Related syncpack issue

https://github.com/JamieMason/syncpack/issues/313
