# how-i-can-run-electronJs-app-in-my-Linux-Machine
  Folow this Steps and you will run it successfuly :>
  <code>
     - sudo apt update
    - sudo apt install nodejs npm
    - mkdir electron-app
    - cd electron-app
    - npm init -y
    - npm install electron --save-dev
    - touch main.js index.html
  </code>

  #  in main.js:
  <code>
        const { app, BrowserWindow } = require('electron')
        const path = require('path')
        function createWindow () {
              const win = new BrowserWindow({
                width: 800,
                height: 600
              })
              win.loadFile('index.html')
            }
       app.whenReady().then(() => {
              createWindow()
            })
       app.on('window-all-closed', () => {
              if (process.platform !== 'darwin') {
                app.quit()
              }
            })
     </code>

  # index.html
  <code>
      default Html page only to test
  </code>

  <h4>make sur your package.json main and scripts property looks like that : </h4>
  <code>
      {
      "main": "main.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "electron ."
      }
  }
  </code>


  # // and Now ?? :
  <code>
       - npm start
   - if there is error looks like that :
    - [17400:1225/160218.477228:FATAL:setuid_sandbox_host.cc(163)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /folder/user/electron-app/node_modules/electron/dist/chrome-sandbox is owned by root and has mode 4755./folder/user/electron-app/node_modules/electron/dist/electron exited with signal SIGTRAP
  </code>

# that what you have to do :
<code>
  - sudo chown root:root node_modules/electron/dist/chrome-sandbox && sudo chmod 4755 node_modules/electron/dist/chrome-sandbox
- npm start
</code>
Now it will run successfuly :>
 
