---
title: 人事管理系统
summary: 运用软件工程的方法
tags:
- College Learning
date: "2022-02-25T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Photo by myself
  focal_point: Smart

links:
- icon: twitter
  icon_pack: fab
  name: Follow
  url: https://twitter.com/tunan666
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""


---
主要是关于软件工程方面的；
本人负责需求规约的执笔，以及系统中员工管理和招聘管理模块的用例设计、界面原型设计、流程设计、静态模型、动态行为模型；
在项目开发过程中使用了快速原型设计工具Axure RP以及UML建模工具Enterprise Architect；这一项目让本人熟悉了软件项目设计与开发的实际过程，提升了本人搜集、利用各种技术资源，综合运用各学科的知识解决实际问题的能力。

---
题目

人事管理系统

---
目的

    1）掌握软件工程学的基本概念、原理和方法；
    2）重点掌握使用传统生命周期方法、面向对象方法开发软件的技术（包括
    技术规范、工具与标准、基本过程与模型、测试技术与用例设计等）以及 UML
    设计的工具； 
    3）了解软件工程学前沿领域的相关新方法、新技术，为进一步从事软件开
    发打下一个较全面、扎实的基础；
    4）培养搜集、利用各种技术资源（参考文献）如专著（M）、期刊（J）、网
    络资源，综合运用各学科的知识（如算法理论、数据结构、数据库、网络技术等）
    解决实际问题的能力。

---
我的工作

这个项目一共分为4个模块，8个功能。
    小组规约，需求规约，概要设计，详细设计，4个模块
    负责薪资管理、奖惩管理、登录界面、修改密码界面、招聘管理、员工管理、部门管理、系统管理，8个功能
    
我负责其中的需求规约模块和招聘管理、员工管理这2个功能。

---
其中需求规约如下：

![image](https://user-images.githubusercontent.com/56355246/156125944-615c6a8e-1fb2-4621-b41c-8c0a00c485ea.png)


一、项目简介

1、目的

本文将确定人事管理系统的需求。


2、范围

本文将影响智能客户关系管理项目的功能规划、概要设计、详细设计等活动。


3、参考资料

《计算机科学与技术与数据科学与大数据技术专业综合实训3》


4、概述

该该文档详细描述了产品的软件需求，编写该文档的目的是为整个系统实现的管理工作和技术工作提供指南；同时确定该系统的内容和范围，为评价和测试该系统提供依据。

5、名词解释

人事管理系统是属于ERP的一个部分。它单指汇集成功企业先进的人力资源管理理念、人力资源管理实践、人力资源信息化系统建设的经验，以信息技术实现对企业人力资源信息的高度集成化管理，为中国企业使用的人力资源管理解决方案。核心价值在于将人力资源工作者从繁重的日常琐碎事务中解放出来，将更多的精力用于企业的人力资源职能管理和管理决策，保持企业的持续高效运营。 集中记录、监测和分析所有劳动力的技能和资格，提供决策分析。提高企业整体的科技含量与管理效率，加快企业的信息化建设。


二、需求分析


1、需求概述


该项目是设计出一个对企业人力资源进行管理的系统，用户对象是企业的管理层。

该系统可管理企业的员工信息、部门信息、实现企业招聘管理；该系统还可以对员工薪资、奖惩情况进行管理，也可以对系统用户信息进行管理。

系统优势：办公自动化，提升工作效率，强化核心业务，提升管控能力，强化实时管控，适应变革需要，管控人工成本，创造管理利润。

2、功能需求分析

人事管理系统的主要功能需求包括如图所示：

![image](https://user-images.githubusercontent.com/56355246/156124986-cdd6b740-961b-4d2e-8a4e-160d3f8fc15a.png)

其中用户由三种角色组成：老板、管理员、员工

1、老板：用户中权限最高的，可以查看所有系统中全部信息，并能管理所有系统中的所有用户

2、管理员：每个系统中的管理员，可以查看其系统的所有信息，可以管理自己系统中的员工

3、员工：只能浏览各系统公开的信息，对数据的修改等操作没有权限

![image](https://user-images.githubusercontent.com/56355246/156125093-42498aa4-834d-4d0a-9304-594aa5a3a023.png)



登录和修改密码模块的主要功能需求如下图：

![image](https://user-images.githubusercontent.com/56355246/156125185-2c2c7242-623a-4dfc-8385-d9e6f2d8f4f6.png)

登录和修改密码简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125215-c7488439-22df-49a5-8f90-6199c87bbf00.png)


招聘管理模块的主要功能需求如下图：

![image](https://user-images.githubusercontent.com/56355246/156125260-785830d4-486d-4278-aeb0-9419cfc36ac3.png)


招聘管理简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125284-e79c7b18-d885-44c8-adcf-591f1239e173.png)


员工管理模块的主要功能需求如下图：
![image](https://user-images.githubusercontent.com/56355246/156125311-914064b9-7298-4f11-9d8e-01bbc786640e.png)


员工管理简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125340-f803766a-ba8d-4762-9351-e8003b178e21.png)


奖惩管理模块的主要功能需求如下图：

![image](https://user-images.githubusercontent.com/56355246/156125364-3ae79b92-9a26-4c9b-862a-dbd3b52ec87a.png)


奖惩管理简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125389-40497b4d-350e-4701-918b-51e9fc96739d.png)


薪资管理模块的主要功能需求如下图：

![image](https://user-images.githubusercontent.com/56355246/156125413-9c2bcc5f-ef34-4365-80d3-29b58e5eed46.png)

薪资管理简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125446-b0013c96-01d9-4c9f-be39-80a712d8687d.png)

系统管理模块的主要功能需求如下图：

![image](https://user-images.githubusercontent.com/56355246/156125522-4f790f31-e8a9-445f-bee7-cf33a858bb77.png)


系统管理简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125545-c0f839ae-e751-4693-96ea-ca6b8c7d019d.png)


部门管理模块的主要功能需求如下图：

![image](https://user-images.githubusercontent.com/56355246/156125575-9d7dbcbd-3648-49ce-ac33-249f90e62b50.png)


部门管理简单任务示意图:

![image](https://user-images.githubusercontent.com/56355246/156125617-2d330f84-4868-432c-a152-b3a9f3699557.png)






