This repository provides a reproducer for https://github.com/github/local-action/issues/168 on Windows.

Failure without `type: "module"` in package.json:
```
$ npm run local-action

> typescript-action@0.0.0 local-action
> npx @github/local-action . src/main.ts .env

     _        _   _               ____       _                                 
    / \   ___| |_(_) ___  _ __   |  _ \  ___| |__  _   _  __ _  __ _  ___ _ __
   / _ \ / __| __| |/ _ \| '_ \  | | | |/ _ \ '_ \| | | |/ _` |/ _` |/ _ \ '__|
  / ___ \ (__| |_| | (_) | | | | | |_| |  __/ |_) | |_| | (_| | (_| |  __/ |
 /_/   \_\___|\__|_|\___/|_| |_| |____/ \___|_.__/ \__,_|\__, |\__, |\___|_|
                                                         |___/ |___/
================================================================================
                                 Configuration
================================================================================

┌─────────┬────────────────────┬──────────────────────────────────────────────────────────────────┐
│ (index) │ Field              │ Value                                                            │
├─────────┼────────────────────┼──────────────────────────────────────────────────────────────────┤
│ 0       │ 'Action Path'      │ 'C:\\git\\reproduce-local-action-issue-168'               │
│ 1       │ 'Entrypoint'       │ 'C:\\git\\reproduce-local-action-issue-168\\src\\main.ts' │
│ 2       │ 'Environment File' │ 'C:\\git\\reproduce-local-action-issue-168\\.env'         │
└─────────┴────────────────────┴──────────────────────────────────────────────────────────────────┘

================================================================================
                                Action Metadata
================================================================================

┌─────────┬────────────────┬───────────────────────────────┐
│ (index) │ Input          │ Description                   │
├─────────┼────────────────┼───────────────────────────────┤
│ 0       │ 'milliseconds' │ 'Your input description here' │
└─────────┴────────────────┴───────────────────────────────┘

┌─────────┬────────┬────────────────────────────────┐
│ (index) │ Output │ Description                    │
├─────────┼────────┼────────────────────────────────┤
│ 0       │ 'time' │ 'Your output description here' │
└─────────┴────────┴────────────────────────────────┘


================================================================================
                                 Running Action
================================================================================

node:internal/modules/cjs/loader:1225
  const err = new Error(message);
              ^

Error: Cannot find module 'C:\C:\git\reproduce-local-action-issue-168\src\main.ts'
Require stack:
- C:\git\reproduce-local-action-issue-168\node_modules\@github\local-action\src\commands\run.ts
    at Module._resolveFilename (node:internal/modules/cjs/loader:1225:15)
    at Module._resolveFilename (C:\git\reproduce-local-action-issue-168\node_modules\@github\local-action\node_modules\tsconfig-paths\lib\register.js:103:40)
    at nextResolveSimple (C:\git\reproduce-local-action-issue-168\node_modules\tsx\dist\register-DCnOAxY2.cjs:3:942)
    at C:\git\reproduce-local-action-issue-168\node_modules\tsx\dist\register-DCnOAxY2.cjs:2:2550
    at C:\git\reproduce-local-action-issue-168\node_modules\tsx\dist\register-DCnOAxY2.cjs:2:1624
    at resolveTsPaths (C:\git\reproduce-local-action-issue-168\node_modules\tsx\dist\register-DCnOAxY2.cjs:3:760)
    at C:\git\reproduce-local-action-issue-168\node_modules\tsx\dist\register-DCnOAxY2.cjs:3:1038
    at m._resolveFilename (file:///C:/git/reproduce-local-action-issue-168/node_modules/tsx/dist/register-RyGUjI6j.mjs:1:789)
    at doWithoutCache (C:\git\reproduce-local-action-issue-168\node_modules\quibble\lib\quibble.js:199:27)
    at Function.fakeLoad [as _load] (C:\git\reproduce-local-action-issue-168\node_modules\quibble\lib\quibble.js:171:12) {
  code: 'MODULE_NOT_FOUND',
  requireStack: [
    'C:\\git\\reproduce-local-action-issue-168\\node_modules\\@github\\local-action\\src\\commands\\run.ts'
  ]
}

Node.js v20.18.1
```

