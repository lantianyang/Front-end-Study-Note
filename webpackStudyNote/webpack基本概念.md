# 基本环境

+ Nodejs 10版本以上
 + webpack 4.26版本以上

# webpack简介

+ webpack是一种前端资源构建工具，静态模块打包器（module bundler）
+ 在webpack中，前端所有的资源文件都会被作为模块处理（.less/.json/.jsx/.png）
 + 根据模块的依赖关系进行静态分析，打包生成对应的静态资源（bundle）

# webpack五个核心概念

+ Entry
  + 入口（Entry）Webpack以哪个文件为入口开始打包。

+ Output
  + 输出（Output）指示webpack打包之后的文件bundles输出到哪里，以及命名。

+ Loader
  + Loader让webpack能解析非js和json文件（webpack自身只能解析js和josn）。

+ Plugins
  + 插件（Plugins）可以用于执行范围更广的任务。插件的范围包括，从打包优化和压缩，一直到重新定义环境变量。

+ Mode
  + 模式（Mode）指示webpack使用相应模式的配置。

|         选项       |                                     描述                               |               特点                |
|------------|-----------------------------------------|--------------------|
| development | 会将process.env.NODE_ENV的值改为development。</br> 启用NamedChunksPlugin和NamedModulesPlugin。 | 能让代码本地调试运行的环境 |
| production | 会将process.env.NODE_ENV的值改为production。</br> 启用FlagDependencyUsagePlugin、FlagIncludedChunksPlugin、ModuleConcatenationPlugin、NoEmitOnErrorsPlugin、OccurrenceOrderPlugin、SideEffectsFlagPlugin、UglifyJsPlugin | 能让代码优化上线运行的环境 |
