## npm命令说明
1. devDependencies 下的模块是我们在开发时需要用的 打包上线之后用不到会自动脱离 比如代码检查规范，压缩代码功能这些上线用不到
2. dependencies	下的模块是上线之后也需要用到的，比如vue-router

### npm install
1. 根据项目中package.json中的配置说明来安装所需要的包

### npm install moduleName 
1. 安装模块到项目node_modules目录下
2. 不会将模块依赖写入devDependencies或dependencies节点
3. 运行 npm install 初始化项目时不会下载模块

### npm install -g moduleName 
1. 安装模块到全局，不会在项目node_modules目录中保存模块包。
2. 不会将模块依赖写入devDependencies或dependencies节点
3. 运行 npm install 初始化项目时不会下载模块。

### npm install --save-dev moduleName
1. 安装模块到项目node_modules目录下。
2. 会将模块依赖写入devDependencies 节点。
3. 运行 npm install 初始化项目时，会将模块下载到项目目录下。
4. 运行npm install --production或者注明NODE_ENV变量值为production时，不会自动下载模块到node_modules目录中

### npm install --save moduleName
1. 安装模块到项目node_modules目录下。
2. 会将模块依赖写入dependencies 节点。
3. 运行 npm install 初始化项目时，会将模块下载到项目目录下。
4. 运行npm install --production或者注明NODE_ENV变量值为production时，会自动下载模块到node_modules目录中。