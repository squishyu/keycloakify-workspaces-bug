# Keycloakify ENOWORKSPACES reproduction repo

Simple repository for reproducing an issue with Keycloakify when used inside Yarn/NPM Workspaces [(Keycloakify issue #380)](https://github.com/keycloakify/keycloakify/issues/380)

## What's the problem?

When running a simple NPM/Yarn install while using NPM version 9+ (included in Node 18.14+), NPM throws the following error:

```
node:internal/errors:867
  const err = new Error(message);
              ^

Error: Command failed: npm config get
npm ERR! code ENOWORKSPACES
npm ERR! This command does not support workspaces.

npm ERR! A complete log of this run can be found in: .../.npm/_logs/2023-07-13T07_38_57_081Z-debug-0.log

    at ChildProcess.exithandler (node:child_process:419:12)
    at ChildProcess.emit (node:events:513:28)
    at maybeClose (node:internal/child_process:1091:16)
    at ChildProcess._handle.onexit (node:internal/child_process:302:5) {
  code: 1,
  killed: false,
  signal: null,
  cmd: 'npm config get',
  stdout: '',
  stderr: 'npm ERR! code ENOWORKSPACES\n' +
    'npm ERR! This command does not support workspaces.\n' +
    '\n' +
    'npm ERR! A complete log of this run can be found in: .../.npm/_logs/2023-07-13T07_38_57_081Z-debug-0.log\n'
}

Node.js v18.16.0
```

## How to reproduce

The repo is set up with the `yarn` package manager, simply run `yarn install` at the repository root (or inside `/packages/keycloakify`) with NPM 9+ to reproduce the issue.

To check your `npm` version, you can run `npm --version`.
