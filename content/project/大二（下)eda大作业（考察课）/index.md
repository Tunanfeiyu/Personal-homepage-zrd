---
title: EDA
summary:  拔河游戏A
tags:
- College Learning
date: "2021-06-30T00:00:00Z"

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
拔河游戏A设计（EDA）

一、题目功能分析：

1）设计拔河游戏电路，用按键与LED表示输入与输出。 

2）初始时，24个LED中间的两个点亮（引脚编号是100和99），然后游戏双方不停按动按键（K7和K0），点亮的两个LED向按动按键慢的一方移动；

3）每按动一下按键，LED向对方移动一格；

4）只要LED移动到头，游戏结束；

5）游戏结束时让胜利一方的LED灯（K7方：118-110，K0方：86-98）循环点亮。

6）设置复位键，按下复位键游戏重新开始。

7）工作时钟100Hz即可。

---
二、总体模块划分：

1. 设计思路
（1） 24个LED成一排，设置三个按键（复位键K6、游戏键K0、K7），游戏键每按一次就会产生一个有效低电平，哪边按得快灯就向对方按键移动一位；

（2） 无论何时按下复位键，24个LED立即恢复初始状态，即中间两个亮，其他灭；

（3） 当中间两个LED灯移到任一边终端时，两边选手按键均无效，而获胜一方的LED灯将循环点亮，直到按下复位键，开始下一轮游戏；

2. 按键比较与亮点移位
3. 
K0、K7是按键的输入变量，24位led_r是亮点当前位置的状态变量，初值为000000000001100000000000。配合时钟脉冲，并且游戏使能端开启的情况下，当K7先按下时，led_r进行逻辑移位，右移，当K0先按下时，led_r进行逻辑移位，左移。其他情况，led_r保持不变。

3. 游戏锁定
在任意一方将亮点按动到对方那边的终点后，游戏结束，此时按动游戏键无效。亮点到达终点时即led_r中第0、1位为1（右端终点）或者第23、22位为1（左端终点）。故设定一个标志变量x，在x=1时按键有效，每当BUFF变化一次就进行一次判断，当led_r=110000000000000000000000或led_r=000000000000000000000011时x=2，此时按键无效。

4. 获胜庆祝
led_r=110000000000000000000000是K7方获胜，需要循环点亮的12个灯的状态变量，此时x值为3，有初始值“100000000000”，通过led_r(23 downto 13) <= led_r(22 downto 12);对led_r的第23位至第12位进行初始赋值，再通过循环移位，ROR循环右移，实现K7方的12个灯循环点亮，庆祝胜利；同理，12位led_r是K0方获胜，需要循环点亮的12个灯的状态变量，有初始值“000000000001”，通过led_r(10 downto 0) <= led_r(11 downto 1);对led_r的第11位至第0位进行初始赋值，再通过循环移位，ROL循环左移，实现K0方的12个灯循环点亮，庆祝胜利。

5. 游戏复位
x有初始值为0，按键K6按下则赋值为零，此时使对led_r恢复初始值，FLAG恢复初始值，实现游戏复位。

