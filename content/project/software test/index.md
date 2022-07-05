---
title: 软件测试技术
summary: 单元测试
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
1.Junit单元测试（1）固定片断方法（Fixture）（2）异常处理（3）条件测试（4）参数注入方法

利用我的直接以及经验结合了错误推断法得到了以下7个测试用例：

体重和身高为偏瘦状态，例如：weight=30kg，height=1.5m

体重和身高为正常状态，例如：weight=50kg，height=1.5m

体重和身高为偏胖状态，例如：weight=60kg，height=1.5m

体重和身高为肥胖状态，例如：weight=80kg，height=1.5m

体重为负数，身高正常，例如：weight= -10kg,height=1.5m

体重正常，身高为负，例如：weight=50kg,height=-1.2m

体重和身高都为负，例如：weight=-10kg,height=-1.2m


1.1固定片段方法：

代码：

![image](https://user-images.githubusercontent.com/56355246/177249308-937258a3-5a6b-4a7e-9ace-9f59fc2f8df1.png)

![image](https://user-images.githubusercontent.com/56355246/177249425-d0536bf6-21e4-4dc5-8db2-dd916d3161ec.png)

使用固定片段的方法，测试了（1）中测试用例的的前4个

---
1.2异常处理

在被测程序中，如果不符合weight>0且height>0则抛出异常

![image](https://user-images.githubusercontent.com/56355246/177249940-91d54327-69dc-4991-9b95-c2b0245652dc.png)

![image](https://user-images.githubusercontent.com/56355246/177249955-735e1242-85e7-4de1-8d3d-a4f3a22ef02e.png)

![image](https://user-images.githubusercontent.com/56355246/177249967-96d0fe7c-14dc-4678-9afe-7ae0fc148b6c.png)

使用异常处理测试了（1）中测试用例的后3个

---
1.3条件测试
我现在只希望测试（1）中的第1个和第6个，即使用条件测试的方法标记一个@Disable即可

![image](https://user-images.githubusercontent.com/56355246/177250012-8628f58b-a21c-4065-91f7-0c2f3c84e594.png)

![image](https://user-images.githubusercontent.com/56355246/177250024-08bcd274-0afe-474f-9034-6dbee88a808d.png)

---
1.4参数注入方法

测试了（1）测试用例中的前4个

![image](https://user-images.githubusercontent.com/56355246/177250073-0732b411-7501-475c-b30d-734ed0c862dd.png)

![image](https://user-images.githubusercontent.com/56355246/177250086-06e53189-b764-4d08-8a17-cfc0c9651098.png)

---