Failure with `type: "module"` in package.json:
```
$ npm run local-action

> typescript-action@0.0.0 local-action
> npx @github/local-action . src/main.ts .env

     _        _   _               ____       _
    / \   ___| |_(_) ___  _ __   |  _ \  ___| |__  _   _  __ _  __ _  ___ _ __ 
   / _ \ / __| __| |/ _ \| '_ \  | | | |/ _ \ '_ \| | | |/ _` |/ _` |/ _ \ '__|
  / ___ \ (__| |_| | (_) | | | | | |_| |  __/ |_) | |_| | (_| | (_| |  __/ |   
 /_/   \_\___|\__|_|\___/|_| |_| |____/ \___|_.__/ \__,_|\__, |\__, |\___|_|   
                                                         |___/ |___/
================================================================================
                                 Configuration
================================================================================

┌─────────┬────────────────────┬──────────────────────────────────────────────────────────────────┐
│ (index) │ Field              │ Value                                                            │
├─────────┼────────────────────┼──────────────────────────────────────────────────────────────────┤
│ 0       │ 'Action Path'      │ 'C:\\git\\reproduce-local-action-issue-168'               │
│ 1       │ 'Entrypoint'       │ 'C:\\git\\reproduce-local-action-issue-168\\src\\main.ts' │
│ 2       │ 'Environment File' │ 'C:\\git\\reproduce-local-action-issue-168\\.env'         │
└─────────┴────────────────────┴──────────────────────────────────────────────────────────────────┘

================================================================================
                                Action Metadata
================================================================================

┌─────────┬────────────────┬───────────────────────────────┐
│ (index) │ Input          │ Description                   │
├─────────┼────────────────┼───────────────────────────────┤
│ 0       │ 'milliseconds' │ 'Your input description here' │
└─────────┴────────────────┴───────────────────────────────┘

┌─────────┬────────┬────────────────────────────────┐
│ (index) │ Output │ Description                    │
├─────────┼────────┼────────────────────────────────┤
│ 0       │ 'time' │ 'Your output description here' │
└─────────┴────────┴────────────────────────────────┘


================================================================================
                                 Running Action
================================================================================


node:internal/process/promises:391
    triggerUncaughtException(err, true /* fromPromise */);
    ^
Error [ERR_MODULE_NOT_FOUND]: Cannot find module 'C:\git\reproduce-local-action-issue-168\lib\github.js' imported from C:\git\reproduce-local-action-issue-168\node_modules\quibble\lib\esm-import-functions.js
    at finalizeResolution (node:internal/modules/esm/resolve:265:11)
    at moduleResolve (node:internal/modules/esm/resolve:933:10)
    at defaultResolve (node:internal/modules/esm/resolve:1169:11)
    at nextResolve (node:internal/modules/esm/hooks:868:28)
    at resolveBase (file:///C:/git/reproduce-local-action-issue-168/node_modules/tsx/dist/esm/index.mjs?1742976235415:2:3212)
    at resolveDirectory (file:///C:/git/reproduce-local-action-issue-168/node_modules/tsx/dist/esm/index.mjs?1742976235415:2:3584)
    at resolveTsPaths (file:///C:/git/reproduce-local-action-issue-168/node_modules/tsx/dist/esm/index.mjs?1742976235415:2:4073)
    at resolve (file:///C:/git/reproduce-local-action-issue-168/node_modules/tsx/dist/esm/index.mjs?1742976235415:2:4447)
    at nextResolve (node:internal/modules/esm/hooks:868:28)
    at resolve (file:///C:/git/reproduce-local-action-issue-168/node_modules/quibble/lib/quibble.mjs:25:5) {
  code: 'ERR_MODULE_NOT_FOUND',
  url: 'file:///C:/git/reproduce-local-action-issue-168/lib/github.js'
}

Node.js v20.18.1
```