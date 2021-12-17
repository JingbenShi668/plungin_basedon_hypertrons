本次Chaoss指标自动化翻译的工作，主要是及时捕捉Chaoss英文指标库的指标变化，然后使用GitHub app获取变化的文本并对其进行翻译。

本次自动化的指标翻译工作主要是使用到了hypertrons，一个优秀的开源协作机器人。🎉🎉🎉

项目运行流程如下(首先需要将该项目克隆在自己的本地): 

1、安装GitHub app - Menbotics，然后对Menbotics进行配置，允许其访问翻译工作所用到的仓库

<img src="https://git-course.oss-cn-shanghai.aliyuncs.com/Chaoss/ImagesForReadme/Menbotics.png" width = "1000" align=center />

2、对Hypertrons的四个核心配置文件进行配置，其中index.lua文件定义了具体的翻译逻辑，

<img src="https://git-course.oss-cn-shanghai.aliyuncs.com/Chaoss/ImagesForReadme/HypertronsArchitecture.png" height = "100" align=center />

3、未完待续~


# 结项报告

## 项目信息

- <b>项目名称</b>：CHAOSS指标中文自动化翻译
- <b>方案描述</b>：<br/>
           基于GitHub开源项目Hypertrons构建GitHub app， 将此GitHub app集成到"Chaoss指标翻译"对应的相关仓库，
           以此实现"Chaoss指标翻译"所需要的相关功能。
- <b>时间规划</b>：<br/>
           - 7/1-7/31： 了解Hypertrons的相关设计以及适用场景。<br/>
           - 8/1-8/20： 了解学习TypeScript以及Lua语法，为后面的脚本编写做准备。<br/>
           - 8/21-8/31：在自己本地运行Hypertrons实例，并将其发布到GitHub marketplace上，并将
                        其接入到项目所对应的GitHub仓库中。 <br/>
           - 9/1-9/20： 在项目所对应的仓库下编写Ts 以及Lua 脚本, 调用Hypertrons 的相关服务，实
                        现项目需求。<br/>
           - 9/20-9/30：与导师沟通交流，进一步完善自动化流程。

## 项目总结

- <b>项目产出</b>：

  本次暑期实践中基于开源项目[Hypertrons](https://www.hypertrons.io/#)所构建的开源翻译组件为TransForChaossApps123。
  该翻译组件的GitHub访问地址为[github.com/apps/transforchaossapps123](https://github.com/apps/transforchaossapps123)。
  
  <b>1、监听issue变化，获取issue信息</b><br/>
  Chaoss官方社区在"Chaoss指标翻译"对应的仓库中提出issue, 其中issue中包含Chaoss提出的相关英文指标，
  此时Github app即transforchaossapps123可以监听到issue的变化，从而获取issue的相关信息，比如issue title、
  issue body等信息，这样我们就拿到了等待翻译的chaoss指标数据。<br/>
  
  <b>2、翻译Chaoss指标信息</b><br/>
  此目标主要是通过Hypertrons的翻译接口所实现的，其中开源项目Hypertrons集成了google翻译接口，可以实现多种
  语言之间的翻译转换，此项目中主要是实现了将英文Chaoss指标翻译成中文的需求。
  其中，关于transforchaossapps123中翻译功能的触发，可以在chaoss指标相关的issues中使用/translate进行
  评论，即可自动调用transforchaossapps123中的翻译组件。<br/>
  
  <b>3、临时保存指标翻译结果，从开发分支向main分支提交PR</b><br/>
  步骤二中已经实现了指标翻译的工作，该步骤可以将翻译后的结果保存在某开发分支B的一个文件中。然后transforchaossapps123
  会从B分支向main分支自动提出PR。<br/>
  
  <b>4、GitHub对接Slack</b><br/>
  通过将Slack的webhookl链接添加到Chaoss指标翻译所对应的GitHub仓库中，即可设置slack channel接受
  GitHub仓库的相关通知，其中可以定制化GitHub仓库的通知内容，可指定GitHub仓库向slack发送指定的Issue、PR
  等信息。
   
- <b>方案进度</b>：
    已经按照原定方案基本实现了时间规划中的内容，基本的监听issue、翻译指标、保存翻译结果、从开发分支向
    main分支提交PR、向slack仓库发送仓库更新信息等。<br/>
    
    目前处于自动化流程的优化阶段，在本次项目结束后，依然有一些部分可以进行优化。比如自动读取issue中所包含的
    链接对应的内容等，目前只能读取issue body中的文本信息。
- <b>遇到的问题及解决方案</b>：

    在基于开源项目[Hypertrons](https://www.hypertrons.io/#)实现自动化翻译插件[transforchaossapps123](https://github.com/apps/transforchaossapps123)
    的过程中，遇到的主要问题就是对于开源项目Hypertrons的使用，其中要深入理解该开源项目的架构设计以及功能、接口的封装，不然
    很难实现自己的翻译插件。<br/>
    
    本地项目中所用到的技术栈基本就是TS + Lua, TS也是在各种开源插件项目中用地比较广泛，但是TS中的Promise对象使用起来具有一定的难度，
    并且要处理好Promise所可能对应的回调函数，不然在调用Hypertrons中各种接口的时候会遇到很多的问题。此外，还要注意Hypertrons中各种
    现成组件的组合使用，以此来简化工作，使用Hypertrons所能提供的原生组件实现相关功能。
- <b>项目完成质量</b>：
    对于此"CHAOSS指标中文自动化翻译"项目，基本已经实现了核心功能，可以实现自动翻译、自动向翻译仓库提交更改、自动通知slack等功能，
    可以说工作量还是比较饱满的。<br/>
    
    但是项目的实施过程中还是存在一定的问题，比如对于issue中可能需要直接包含指标信息，自动翻译插件transforchaossapps123才能执行
    自动翻译等流程，如果issue中只是包含指标相关的一个链接，这个时候就需要手动提个issue包含指标信息。之后，尽量接入读取issue中链接
    对应的内容，以实现更完善的自动化翻译流程。<br/>
    
    此外，项目翻译的准确度有必要进一步提高，需要整理指标体系，并且将指标体系运用到翻译过程中，以实现更加精确的翻译。之后可能会使用
    "分词后进行翻译"的模式，此翻译流程有待实践。
- <b>与导师沟通及反馈情况</b>：
    基本实现了指标翻译自动化，但是还是存在一定的问题，之后有可能的话继续完善。缺少一些非核心功能的实现，如若实现，此翻译插件功能就会非常
    完善了，可以真正实现"指标翻译自动化"。

