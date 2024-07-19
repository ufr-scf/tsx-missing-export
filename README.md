# tsx missing export

## Steps to reproduce

- In `shared` dir:
  - run `npm install`
- In `backend` dir:

  - run `npm install`
  - run `npm run build`. There won't be any errors.
  - run `node build/index.js`. This will print "Hello World" to the console.
  - now try running `npm run dev`. You will get the following error:

  ```
    > dev
    > tsx src/index.ts

    Debugger listening on ws://127.0.0.1:53043/612628a8-4cb0-4782-a14f-dc06f7658ed7
    For help, see: https://nodejs.org/en/docs/inspector
    Debugger attached.
    Waiting for the debugger to disconnect...
    /workspaces/tsx-missing-export/backend/src/index.ts:1
    import { Permission } from "@/shared";
             ^

    SyntaxError: The requested module '@/shared' does not provide an export named 'Permission'
        at ModuleJob._instantiate (node:internal/modules/esm/module_job:171:21)
        at async ModuleJob.run (node:internal/modules/esm/module_job:254:5)
        at async onImport.tracePromise.__proto__ (node:internal/modules/esm/loader:485:26)
        at async asyncRunEntryPointWithESMLoader (node:internal/modules/run_main:109:5)

    Node.js v22.4.0
  ```

  - set `type` in `backend/package.json` to `commonjs`
  - try running `npm run dev` again. This time the error will be gone and the code will print "Hello World" to the console
