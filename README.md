# how-i-can-run-electronJs-app-in-my-Linux-Machine
  Folow this Steps and you will run it successfuly :>
   - sudo apt update
   - sudo apt install nodejs npm
   - mkdir electron-app
   - cd electron-app
   - npm init -y
   - npm install electron --save-dev
   - touch main.js index.html

     # // in main.js:
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

     # // index.html

     <code>
        <!DOCTYPE html.>
          <html.>
            <head.>
              <title>Hello Electron</title>
            </head.>
            <body.>
              <h1.>Hello Electron!</h1.>
            </body>.
            </html.>
     </code>

  <h4>make sur your package.json main and scripts property looks like that : </h4>
  {
      "main": "main.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "start": "electron ."
      }
  }


  # // and Now ?? :
  - npm start
   - if there sis error looks like that :
    - [17400:1225/160218.477228:FATAL:setuid_sandbox_host.cc(163)] The SUID sandbox helper binary was found, but is not configured correctly. Rather than run without sandboxing I'm aborting now. You need to make sure that /folder/user/electron-app/node_modules/electron/dist/chrome-sandbox is owned by root and has mode 4755./folder/user/electron-app/node_modules/electron/dist/electron exited with signal SIGTRAP

# that what you have to do :
- sudo chown root:root node_modules/electron/dist/chrome-sandbox && sudo chmod 4755 node_modules/electron/dist/chrome-sandbox
- npm start
Now it will run successfuly :>
 
