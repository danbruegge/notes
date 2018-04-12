yarn lock file merge conflict
=============================
```bash
rm yarn.lock && yarn && git add yarn.lock
 ```

npm lock file merge conflict
============================
```bash
rm package-lock.json && npm shrinkwrap && mv npm-shrinkwrap.json package-lock.json
 ```

