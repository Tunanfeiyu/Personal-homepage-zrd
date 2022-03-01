---
title: 数据分析
summary: 两个基础的算法
tags:
- College Learning
date: "2021-11-22T00:00:00Z"

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
写在开头
---
上课随手写的，挺不行的，不过既然写了还是发出来

---
Apriori算法


对Apriori发现频繁项目集算法进行设计实验，给出样本事务数据库，实施Apriori算法。核心思想是通过候选集生成和情节的向下封闭检验检测两个阶段来挖掘频繁项集。

生成1项候选集的算法关键代码

    for(i=1; i<=nn; i++) //交易集
        {
            for(j=1; j<=D[i].item[0]; j++) // 某个交易集中的记录
            {
                temp=1;
                for(k=1; k<=no; k++)   //no：候选集中数据项的个数
                {
                    if(C[1][k].item[1]==D[i].item[j])//一项候选集的第k项的值等于第i条交易中第j项的值
                    {
                        C[1][k].item[0]++; //一项候选集的第k项的支持度加1
                        temp=0;

                    }
                }

                if(temp)//第i条交易中的第j数不在候选集中  添加  生成新的项集
                {

                    C[1][++no].item[1]=D[i].item[j];
                    C[1][no].item[0]=1;
                }

            }
    用频繁集Ln-1为基础，通过连接得到n项候选集Cn的算法关键代码
     for(i = 1; i <= num; i++) //扫描频繁项集
        {

            for(j = i+1; j <= num; j++)
            {

                temp = 1; //测试是否满足连接条件
                if(n > 2)//可能有重复项
                {
                    for(k = 1; k < n-1; k++)
                    {
                        if(L[n-1][i].item[k] != L[n-1][j].item[k])//相同位置有相同的项才连接
                        {
                            temp = 0;
                            break;
                        }
                    }
                }
                if(temp==1)//满足连接条件
                {
                    no++;
                    for(p = 1; p <= n-1; p++)
                        C[n][no].item[p] = L[n-1][i].item[p];   
                    C[n][no].item[p] = L[n-1][j].item[p-1];	                
    C[n][no].item[0] = 0;
                    for(q = 1; q <= nn; q++) // 测试支持度
                    {
                        count = 0;                     
    for(s = 1; C[n][no].item[s] != 0; s++)                     {
                            for(t = 1; t <= D[q].item[0]; t++) //遍历第q条记录
                            {
                                if(C[n][no].item[s] == D[q].item[t])  
    { count=count+ 1;
                                    break; }} }
                        if(count == n) //第n项候选集的第no条记录
                            C[n][no].item[0] += 1;//子集存在,第no项的支持度加1

                          }
     C[n][0].item[0] += 1;}  }   }

 ---
实验结果与分析

1、
样本事务数据库为

![image](https://user-images.githubusercontent.com/56355246/156108769-bdb4beb4-77ba-41f0-a4a9-d2e5c8923a43.png)

代码运行结果如下

![image](https://user-images.githubusercontent.com/56355246/156108834-6b405686-869c-4f33-9c8f-b57592a8a8f7.png)

我在设计该算法时遇到了一些小问题，首先是数据的保存，开始想用指针的方式来做，但是逻辑较为复杂，改用数组后，由于定义多个数组结构很混乱，最后采用结构体数组的方式处理数据，算法参照了教材上的如下图的伪代码，结合自己存储数据的方式写为完整的c代码即可即可。

![image](https://user-images.githubusercontent.com/56355246/156109004-c744e497-720c-40ed-92d8-a361f8eca344.png)

![image](https://user-images.githubusercontent.com/56355246/156109285-9b8493b1-7d14-4587-a921-2534b39d0a2d.png)

![image](https://user-images.githubusercontent.com/56355246/156109292-cbd96dde-5365-48f1-838c-1d9c74626e8f.png)

---

AGNES层次聚类算法
对AGNES层次聚类算法进行设计实验，给出一个样本数据，对它实施AGNES层次聚类算法，该方法是自底向上的方法，初始每个对象看做一个簇，每一步合并最相近的簇，最终形成一个簇。
直接采用链表的思想及结构来实现agnes算法

核心算法如下：
    for(int it_cnt =0;it_cnt<n-k;it_cnt++){
        minDis = pow((head->next->x - head->next->next->x),2)+pow((head->next->y - head->next->next->y),2);//初始最小距离的平方是前两个簇的距离
        p3 = head->next;
        prep4 = p3;//记录p4的前一个节点
        p4 = head->next->next;//初始p3,p4记录最小距离的两个簇的位置
        p1 = head->next;
        while(p1->next!=NULL){
          p2=p1->next;
          struct zu *prep2=p1;//记录p2前面的簇，方便记录prep4
          while(p2!=NULL){
            //计算距离
            double tmpdis = pow((p1->x - p2->x),2)+pow((p1->y - p2->y),2);
            if(tmpdis<minDis){//比最小距离小
              minDis = tmpdis;
              p3=p1;
              p4=p2;
              prep4=prep2;
            }
            prep2=p2;
            p2=p2->next;
          }
          p1=p1->next;
        }

        //一次遍历，获得距离最近的两个簇p3,p4，将p4合并到p3，删除p4.
        //合并
        for(int i=0;i<p4->cnt;i++){
          p3->d[p3->cnt]=p4->d[i];

          p3->cnt++;
        }
        //删除p4
        prep4->next=p4->next;
        free(p4);
        //重新计算p3的中心点
        int tempsumx=0,tempsumy=0;
        for(int i = 0 ;i< p3->cnt;i++){
          tempsumx+=d[p3->d[i]].x;
          tempsumy+=d[p3->d[i]].y;
        }
        p3->x=1.0*tempsumx/p3->cnt;
        p3->y=1.0*tempsumy/p3->cnt;
      }

使用的样本数据库
![image](https://user-images.githubusercontent.com/56355246/156109508-0a36aa67-f2b0-4363-a6df-681823f1e781.png)

理论上的执行过程
![image](https://user-images.githubusercontent.com/56355246/156109655-cc7d9bb5-b9d9-4731-8b07-c9df45ed3e86.png)

结果
![image](https://user-images.githubusercontent.com/56355246/156109677-6d18e492-af68-48bc-8f29-cd1a392bf444.png)

过程中遇到的最大的问题就是，用什么结构来实现，我最开始采用了数组的方式，但是二维数组不能很好的保存簇的序号，我想过设定一个三维数组，但是在学习借鉴了他人的算法思想后，采用了链表的结构解决了这一问题。
