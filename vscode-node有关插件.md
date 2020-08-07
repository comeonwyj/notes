![Uploading 28.jpg… (3zlel8phx)]()

  **vscode插件大全**

@import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=true}

<!-- code_chunk_output -->

1. [代码提示[node 或jquery等第三方库]](#代码提示node-或jquery等第三方库)
2. [代码运行： Code Runner插件](#代码运行-code-runner插件)
3. [网页实时刷新： Liver Server插件](#网页实时刷新-liver-server插件)
4. [应用SCSS并实时刷新：Live Sass Compiler插件](#应用scss并实时刷新live-sass-compiler插件)
5. [markdown 相关插件](#markdown-相关插件)
    1. [1. markdown all in one](#1-markdown-all-in-one)
    2. [2. markdown preview enhanced](#2-markdown-preview-enhanced)
    3. [3. markdown shortcut](#3-markdown-shortcut)
    4. [4. markdown pdf](#4-markdown-pdf)
6. [TabNine强大的智能提示插件](#tabnine强大的智能提示插件)
7. [如何在注释和字符串里弹出提示：](#如何在注释和字符串里弹出提示)
8. [括号不同颜色 Bracket pair Colorizer](#括号不同颜色-bracket-pair-colorizer)
9. [在vscode里预览：Browser preview](#在vscode里预览browser-preview)
10. [更加容易的创建文件或文件夹：Faster New File And Folder](#更加容易的创建文件或文件夹faster-new-file-and-folder)
11. [代码美化 Beautify插件](#代码美化-beautify插件)
12. [为HTML添加css类提示：IntelliSence for Css class names In HTML 和 HTML CSS Support](#为html添加css类提示intellisence-for-css-class-names-in-html-和-html-css-support)
13. [路径输入提示：Path Autocomplete 和 Path Intellisenece](#路径输入提示path-autocomplete-和-path-intellisenece)
14. [跳出括号：TabOut](#跳出括号tabout)
15. [在vue或其他文件类型里使用emmet：](#在vue或其他文件类型里使用emmet)

<!-- /code_chunk_output -->


#### 代码提示[node 或jquery等第三方库]

 1. 安装typings：`npm install -g typings`  

 2. 在项目目录下，打开命令窗口，输入：`typings init`.这时当前目录下会出现一个typings.json的文件,类似npm的package.json.

 3. 在项目下安装nodejs,jquery等库的代码提示：
   `typings install dt~node --global--save`
   `typings install dt~jquery --global--save`
   （–global：代表全局文件，有些包必须得加上这个参数才行）
    （–save ：表示将此次的安装信息记录到上面讲的typings.json中）
    这时当前目录会出现一个名为typings的目录，此目录下便是一些提示文件
    > 如何查找dt ~的文件
    在命令行下输入：`typings search --name juqery|node|vue|angular等`
 4. 在项目目录下新建一个jsconfig.json空文件，这一步至关重要；当新建完此文件后，
 5. 重启VSCode就可以获得代码提示了.

----

> 对于typescript项目，需要用以下方法

1. 我们要安装node|jquery|sequelize的类型文件，可以直接使用：
   `npm install @types/node|jquery|sequelize --save-dev`
   如果被墙了，可以使用淘宝库：
   `$ npm install @types/jquery -save --registry=https://registry.npm.taobao.org`
安装完成后，我们在 node_modules目录下发现有一个@types目录，该目录里就是所安装的所有的类型声明文件。
2. 配置 jsconfig.json 文件
   ```json
    "include": [
        "model/**",
        "service/**"
    ],
    "typeAcquisition": {
        "include": [
            "node",
            "jquery",
            "sequelize"
        ]
    }
    //开启语义检查
    "compilerOptions": {
        "target": "es5",
        "module": "commonjs",
        "allowSyntheticDefaultImports": true,
        "checkJs": true
    },
    "exclude": [
        "node_modules"
    ]
   ```
   其中typeAcquisition参数是必配的，标识启用类型感知功能，里面的include标识对哪个包启用。
上面的include不是必须的，只是用来标识jsconfig.json文件对哪些文件起作用。
####代码运行： Code Runner插件
####网页实时刷新： Liver Server插件
####应用SCSS并实时刷新：Live Sass Compiler插件
1. 第一步  下载扩展Live Sass Compiler

2. 第二步 点状态栏的watch图标或快捷键 ctrl+shift+p 输入live 并选择Live Sass：Watch Sass

3. 第三步 在setting里设置：
```json
"liveSassCompile.settings.showOutputWindow": false,
 "liveSassCompile.settings.formats":[
        // This is Default.这是默认的
        {
            "format": "expanded",
            "extensionName": ".css",
            "savePath": null //表示当前目录
        },
        // You can add more
        {
            "format": "compressed",
            "extensionName": ".min.css",
            "savePath": "/dist/css"
        },
        // More Complex
        {
            "format": "compressed",
            "extensionName": ".min.css",
            "savePath": "~/../css/"
        }
    ]
```
####markdown 相关插件

#####1. markdown all in one
#####2. markdown preview enhanced
#####3. markdown shortcut
#####4. markdown pdf

####TabNine强大的智能提示插件
####如何在注释和字符串里弹出提示：
```json
    "editor.quickSuggestions": {
        "other": true,
        "comments": true,
        "strings": true
  },
```
####括号不同颜色 Bracket pair Colorizer
####在vscode里预览：Browser preview
####更加容易的创建文件或文件夹：Faster New File And Folder
####代码美化 Beautify插件
vue文件的代码美化设置
```json
"beautify.language": {    
    "js": {
      "type": [
        "javascript",
        "json",
        "jsonc",
        "vue"
      ],
      "filename": [
        ".jshintrc",
        ".jsbeautifyrc"
      ]
    },
    "css": [
      "css",
      "less",
      "scss",
      "vue"
    ],
    "html": [
      "htm",
      "html",
      "vue"
    ]
  }
```
####为HTML添加css类提示：IntelliSence for Css class names In HTML 和 HTML CSS Support

####路径输入提示：Path Autocomplete 和 Path Intellisenece
####跳出括号：TabOut

####在vue或其他文件类型里使用emmet：
```json
"emmet.includeLanguages": {
    "vue-html": "html",
    "vue": "html"
  },
```

@import "assets/27.jpg"

