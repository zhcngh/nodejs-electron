 
 #通过官方quick-start demo来模拟项目

 ## 1.安装项目 
      git clone https://github.com/electron/electron-quick-start
      cd electron-quick-start
      npm install
      npm start

 ## 2. 安装electron-prebuilt
      npm install –save-dev electron-prebuilt
      
 ## 3. 安装gulp构建工具
      npm install -g gulp
      全局安装后，再在本地安装一次
      npm install gulp
      
 ## 4. 新建一个gulpfile.js文件

        `
          // 获取依赖
          var gulp = require('gulp'), 
            childProcess = require('child_process'), 
            electron = require('electron-prebuilt');
          // 创建 gulp 任务
          gulp.task('run', function () { 
            childProcess.spawn(electron, ['.'], { stdio: 'inherit' }); 
          });
        `

        使用命令 gulp run 应该是可以跑起来程序的
 ## 5. 在.VSCode文件夹中新建一个tasks.json文件

      `
              {
            "version": "0.1.0", 
            "command": "gulp", 
            "isShellCommand": true, 
            "args": [
                "--no-color"
            ], 
            "tasks": [
                {
                    "taskName": "run", 
                    "args": [ ], 
                    "isBuildCommand": true
                }
            ]
        }
      `

 ## 6. 配置调试启动环境
      按F5 会出来选择调试环境， 选择 Node.js
      vscode会生成一个launch.json文件
      修改 runtimeExecutable:""

      `
      "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "启动程序",
            "program": "${workspaceRoot}\\main.js",
            "cwd": "${workspaceRoot}",
            "runtimeExecutable": "${workspaceRoot}/node_modules/electron-prebuilt/dist/electron.exe"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "附加到进程",
            "port": 5858
        }
      `

 ## 7.下断点，调试 
 
