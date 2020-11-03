# GIT提交规范

源代码的管理通常基于 GIT平台，在日常的开发中需要对 Commit 进行规范。业界用的比较多的是 `Angular` 规范。可以参考[阮一峰博客](http://www.ruanyifeng.com/blog/2016/01/commit_message_change_log.html)。每个 commit 都应该清晰明了且颗粒度适中，不允许一次性提交糅杂各个模块的所有改动，例如：一个 commit 同时包含“修复了模块 A 的一个 Bug”、“实现了模块 B 的两个新功能”和“重构了模块 C 的小部分代码”。这样的 commit 是不允许的。

## 规范说明
Commit message 格式：`<type>(<scope>): <subject>`。  
举个例子：
* fix: 修复 functionA 偶尔崩溃的问题
* feat(moduleA): 完成 moduleA 的基本功能
* style(moduleB): 格式化 moduleB 的代码
* chore: upgrade dependencies
* docs: update README

**type**  
用于说明 commit 的类型，可以使用如下几个类型

* `feat`：新功能
* `fix`：修复 Bug
* `docs`：文档
* `style`：调整代码格式
* `refactor`：重构代码
* `test`：测试
* `chore`：打包与构建的变动
* `perf`: 提升页面性能

**scope**  
用于补充说明 commit 的影响范围，如：模块 A、模块 B、模块 C。  

**subject**  
用于简述 commit 的内容。要求：

* 以动词开头
* 如果是英文，第一个字母小写，使用第一人称现在时。如：change XXX，而不是 changed 或 changes
* 结尾不加句号或其它标点符号


## 提交频率

每次写完一个功能的时候，就应该做一次提交（这个提交是指提交到本地的git库中）