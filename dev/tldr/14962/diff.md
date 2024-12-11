# tmt, tmt-run, tmt-try: add Chinese translation

```bash
# 1 - TMT issue
https://github.com/teemtee/tmt/issues/968
# 2 - Martin's  PR
https://github.com/tldr-pages/tldr/pull/14921
# 3 - Huanian's PR
https://github.com/tldr-pages/tldr/pull/14962
```

## 1 `diff -u ../../pages/linux/tmt.md tmt.md`

```patch
--- ../../pages/linux/tmt.md	2024-11-26 09:41:54.657850534 +0800
+++ tmt.md	2024-11-26 09:57:39.128728061 +0800
@@ -1,37 +1,37 @@
 # tmt

-> Test Management Tool for creating, running, and debugging tests.
-> Some subcommands such as `run`, `try`, etc. have their own usage documentation.
-> More information: <https://tmt.readthedocs.io>.
+> 创建、运行和调试测试的测试管理工具。
+> 诸如`运行`、`尝试`等子命令，均有相应的用法文档。
+> 更多信息：<https://tmt.readthedocs.io>.

-- List available tests, plans, and stories:
+- 列举可用的测试、计划和用户故事：

 `tmt`

-- Initialize tmt files/project structure:
+- 初始化测试管理工具的文件/项目结构：

 `tmt init`

-- Create a new test with a template and a link:
+- 基于模板和链接创建新的测试：

 `tmt test create --template {{beakerlib}} --link {{verifies:issue#1234}}`

-- List available tests, plans, or stories:
+- 列出可用的测试、计划和用户故事：

 `tmt {{test|plan|story}} ls {{pattern}}`

-- Show detailed test metadata in the given context:
+- 在给定的上下文中显示详细的测试元数据：

 `tmt --context {{arch=aarch64}} test show`

-- Validate tmt files against the specification:
+- 根据说明书验证测试管理工具文件的有效性：

 `tmt lint`

-- Use filter:
+- 使用筛选条件：

 `tmt tests ls --filter {{tag:foo}} --filter {{tier:0}}`

-- Display help:
+- 显示帮助：

 `tmt --help`
```


## 2 `diff -u ../../pages/linux/tmt-run.md tmt-run.md`
```patch
--- ../../pages/linux/tmt-run.md	2024-11-26 09:41:54.657850534 +0800
+++ tmt-run.md	2024-11-26 09:57:39.183728636 +0800
@@ -1,36 +1,36 @@
 # tmt run

-> Execute tmt test steps. By default, all steps are run.
-> More information: <https://tmt.readthedocs.io/en/stable/overview.html#run>.
+> 执行测试步骤。默认情况下，所有测试步骤都被执行。
+> 更多信息：<https://tmt.readthedocs.io/en/stable/overview.html#run>.

-- Run all test steps for each plan:
+- 在每一个计划中执行所有测试步骤：

 `tmt run`

-- Run only the discover step to show what tests would be run:
+- 仅在发现步骤中显示将要执行的测试：

 `tmt run discover -v`

-- Run all steps and adjust the provision step options:
+- 运行所有测试步骤并调整测试环境配置步骤选项：

 `tmt run --all provision --how {{container}} --image {{fedora:rawhide}}`

-- Run only selected plans and tests:
+- 仅执行选定的计划和测试：

 `tmt run plan --name {{/plan/name}} test --name {{/test/name}}`

-- Show results from the last run in a web browser:
+- 在网页浏览器中显示上次运行的结果：

 `tmt run --last report --how {{html}} --open`

-- Run tests with the provided context:
+- 在提供的上下文中运行测试：

 `tmt run --context {{key=value}} -c {{distro=fedora}}`

-- Run tests interactively (debug test code in the middle of a test):
+- 以交互方式运行测试（在测试运行过程中调试测试代码）：

 `tmt run --all execute --how {{tmt}} --interactive`

-- Use dry mode to see what actions would happen and use the highest verbosity:
+- 使用干模式查看接下来将发生的动作，并将输出详实度设置为最高级：

 `tmt run --dry -vvv`
```


## 3 `diff -u ../../pages/linux/tmt-try.md tmt-try.md`
```patch
--- ../../pages/linux/tmt-try.md	2024-11-26 09:41:54.657850534 +0800
+++ tmt-try.md	2024-11-26 09:57:39.214728960 +0800
@@ -1,36 +1,36 @@
 # tmt try

-> Quickly experiment with tests and environments.
-> More information: <https://tmt.readthedocs.io/en/stable/stories/cli.html#try>.
+> 测试及环境快速上手。
+> 更多信息：<https://tmt.readthedocs.io/en/stable/stories/cli.html#try>.

-- Quickly experiment with the default provision method (no tests in the CWD):
+- 快速尝试默认的测试环境配置方法（当前工作目录中没有测试）：

 `tmt try`

-- Run a test in the current working directory:
+- 在当前的工作目录中运行一个测试：

 `cd {{path/to/test}} && tmt try`

-- Use a specific operating system:
+- 使用特定的操作系统：

 `tmt try {{fedora-41}}`

-- Select both custom image and provision method:
+- 选择定制的镜像和测试环境配置方法：

 `tmt try {{fedora@container}}`

-- Select tests with custom filter:
+- 根据定制的筛选条件选择测试：

 `tmt try --test {{feature}}`

-- Provision guest and wait for instructions:
+- 配置客户机并等待用户输入指令：

 `tmt try --ask`

-- Directly log into the guest without asking:
+- 直接登录到客户机：

 `tmt try --login`

-- Display help:
+- 显示帮助：

 `tmt try --help`
```
