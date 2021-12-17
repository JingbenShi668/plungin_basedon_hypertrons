本次Chaoss指标自动化翻译的工作，主要是及时捕捉Chaoss英文指标库的指标变化，然后使用GitHub app获取变化的文本并对其进行翻译。

本次自动化的指标翻译工作主要是使用到了hypertrons，一个优秀的开源协作机器人。🎉🎉🎉

项目运行流程如下(首先需要将该项目克隆在自己的本地): 

1、安装GitHub app - Menbotics，然后对Menbotics进行配置，允许其访问翻译工作所用到的仓库

<img src="https://git-course.oss-cn-shanghai.aliyuncs.com/Chaoss/ImagesForReadme/Menbotics.png" width = "1000" align=center />

2、对Hypertrons的四个核心配置文件进行配置，其中index.lua文件定义了具体的翻译逻辑，

<img src="https://git-course.oss-cn-shanghai.aliyuncs.com/Chaoss/ImagesForReadme/HypertronsArchitecture.png" height = "100" align=center />

3、未完待续~
