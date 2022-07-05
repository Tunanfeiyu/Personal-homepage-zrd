---
title: 软件测试技术
summary: 黑盒测试
tags:
- College Learning
date: "2022-05-09T00:00:00Z"

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
2.黑盒测试

2.1BMI计算问题

![image](https://user-images.githubusercontent.com/56355246/177251008-60a1833e-f8df-4002-b118-967f3e5335a3.png)


结果：

![image](https://user-images.githubusercontent.com/56355246/177251727-62d9752d-0f2f-4537-88fe-484f6b08a987.png)

一共设置4组测试用例，划分等价类2个测试用例，边界值法2个测试用例，在划分等价类中的字符a,a程序不允许输入，设置测试用例没有意义

测试代码如下：

![image](https://user-images.githubusercontent.com/56355246/177251765-89b86eb5-28a8-4543-98ba-7a396be522d6.png)

测试组1是1.5，50没有抛出异常，测试组2是-1，-1抛出了异常，测试组3是0，0抛出了异常，测试组4是0.01，0.01没有抛出异常.

测试的结果如下：

![image](https://user-images.githubusercontent.com/56355246/177251834-bcf7c119-8d79-481a-b056-c7ff037d6677.png)


2.2三角形问题
 
 三角形问题接收三个整数a，b，c 作为输入，代表三角形的三条边。a，b，c 必须满足以下条件： 

C1: a<b+c?     C2: b<a+c?     C3: c<a+b?    C4: a=b?   C5: a=c?    C6: b=c? 

程序的输出是由这三条边确定的三角形类型： 

等边三角形 

等腰三角形 

不等边三角形 

非三角形 

•注：为便于统一，我们约定在“三角形判断”程序中有三个整数型变量a、b、c，分别表示三条边，并假设已经限定输入数据均为整数.

![image](https://user-images.githubusercontent.com/56355246/177251859-f3b05b4d-02d0-4f6d-b931-67c45eea00bb.png)

![image](https://user-images.githubusercontent.com/56355246/177251874-8d441ceb-46d7-409d-adff-adb06d1d677d.png)

代码为：

![image](https://user-images.githubusercontent.com/56355246/177251864-fe4da26a-bb36-4fc8-8155-4510980d9086.png)
![image](https://user-images.githubusercontent.com/56355246/177251885-fa9c66f0-81f1-485d-8fdf-8c0eb06dd081.png)

测试结果如下：

所得到的结果都符合预期

![image](https://user-images.githubusercontent.com/56355246/177251912-c798d8d9-6206-4419-8c2c-713d87dfb68f.png)

即具体为：

![image](https://user-images.githubusercontent.com/56355246/177251928-c3504a3b-c6d9-4074-8e32-935019b7cb1f.png)




