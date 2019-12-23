---
title: Note - HEXO
date: 2017-03-04 17:47:49
description: How to start using Hexo?
---
### How to start?
1. Install Node.js.
2. Use `node -v` and `npm -v` to confirm the success of installation.
3. In stall Git.exe.
4. `git --version` to confirm.
5. `npm install hexo-cli -g`
6. `npm install hexo --save`
7. `hexo -v` to confirm it.
8. More details can be found [here](https://www.instapaper.com/read/875351959).

### How to deploy?
1. `hexo clean`
2. `hexo generate`
3. `hexo serever`
4. `hexo deploy`

### Err message -- `ERR! Cannot find module 'internal/util/types'`

After upgrading Node and install hexo again with `npm install hexo-cli -g`, an error message shows up.

`ERR! Cannot find module 'internal/util/types'`

This problem can be solve by deleting the folders

`C:\Users\youruser\AppData\Roaming\npm`

`C:\Users\youruser\AppData\Roaming\npm-cache`

### Err message -- ``libsass` bindings not found`

Delete the `node_modules`folder, then run `npm install`.

### Generate and deploy in existing blog folders

1. Go to the folder with relevant source folders. Run `npm install`
2. `hexo g`
3. `hexo d`





































