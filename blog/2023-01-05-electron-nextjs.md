---
slug: electron-nextjs
title: Electron + Next.js셋팅
authors: gimso2x
tags: [Electron, Next.js]
---

### 1. NextJs 설치

```jsx
npx create-next-app
```

### 2. electron 폴더 및 index.js, preload.js 추가

> index.js

```jsx
// Native
const { join } = require("path");
const { format } = require("url");

// Packages
const { BrowserWindow, app, ipcMain } = require("electron");
const isDev = require("electron-is-dev");
const prepareNext = require("electron-next");

// Prepare the renderer once the app is ready
app.on("ready", async () => {
  await prepareNext("./");

  const mainWindow = new BrowserWindow({
    width: 800,
    height: 600,
    webPreferences: {
      nodeIntegration: false,
      preload: join(__dirname, "preload.js"),
    },
  });

  const url = isDev
    ? "http://localhost:8000"
    : format({
        pathname: join(__dirname, "../out/index.html"),
        protocol: "file:",
        slashes: true,
      });

  mainWindow.loadURL(url);
});

// Quit the app once all windows are closed
app.on("window-all-closed", app.quit);

// listen the channel `message` and resend the received message to the renderer process
ipcMain.on("message", (event, message) => {
  event.sender.send("message", message);
});
```

>preload.js

```jsx
const { ipcRenderer, contextBridge } = require("electron");

contextBridge.exposeInMainWorld("electron", {
  message: {
    send: (payload) => ipcRenderer.send("message", payload),
    on: (handler) => ipcRenderer.on("message", handler),
    off: (handler) => ipcRenderer.off("message", handler),
  },
});
```

### 3. package.json 내용 수정

```json
{
  "name": "elec",
  "version": "0.1.0",
  "private": true,
  "description": "Hello World!",
  "main": "electron/index.js",
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "clean": "rimraf dist out .next",
    "electron:start": "electron .",
    "electron:build": "next build && next export",
    "electron:dist": "npm run electron:build && electron-builder"
  },
  "dependencies": {
    "electron-is-dev": "^2.0.0",
    "electron-next": "^3.1.5",
    "eslint-config-prettier": "^8.5.0",
    "next": "12.3.1",
    "react": "18.2.0",
    "react-dom": "18.2.0"
  },
  "devDependencies": {
    "electron": "^21.1.0",
    "electron-builder": "^23.6.0",
    "eslint": "8.25.0",
    "eslint-config-next": "^12.3.1"
  },
  "build": {
    "asar": true,
    "files": [
      "electron",
      "out"
    ]
  }
}
```

### 4. eslintrc.json 수정

```jsx
{
  "root":true,
  "extends": ["next/core-web-vitals", "prettier"]
}
```

#### 참조링크

<https://www.notion.so/Electron-Next-js-URL-282af8db7a3b4588b71122fc18d3eaf8#ff0602d1c7264aa699b87ffc20e00538>
<https://youtu.be/oAaS9ix8pes>
<https://github.com/vercel/next.js/tree/canary/examples/with-electron>
<https://kingsubin.tistory.com/475>
