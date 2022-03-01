---
title: 数据分析
summary: 三个特别基础的算法
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
