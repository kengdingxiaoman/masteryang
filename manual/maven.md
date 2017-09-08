# maven命令积累

## 常用命令
所有命令后面添加 -X，则会查看完整的运行过程，可以类比为没添加时是 info 级别，添加后就是 debug 级别了

### 项目删除并编译
mvn clean install

如果需要跳过执行测试用例，可以在后面加上 -Dmaven.test.skip=true，例如：
mvn clean install -Dmaven.test.skip=true

也可以添加 -DskipTests，-DskipTests 和 -Dmaven.test.skip=true 的异同点在于：<br/>

他们都会跳过 src/test/java中的JUnit测试用例，但是

- -DskipTests，不执行测试用例，但会编译测试用例类并生成相应的class文件到target/test-classes下。
- -Dmaven.test.skip=true，不执行测试用例，也不编译测试用例类。

### 查看 maven 项目和模块之间的依赖关系
mvn dependency:tree

- dependency:list 列出项目最终解析到的依赖列表
- dependency:tree 进一步的描绘项目依赖树
- dependency:analyze 恰如其名的分析项目依赖的潜在问题，如果有直接使用到但却未声明的依赖时，会发出警告

一般 dependency:tree 用到的比较多一些

### 显示 maven 版本
mvn -v
