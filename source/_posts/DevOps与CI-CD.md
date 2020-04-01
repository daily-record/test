---
title: DevOps与CI/CD
author: 霜雨
top: false
cover: true
coverImg: false
toc: true
mathjax: false
date: 2020-03-31 12:08:04
img:
password:
summary: 简单了解了DevOps与CI/CD的概念
categories:
tags:
    - DevOps
    - CI
    - CD
---

## DevOps

#### 定义

> DevOps 一词的来自于 Development 和 Operations 的组合，突出重视软件开发人员和运维人员的沟通合作，通过自动化流程来使得软件构建、测试、发布更加快捷、频繁和可靠

DevOps 其实包含了三个部分:

- 开发
- 测试
- 运维

一个团队中各个角色存在天然上的工作矛盾：
![](https://raw.githubusercontent.com/daily-record/daily-record-img/master/20200331144227.png)

对于运维来说，稳定性压到一切，新feature越少越好；而对于研发来说，能够开发的新功能越多越好，这种矛盾会导致大量资源的浪费。

DevOps 希望将产品交付过程中各种壁垒打破，让Dev和Ops一体化，通过自动化工具辅助开发完成运维的部分工作，减少成本。

</br>

#### 概述工作流

##### 传统工作流

PD(Demond) -> [DEV(Coding) -> SCM(Build) -> QA(Test) -> OPS(Deploy)]-> Release
PD 提出需求 -> [开发者根据需求写代码 -> SCM 拿着代码去打包 -> QA 测试 -> 运维进行上线部署]

</br>

#### DevOps工作流

通过高度自动化工具与流程来使得软件构建、测试、发布更加快捷、频繁和可靠；

同时，`CI/CD`（持续集成/持续部署）可看作传统工作流的增强版；`DevOps` 可看作是 `CI/CD` 的增强版。

![](https://raw.githubusercontent.com/daily-record/daily-record-img/master/20200331150116.png)

![](https://raw.githubusercontent.com/daily-record/daily-record-img/master/20200331150144.png)

</br>

## CI与CD

CI/CD 是一种通过在应用开发阶段引入自动化来频繁向客户交付应用的方法。CI/CD 的核心概念是持续集成、持续交付和持续部署。

不过，由于还需要编写自动化测试以适应 CI/CD 管道中的各种测试和发布阶段，因此前期投资还是会很大。

- CI:持续集成(Continuous Integration)
- CD:
    - 持续交付(Continuous Delivery)
    - 持续部署(Continuous Deployment)

</br>

#### 持续集成

**持续集成指的是，频繁地（一天多次）将代码集成到主干。**

持续集成可以帮助开发人员更加频繁地（有时甚至每天）将代码更改合并到共享分支或“主干”中。一旦开发人员对应用所做的更改被合并，系统就会通过自动构建应用并运行不同级别的自动化测试（通常是单元测试和集成测试）来验证这些更改，确保这些更改没有对应用造成破坏。这意味着测试内容涵盖了从类和函数到构成整个应用的不同模块。如果自动化测试发现新代码和现有代码之间存在冲突，CI 可以更加轻松地快速修复这些错误。

</br>

##### 目的

**让产品可以快速迭代，同时还能保持高质量。**它的核心措施是，代码集成到主干之前，**必须通过自动化测试**。只要有一个测试用例失败，就不能集成。

</br>

##### 好处

1. **快速发现错误。**每完成一点更新，就集成到主干，可以快速发现错误，定位错误也比较容易。
2. **防止分支大幅偏离主干。**如果不是经常集成，主干又在不断更新，会导致以后集成的难度会非常的大，甚至难以集成。

> 持续集成并不能消除Bug，而是让它们非常容易发现和改正。

</br>

#### 持续交付

**持续交付指的是，频繁地将软件的新版本，交付给质量团队或者用户，以供评审。**如果评审通过，代码就进入生产阶段。

在持续交付中，每个阶段（从代码更改的合并，到生产就绪型构建版本的交付）都涉及测试自动化和代码发布自动化。在流程结束时，运维团队可以快速、轻松地将应用部署到生产环境中。

持续交付可以看作持续集成的下一步。它强调的是，不管怎么更新，软件是随时随地可以交付的。

</br>

#### 持续部署

**持续部署是持续交付的下一步，指的是代码通过评审以后，自动部署到生产环境。**

持续部署的目标是，代码在任何时刻都是可部署的，可以进入生产阶段。

持续部署的前提是能自动化完成测试、构建、部署等步骤。

持续部署意味着开发人员对应用的更改在编写后的几分钟内就能生效（假设它通过了自动化测试）。这更加便于持续接收和整合用户反馈。总而言之，所有这些 CI/CD 的关联步骤都有助于降低应用的部署风险，因此更便于以小件的方式（而非一次性）发布对应用的更改。

</br>

## 工作流程

#### DevOps工具链

![](https://raw.githubusercontent.com/daily-record/daily-record-img/master/20200331175003.png)

- 版本控制&协作开发：GitHub、GitLab、BitBucket、SubVersion、Coding、Bazaar
- 自动化构建和测试: Apache Ant、Maven 、Selenium、PyUnit、QUnit、JMeter、Gradle、PHPUnit
- 持续集成&交付:Jenkins、Capistrano、BuildBot、Fabric、Tinderbox、Travis CI、flow.ci Continuum、LuntBuild、CruiseControl、Integrity、Gump、Go
- 容器平台: Docker、Rocket、Ubuntu（LXC）、第三方厂商如（AWS/阿里云）
- 配置管理：Chef、Puppet、CFengine、Bash、Rudder、Powershell、RunDeck、Saltstack、Ansible
- 微服务平台：OpenShift、Cloud Foundry、Kubernetes、Mesosphere
- 服务开通：Puppet、Docker Swarm、Vagrant、Powershell、OpenStack Heat
- 日志管理：Logstash、CollectD、StatsD
- 监控，警告&分析：Nagios、Ganglia、Sensu、zabbix、ICINGA、Graphite、Kibana

</br>

#### 1. 提交

开发者向代码仓库提交代码。所有后面的步骤都始于本地代码的一次提交（commit）。

</br>

#### 2. 测试（第一轮）

代码仓库对commit操作配置了钩子（hook），只要提交代码或者合并进主干，就会跑自动化测试。

测试分为多钟：
- 单元测试：针对函数或模块的测试
- 集成测试：针对整体产品的某个功能的测试，又称功能测试
- 端对端测试：从用户界面直达数据库的全链路测试

第一轮至少要跑单元测试。

</br>

#### 3. 构建

通过第一轮测试，代码就可以合并进主干，就算可以交付了。

交付后，就先进行构建（build），再进入第二轮测试。所谓构建，指的是将源码转换为可以运行的实际代码，比如安装依赖，配置各种资源（样式表、JS脚本、图片）等等。

常用的构建工具如下：
- Jenkins
- Travis
- Codeship
- Strider

</br>

#### 4. 测试（第二轮）

构建完成，就要进行第二轮测试。如果第一轮已经涵盖了所有测试内容，第二轮可以省略，当然，这时构建步骤也要移到第一轮测试前面。

第二轮是全面测试，单元测试和集成测试都会跑，有条件的话，也要做端对端测试。所有测试以自动化为主，少数无法自动化的测试用例，就要人工跑。

需要强调的是，新版本的每一个更新点都必须测试到。如果测试的覆盖率不高，进入后面的部署阶段后，很可能会出现严重的问题。

</br>

#### 5. 部署

通过了第二轮测试，当前代码就是一个可以直接部署的版本（artifact）。将这个版本的所有文件打包（ tar filename.tar * ）存档，发到生产服务器。

生产服务器将打包文件，解包成本地的一个目录，再将运行路径的符号链接（symlink）指向这个目录，然后重新启动应用。这方面的部署工具有Ansible，Chef，Puppet等。

</br>

#### 6. 回滚

一旦当前版本发生问题，就要回滚到上一个版本的构建结果。最简单的做法就是修改一下符号链接，指向上一个版本的目录。

</br>

## 参考链接

[阮一峰：持续集成是什么](http://www.ruanyifeng.com/blog/2015/09/continuous-integration.html)

[DevOps工作流](https://marlous.github.io/2018/10/31/DevOps%20%E4%B8%8E%20CICD%20%E7%9A%84%E6%A6%82%E5%BF%B5/#%E4%B8%89-DevOps-%E7%9F%A5%E8%AF%86%E5%9B%BE%E8%B0%B1)

[RedHat：什么是CI/CD](https://www.redhat.com/zh/topics/devops/what-is-ci-cd)
