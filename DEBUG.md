## Debugger

### Node built-in debugger
Debug lower-level languages such as C/C++, like GDB or LLDB:
```shell
$ node debug app.js
```

### node-inspector
```shell
$ npm -g i node-inspector
$ node-debug app.js
```

[webkit-devtools-agent](https://www.npmjs.com/package/webkit-devtools-agent) covers Devtools-based heap and CPU profiling

For script started with debug option:
```shell
$ node --debug app.js
# or pause on the first line
$ node --debug-brk app.js
$ node-inspector &
```
For running node
```
$ pgrep -l node 
# or
$ ps -ef | grep node
$ kill -s USR1 <pid>
$ node-inspector &
```
[Reference](http://blog.nodeknockout.com/post/34843655876/debugging-with-node-inspector)

## Debug logs
enable core API debug
```shell
$ NODE_DEBUG=http,net,fs,tls,module,timers node app.js
```
for non-core module, `debug` module can do the same thing
```shell
$ npm install debug --save
```
```javascript
var debug = require('debug');
var log = debug('tag:log');
var info = debug('tag:info');
var error = debug('tag:error');
log('debug log');
info('debug inof');
error('debug error');
```
```shell
$ DEBUG=* node app.js
$ DEBUG=tag:* node app.js
$ DEBUG=tag:info node app.js
```

add `debugger` in the code

## Stack traces
- `$ node -e "console.log('abc');"` node shell
- `#!/usr/bin/env node` node executable
- `longjohn` module can trace calls across ticks
- `cute-stack` supplies a variety of stack trace formats