---
三、代码实现：

  library IEEE;

  use IEEE.STD_LOGIC_1164.ALL;

  use IEEE.STD_LOGIC_ARITH.ALL;

  use IEEE.STD_LOGIC_UNSIGNED.ALL;

  ENTITY control IS

	PORT(	 
  
		CLK:		   IN STD_LOGIC;
    
		rst:		   IN STD_LOGIC;
		
    key1:		   IN STD_LOGIC;
		
    key2:		   IN STD_LOGIC;
		
    led:         out std_logic_vector(23 downto 0));

  END control;


  ARCHITECTURE Behavioral OF control IS
	
  signal State      :   std_logic_vector(3 downto 0);
	
  signal key1_r:std_logic;
	
  signal key2_r:std_logic;
	
  signal key1_r1:std_logic;
	
  signal key2_r1:std_logic;
	
  signal bt1:std_logic;
	
  signal bt2:std_logic;
	
  signal led_r:std_logic_vector(23 downto 0);
	
  signal cnt:std_logic_vector(7 downto 0);

  BEGIN
	
  led <= led_r;
	
  PROCESS(clk)BEGIN
		
    IF clk'EVENT AND clk='1' THEN
			
      key1_r <= key1;
			
      key1_r1 <= key1_r;
			
      key2_r <= key2;
			
      key2_r1 <= key2_r;
			
      if(key1_r = '1' and key1_r1 = '0')then
				
        bt1 <= '1';
			
      else
				
        bt1 <= '0';
			
      end if;
			
      if(key2_r = '1' and key2_r1 = '0')then
				
        bt2 <= '1';
			
      else
				
        bt2 <= '0';
			
      end if;
		
    END IF;
	
  END PROCESS;
	
  PROCESS(clk,rst)BEGIN
		
    if(rst = '0')then
			
      led_r <= "000000000001100000000000";
			
      State <= x"0";
			
      cnt <= x"00";
		
    elsIF clk'EVENT AND clk='1' THEN
			
      case State is
	    		
          when x"0" =>
	    			
            if(bt1 = '1' and bt2 = '1')then
	    				
              led_r <= led_r;
	    			
            elsif(bt1 = '1')then
	    				
              led_r(22 downto 0) <= led_r(23 downto 1);
	    				
              led_r(23) <= '0';
	    			
            elsif(bt2 = '1')then
	    				
              led_r(23 downto 1) <= led_r(22 downto 0);
	    				
              led_r(0) <= '0';
	    			
            else
	    				
              led_r <= "000000000001100000000000";
	    			
            end if;
	    			
            if(bt1 = '1' or bt2 = '1')then
	    				
              State <= State +  '1';
	    			
            else
	    				
              State <= State;
	    			
            end if;
	    			
            cnt <= x"00";
	    		
          when x"1" =>
	    			
            if(bt1 = '1' and bt2 = '1')then
	    				
              led_r <= led_r;
	    			
            elsif(bt1 = '1')then
	    				
              led_r(22 downto 0) <= led_r(23 downto 1);
	    				
              led_r(23) <= '0';
	    			
            elsif(bt2 = '1')then
	    				
              led_r(23 downto 1) <= led_r(22 downto 0);
	    				
              led_r(0) <= '0';
	    			
            else
	    				
              led_r <= led_r;
	    			
            end if;
	    			
            if(led_r = "110000000000000000000000" or led_r = "000000000000000000000011")then
	    				
              State <= State +  '1';
	    			
            else
	    				
              State <= State;
	    			
            end if;
	    			
            cnt <= x"00";
	    		
          when x"2" =>
	    			
            if(led_r = "110000000000000000000000")then
	    				
              led_r <= "000000000000000000000001";
	    			
            elsif(led_r = "000000000000000000000011")then
	    				
              led_r <= "100000000000000000000000";
	    			
            else
	    				
              led_r <= led_r;
	    			
            end if;
	    			
            State <= State +  '1';
	    			
            cnt <= x"00";
	    		
          when x"3" =>
	    			
            if(cnt >= x"19")then
						
            cnt <= x"00";
						
            led_r(23 downto 13) <= led_r(22 downto 12);
						
            led_r(12) <= led_r(23);
						
            led_r(10 downto 0) <= led_r(11 downto 1);
						
            led_r(11) <= led_r(0);
					
          else 
						
            cnt <= cnt + '1';
					
          end if;
	    		
          when others =>
	    			
            State <= x"0";
	    			
            led_r <= "000000000001100000000000";
	    	
        end case;
		
    END IF;
	
   END PROCESS;

  END Behavioral;

---
四、设计心得、体会：

这个大作业布置的很早但是正式开始做的很晚，刚开始的准备工作开始就遭遇了各种麻烦，群里的quartusⅡ下载过后用不了，baidu上面只有最新版本的，最后在csdn上找到了8.0的https://blog.csdn.net/moxiangfeng/article/details/80260059
但是在测试电路板能否连接到电脑的时候发现我们领到的数据线是错的，班上领了一根电线过来，快4月底初才领到好的数据线，5月初才分好题目，五月中旬就要期中考试了，然后组长电脑用不了8.0的版本，也不知道为什么，我就用的8，我队友用的13的版本，然后准备工作做完了，就开始做了，VHDL语言大体还好，细节有些地方总是出错，加上我和我队友用的版本不一样，工程文件有些时候莫名其妙还不能用，代码写完了过后，波形测试也从头开始在网上找方法，频率的设定就弄了好久，总时间不够，频率过快等层出不穷，我们就选择了先下到电路板上试试，然后驱动安装失败，“第三方 INF不包含数字签名信息”的，我试了试禁用驱动强制签名，也不行，最后找了一个装成功了的驱动装好了，好在下到电路板上之后大都正常，在网上摸索好一阵，波形测试最后也做好了，学到了很多吧，不仅仅是eda这门技术和vhhdl语言，团队合作的重要性，还要克服自己的惰性，这次eda的大作业收益颇丰。
