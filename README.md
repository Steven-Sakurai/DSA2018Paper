# Paper.io
Group work

## 如何增强normal wanderer  
- 在领地内wander时，尽量靠边    
- 尽量圈别人地  
- 如果领先很多，贴防

## Crazy Pig      
#### 思路    
- 离敌人远时，往他身上靠    
- 离敌人近时，躲着跑    
- 离敌人绝对距离远时，圈地激进一点（就是改成除4或除3） 
 
#### 代码改动  
- storage['myField'] is a np matrix: {0: nothing, 1: my field, 2: my band, 3: his field, 4: his band}  
- directions相关都改成np.array，转向用矩阵乘法    

#### 调参  
- 主要是118行那个20可以调下  
- 还有202-218  

#### 目前效果
After less than 20 hours, `crazy_pig` is completely outperformed by its children `crazy_pig_v2`

## Crazy Pig v2
Right now `crazy_pig_v2` outperforms all the other bots.   
 
- 加入最简单的杀人、逃跑，搜索`杀人`即可找到相应代码，需改进  
- 加入`summary`函数自动调参，应对不同类型bots，只在knockout中有作用。  
- 最需要调的就是`summary`函数和line 119。line 119是判断何时远离敌人，何时靠近敌人。

#### 目前效果

```bash
Knockout Result: Crazy_Pig_v2 wins.
AI_normal_wanderer 0 : 11 Crazy_Pig_v2
+----+------------------+----------------+-----------+
|  # |  Endgame Winner  | Endgame Reason |    Rmk    |
+----+------------------+----------------+-----------+
|  1 | (B) Crazy_Pig_v2 |  (829, 1411)   | END, 4000 |
|  2 | (A) Crazy_Pig_v2 |  (2019, 886)   | END, 4000 |
|  3 | (B) Crazy_Pig_v2 |  (940, 1847)   | END, 4000 |
|  4 | (A) Crazy_Pig_v2 |       KO       | TAP,  832 |
|  5 | (B) Crazy_Pig_v2 |  (677, 1741)   | END, 4000 |
|  6 | (A) Crazy_Pig_v2 |  (1387, 1039)  | END, 4000 |
|  7 | (B) Crazy_Pig_v2 |  (1000, 1560)  | END, 4000 |
|  8 | (A) Crazy_Pig_v2 |  (1546, 1180)  | END, 4000 |
|  9 | (B) Crazy_Pig_v2 |  (590, 1982)   | END, 4000 |
| 10 | (A) Crazy_Pig_v2 |  (1732, 1125)  | END, 4000 |
| 11 | (B) Crazy_Pig_v2 |  (1069, 1539)  | END, 4000 |
|    |     Knockout     |   Ended Here   |           |
+----+------------------+----------------+-----------+

Knockout Result: Crazy_Pig_v2 wins.
AI_simple_wanderer 0 : 11 Crazy_Pig_v2
+----+------------------+----------------+-----------+
|  # |  Endgame Winner  | Endgame Reason |    Rmk    |
+----+------------------+----------------+-----------+
|  1 | (B) Crazy_Pig_v2 |  (914, 2052)   | END, 4000 |
|  2 | (A) Crazy_Pig_v2 |       KO       | TAP, 1831 |
|  3 | (B) Crazy_Pig_v2 |  (1022, 1466)  | END, 4000 |
|  4 | (A) Crazy_Pig_v2 |  (1673, 850)   | END, 4000 |
|  5 | (B) Crazy_Pig_v2 |       KO       | TAP, 2118 |
|  6 | (A) Crazy_Pig_v2 |       KO       | TAP, 1465 |
|  7 | (B) Crazy_Pig_v2 |  (1062, 2036)  | END, 4000 |
|  8 | (A) Crazy_Pig_v2 |       KO       | TAP, 1769 |
|  9 | (B) Crazy_Pig_v2 |  (1354, 1488)  | END, 4000 |
| 10 | (A) Crazy_Pig_v2 |  (1836, 893)   | END, 4000 |
| 11 | (B) Crazy_Pig_v2 |  (1175, 2330)  | END, 4000 |
|    |     Knockout     |   Ended Here   |           |
+----+------------------+----------------+-----------+

Knockout Result: Crazy_Pig_v2 wins.
Crazy_Pig 2 : 11 Crazy_Pig_v2
+----+------------------+----------------+-----------+
|  # |  Endgame Winner  | Endgame Reason |    Rmk    |
+----+------------------+----------------+-----------+
|  1 | (B) Crazy_Pig_v2 |  (987, 1679)   | END, 4000 |
|  2 | (A) Crazy_Pig_v2 |       KO       | TAP, 3080 |
|  3 | (B) Crazy_Pig_v2 |       KO       | TAP, 2463 |
|  4 |  (B) Crazy_Pig   |       KO       | TAP, 2491 |
|  5 | (B) Crazy_Pig_v2 |  (1091, 1536)  | END, 4000 |
|  6 | (A) Crazy_Pig_v2 |  (1310, 904)   | END, 4000 |
|  7 | (B) Crazy_Pig_v2 |  (883, 1542)   | END, 4000 |
|  8 | (A) Crazy_Pig_v2 |       KO       | TAP, 2074 |
|  9 | (B) Crazy_Pig_v2 |       KO       | TAP, 2717 |
| 10 | (A) Crazy_Pig_v2 |       KO       | TAP, 3160 |
| 11 | (B) Crazy_Pig_v2 |  (839, 1818)   | END, 4000 |
| 12 |  (B) Crazy_Pig   |       KO       | TAP, 3005 |
| 13 | (B) Crazy_Pig_v2 |       KO       | CIT, 2703 |
|    |     Knockout     |   Ended Here   |           |
+----+------------------+----------------+-----------+

Knockout Result: AI_25x25 wins.
AI_25x25 11 : 0 Crazy_Pig_v2
+----+----------------+----------------+-----------+
|  # | Endgame Winner | Endgame Reason |    Rmk    |
+----+----------------+----------------+-----------+
|  1 |  (A) AI_25x25  |       KO       | TAP, 1090 |
|  2 |  (B) AI_25x25  |       KO       | TAP, 1599 |
|  3 |  (A) AI_25x25  |       KO       | TAP, 1394 |
|  4 |  (B) AI_25x25  |       KO       | TAP,  936 |
|  5 |  (A) AI_25x25  |       KO       | TAP, 1294 |
|  6 |  (B) AI_25x25  |       KO       | TAP,  543 |
|  7 |  (A) AI_25x25  |       KO       | TAP,  708 |
|  8 |  (B) AI_25x25  |       KO       | TAP, 1025 |
|  9 |  (A) AI_25x25  |       KO       | TAP,  690 |
| 10 |  (B) AI_25x25  |       KO       | TAP,  709 |
| 11 |  (A) AI_25x25  |       KO       | TAP,  477 |
|    |    Knockout    |   Ended Here   |           |
+----+----------------+----------------+-----------+
```

