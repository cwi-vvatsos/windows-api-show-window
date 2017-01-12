# windows-api-show-window
>> Call ShowWindow from node via .NET

## What can I do with this?
Hide, show, maximize or minimize a window where you know either the window's hWnd or the process' PID.

The helper methods (methods not starting with "winApi") will only work when you are running node.exe as the main process, unlike running cmd.exe -> node, which makes cmd.exe the main process. This is because they use `process.pid` as the PID.

## Installing
```powershell
npm install --save windows-api-show-window
```

## Testing (manual only)
```powershell
// run with win + r
node {repository-location}/test/index.js
```

## Usage
```js
var api = require("windows-api-show-window");

api.hideCurrentProcessWindow().then(() => {
    // console window is hidden
}).catch(err => {
    console.error(err);
});

api.showCurrentProcessWindow().then(() => {
    // console window is visible
}).catch(err => {
    console.error(err);
});

api.maximizeCurrentProcessWindow().then(() => {
    // console window is maximized
}).catch(err => {
    console.error(err);
});

api.minimizeCurrentProcessWindow().then(() => {
    // console window is minimized
}).catch(err => {
    console.error(err);
});

api.restoreCurrentProcessWindow().then(() => {
    // console window is restored
}).catch(err => {
    console.error(err);
});
```

## Advanced usage
```js
api.winApiGetHwndFromPid(process.pid).then(hWnd => {
    // do something with hWnd
}).catch(err => {
    console.error(err);
});

api.winApiShowWindow(hWnd, api.SW_HIDE).then(() => {
    // custom calls to ShowWindow
}).catch(err => {
    console.error(err);
});
```

## Relevant
* [Windows Api ShowWindow documentation](https://msdn.microsoft.com/en-us/library/windows/desktop/ms633548.aspx)
* [sindresorhus/module-requests issue](https://github.com/sindresorhus/module-requests/issues/81)
