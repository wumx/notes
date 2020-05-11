

[TOC]

## git commit 基本规范

目前比较流行的规范是 [Angular团队规范](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines ) ，也可以使用其衍生  [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/ )

Angular 规范格式如下

```js
<type>(scope):<subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

* 标题行：**必填**   描述主要修改的类型，模块，大致内容
* 标题内容：选填    描述修改的原因，方式，以及开发思路
* 页脚注释： 选填   

### Revert

如果当前 commit 用于撤销以前的 commit，则必须以revert:开头，后面跟着被撤销 commit 的 header。 

body部分的格式是固定的，必须写成`This reverts commit <hash>`，其中的hash是被撤销 commit 的 SHA 标识符。 

### Type

必须是以下的类型之一

* **feat**: 一个新的功能点(需求)
* **fix**: bug修正
* **docs**:文档修改
* **style**: 代码格式的修改( 空格，格式，缺少分号等等)(不是css的修改)
* **refactor**:代码重构
* **perf**：性能优化
* **test**: 测试用例修改
* **chore**：其他修改, 比如构建流程, 依赖管理 

### Scope

commit 的影响范围，例如 **Router**，**View**, **Store** 等等， 可以使用 ***** 代表影响任何一个地方

### Subject

简洁的描述提交的内容 ，建议使用 [50/72格式化](https://stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting )

### Body

commit 的具体内容，需在**header** **footer** 之间空一行 ;建议使用 [50/72 格式化](https://link.zhihu.com/?target=https%3A//stackoverflow.com/questions/2290016/git-commit-messages-50-72-formatting)

### Footer

* 不兼容变动 ：如果当前代码与上一个版本不兼容，则 Footer 部分以BREAKING CHANGE开头，后面是对变动的描述、以及变动理由和迁移方法 
* 关闭 Issue ：如果当前 commit 针对某个issue，那么可以在 Footer 部分关闭这个 issue 





