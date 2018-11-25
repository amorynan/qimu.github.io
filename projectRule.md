#项目开发流程中各种规范
tag ： 测试（alpha and beta， produce）
alpha -- 一般指开发内部使用，内部测试，bug比较多的情况
beta -- 一般在alpha之后，修复了大部分的bug， 但是还是有， 会只提供给特定的人员使用测试
produce -- 线上环境了

tag : 各种工具使用
maven - 依赖管理工具来管理项目的生命周期，将一个大的project 分成各个模块，然后programmer在各自的模块中进行开发，如果模块A 以来模块B， 模块B 依赖模块C， 那么Maven就会将模块A 依赖模块C

常见的maven 命令
mvn clean -- 清理项目打包文件，即项目下的target目录
mvn compile -- compile project中的src/main/java source code
mvn package -- package project, 在target下生成jar
mvn install -- package and publish to local repo
mvn depoly -- package and publish to remote repo
mvn test --单元测试命令，执行src/test/java/下的junit的单元测试用例
mvn site -- 生成项目相关信息的网站

every project 都会有一个pox.xml
配置的结点含义(imp)：
1. modelversion - maven 模型版本
2. groupid - 项目的组织，一般是顶级域名名称＋公司或者组织名称，如alibaba的项目组织为com.alibaba，如果你们公司的域名为www.abc.com，
3. artifactId -- 项目名称
（ps ： 例子来一波:<groupId>com.qunhe.instdeco</groupId>
    <artifactId>decoration-param-editor-service</artifactId>）
4. dependency -- 添加的依赖（几个重要的node）
	4.1 scope : 依赖范围（compile ， provided， runtime， test， system， import）
	4.2 exclusion : 依赖排除，（适用场景 ： A 依赖B ， c2.0 ; B 依赖C1.0 ，A就会冲突， 那么需要依赖排除）
	eg：
    ```
<groupId>org.testgroupId>
	<artifactId>B</artifactId>
	<version>1.0</version>
	<exclusions>
		<exclusion>
			<groupId>com.test</groupId>
			<artifactId>C</artifactId>
		</exclusion>
	</exclusions>
```

    or ：排除所有的间接依赖
    ```
        <groupId>org.test<groupId>
	<artifactId>B</artifactId>
	<version>1.0</version>
	<exclusions>
		<exclusion>
			<groupId>*</groupId>
			<artifactId>*</artifactId>
		</exclusion>
	</exclusions>
    ```