#### how to fuck 25x25?

## Crazy Pig v3

Created for fucking 25x25, but it cannot beat normal wanderer.

- status: discarded

## Crazy Pig v2.1

- minor bugs fixed
- able to defeat 25x25 and normal wanderer

#### 目前效果

```bash
Knockout Result: Crazy_Pig_v2_1 wins.
AI_25x25 2 : 11 Crazy_Pig_v2_1
+----+--------------------+----------------+-----------+
|  # |   Endgame Winner   | Endgame Reason |    Rmk    |
+----+--------------------+----------------+-----------+
|  1 | (B) Crazy_Pig_v2_1 |  (681, 3691)   | END, 4000 |
|  2 | (A) Crazy_Pig_v2_1 |       KO       | CIT,  514 |
|  3 | (B) Crazy_Pig_v2_1 |       KO       | TAP, 3340 |
|  4 | (A) Crazy_Pig_v2_1 |  (3107, 679)   | END, 4000 |
|  5 | (B) Crazy_Pig_v2_1 |  (679, 4003)   | END, 4000 |
|  6 | (A) Crazy_Pig_v2_1 |       KO       | WAL,   84 |
|  7 | (B) Crazy_Pig_v2_1 |  (676, 3601)   | END, 4000 |
|  8 |    (B) AI_25x25    |       KO       | TAP, 3485 |
|  9 |    (A) AI_25x25    |       KO       | TAP, 3308 |
| 10 | (A) Crazy_Pig_v2_1 |       KO       | TAP, 2769 |
| 11 | (B) Crazy_Pig_v2_1 |  (679, 3841)   | END, 4000 |
| 12 | (A) Crazy_Pig_v2_1 |       KO       | WAL,   98 |
| 13 | (B) Crazy_Pig_v2_1 |  (619, 4444)   | END, 4000 |
|    |      Knockout      |   Ended Here   |           |
+----+--------------------+----------------+-----------+

Knockout Result: Crazy_Pig_v2_1 wins.
AI_normal_wanderer 3 : 11 Crazy_Pig_v2_1
+----+------------------------+----------------+-----------+
|  # |     Endgame Winner     | Endgame Reason |    Rmk    |
+----+------------------------+----------------+-----------+
|  1 |   (B) Crazy_Pig_v2_1   |       KO       | CIT, 2122 |
|  2 |   (A) Crazy_Pig_v2_1   |  (3626, 2875)  | END, 4000 |
|  3 |   (B) Crazy_Pig_v2_1   |  (1820, 3663)  | END, 4000 |
|  4 |   (A) Crazy_Pig_v2_1   |  (3467, 2941)  | END, 4000 |
|  5 | (A) AI_normal_wanderer |  (2465, 2084)  | END, 4000 |
|  6 | (B) AI_normal_wanderer |       KO       | TAP, 3209 |
|  7 |   (B) Crazy_Pig_v2_1   |  (3653, 3829)  | END, 4000 |
|  8 |   (A) Crazy_Pig_v2_1   |  (3853, 2011)  | END, 4000 |
|  9 |   (B) Crazy_Pig_v2_1   |       KO       | TAP, 2720 |
| 10 |   (A) Crazy_Pig_v2_1   |  (3266, 2322)  | END, 4000 |
| 11 | (A) AI_normal_wanderer |  (3821, 3515)  | END, 4000 |
| 12 |   (A) Crazy_Pig_v2_1   |       KO       | TAP, 1518 |
| 13 |   (B) Crazy_Pig_v2_1   |  (3352, 4226)  | END, 4000 |
| 14 |   (A) Crazy_Pig_v2_1   |       KO       | TAP, 3574 |
|    |        Knockout        |   Ended Here   |           |
+----+------------------------+----------------+-----------+
```

## git 使用说明  
先下载git  
设置邮箱：git config --global user.email "xxx@pku.edu.cn"  
然后  
git clone https://github.com/Steven-Sakurai/Paper.io  
cd Paper.io  
git pull origin master  
添加文件  
touch xxx.py  
git add -A  
git commit -m "一些信息"  
git push origin master  
