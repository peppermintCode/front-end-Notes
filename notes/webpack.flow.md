- shell与config解析，生成options
    - 使用optimist解析node行，将命令行参数保存以键值对形式保存在optimist.argv中
    - 将webpack.config.js拷贝到options中，并加载webpack.config.js中的plugins
    - 判断optimist.argv中参数，决定是否去加载对应插件
    - 生成options,,其中包含之后构建需要的重要信息,用于初始化webpack
- 编译与构建
    - 根据options初始化webpack对象complier
        - 从webpack启动到结束只存在一个Compiler，Compiler存放着webpack配置
    - complier执行run方法，执行完后触发complie事件，构建compilication对象
        - compilation代表一次编译，负责整个编译过程
        - 存放了所有modules,chunks,生成的assets
    - complier执行make方法
        - 在options中的找到入口点，进行分析模块及其依赖的模块，创建这些模块对象
    - 构建模块
        - 构建源文件
            - 调用loader解析源文件
            - 调用acorn构建AST
            - 遍历AST，记录依赖
        - 异步对依赖的module进行构建模块
    - 封装输出
        - compilication调用seal，生成编译后的源码,合并和拆分
        - 每个chunk代表一个入口文件
    - 打包
        - compilation调用createChunkAssets，进行打包后代码的生成
- 输出
    - compiler调用emitAssets，根据options中的output将文件输出到对应path