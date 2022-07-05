---
title: 软件测试技术
summary: 单元测试，黑盒测试，白盒测试，性能与自动化测试
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
Junit单元测试（1）固定片断方法（Fixture）（2）异常处理（3）条件测试（4）参数注入方法

利用我的直接以及经验结合了错误推断法得到了以下7个测试用例：

1.体重和身高为偏瘦状态，例如：weight=30kg，height=1.5m

2.体重和身高为正常状态，例如：weight=50kg，height=1.5m

3.体重和身高为偏胖状态，例如：weight=60kg，height=1.5m

4.体重和身高为肥胖状态，例如：weight=80kg，height=1.5m

5.体重为负数，身高正常，例如：weight= -10kg,height=1.5m

6.体重正常，身高为负，例如：weight=50kg,height=-1.2m

7.体重和身高都为负，例如：weight=-10kg,height=-1.2m


1.固定片段方法：

代码：
![image](https://user-images.githubusercontent.com/56355246/177249308-937258a3-5a6b-4a7e-9ace-9f59fc2f8df1.png)

![image](https://user-images.githubusercontent.com/56355246/177249425-d0536bf6-21e4-4dc5-8db2-dd916d3161ec.png)
使用固定片段的方法，测试了（1）中测试用例的的前4个

