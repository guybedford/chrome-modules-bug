Chrome ES modules circular error case

Open test.html in Chrome Canary with ES modules enabled, and there is a resolve error due to the circular reference resolution.

The following alteration can reduce the error to, instead of happening everytime, only happening sporadically:

Comment out the require to `g.js` in `b.js`:

`b.js`:
```js
import './b.js';
// import './g.js';
```

The exact error shown reads:

```
Uncaught TypeError: Failed to execute 'resolveModuleCallback' on 'ScriptModule': Failed to load module script for module specifier './g.js'
```
