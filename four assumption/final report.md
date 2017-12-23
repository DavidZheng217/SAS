[TOC]

#CAN THE SALARY OF NAB PLAYERS BE PREDICTED?

Team Number:  Jenny Viola Alice Dean David 

##INTRODUCTION

As the topest basketball association in the world, revenue of NBA players are very high, for example Stephen Curry whose annual salary is 34.68 million. However we are doubt that if some players are overvalued or undervalued. So we decided use multilinear regression to preduct the revenue of the NBA players.

###DATA RESOURCE

The data set we collected is from [Kaggle](https://www.kaggle.com/noahgift/social-power-nba/data) which contains one respones variable which is salary and 52 explaintory variables. Moreover the data is for the 2016 - 2017 season, the newest one.

URL: https://www.kaggle.com/noahgift/social-power-nba/data

##DATA ANLYSIS

We will do basic statistics, introduce variables and choose variables in this step. First, in the residual plot, someone have significant pattern. So we adjusted these variables by taking square, log10, etc.

| VARIABLE | WAY OF PROCESS |
| -------- | -------------- |
| $TWI$    | $log_{10}TWI$  |
| $GP$     | $GP^2$         |

###SCATTER PLOT 

In the appendix, most variables do not any relationship to the salary. However, the trend between rankings and salary is usually more significant, usually is the nagetive one. It is quite resonable, smaller ranking number usually means players are more capable. Besides, the positive relationship between PTS and SAL can be seen from the scatter plot.

Besides, in the scatter plot between PG_PCT and SAL, it is strange to someone's PG_PCT is 1 which means every time this man shoot the ball, it will goal. After doing further research, we found this player's field goal attempt is 1. So we delete this data.

### CORRELATION MATRIX

As for correlation matrix, many variabels have the high linear relationship between each other. For example, SAL and FGM_PG whose $r$ is 0.63583. 

###VARIABLE EXPLAINATION

In the dataset, some variables are assigned the rankings, we add the sign *(RANK)* after the 

| VARIABLE          | EXPLANATION                              |
| ----------------- | ---------------------------------------- |
| AGE               | age of the player                        |
| TWI               | number of followers in Twitter           |
| W                 | number of games team wins                |
| W_RANK            | ranking of the variable **W**            |
| L                 | number of games that team lose           |
| L_RANK            | ranking of the variable **L**            |
| GP                | number of games player played            |
| GP_RANK           | ranking of the variable **GP**           |
| MIN               | minutes of player on the floor           |
| MIN_RANK          | ranking of the variable **MIN**          |
| W_PCT             | precentage of winning the game           |
| W_PCT_RANK        | ranking of the variable **W_PCT**        |
| OFF_RATING (进攻效率) | offense rating: A statistic used in basketball to measure an individual player's efficiency at producing points for the offense |
| OFF_RATING_RANK   | ranking of the variable **OFF_RATING**   |
| DEF_RATING (防守效率) | defense rating: A statistic used in basketball to measure an individual player's efficiency at producing points for the defense |
| DEF_RATING_RANK   | ranking of the variable **DEF_RATING**   |
| NET_RATING        | offense rating minus defense rating      |
| NET_RATING_RANK   | ranking of the variable **NET_RATING**   |
| AST_PCT (助攻率)     | assist percentage:  A statistics that estimates the percentage of field goals made by a team that a particular player assisted on while he was in the game |
| AST_PCT_RANK      | ranking of the variable **AST_PCT**      |
| AST_TO (助攻失误比)    | assist to overturn:  A statistics used to evaluate the ball control and ball handling skills of a player |
| AST_TO_RANK       | ranking of the variable **AST_TO**       |
| AST_RATIO (助攻比率)  | assist ratio:  A statistics that estimates the percentage of a team’s possessions that ends in an assist |
| AST_RATIO_RANK    | ranking of the variable **AST_RATIO**    |
| OREB_PCT (进攻篮板率)  | offensive rebound percentage:  A statistic that puts a player’s number of offensive rebounds in proportion to the total number of offensive rebounds available while they were in active play |
| OREB_PCT_RANK     | ranking of the variable **OREB_PCT**     |
| DREB_PCT (防守篮板率)  | defensive rebound percentage:  A statistic that puts a player’s number of defensive rebounds in proportion to the total number of defensive rebounds available while they were in active play |
| DREB_PCT_RANK     | ranking of the variable **DREB_PCT**     |
| REB_PCT (篮板率)     | rebound percentage: A statistic that puts a player’s number of rebounds of rebounds in proportion to the total number of rebounds available while they were in active play |
| REB_PCT_RANK      | ranking of the variable **REB_PCT**      |
| TS_PCT (真实命中率)    | true shooting percentage: A statistic that measures a player's efficiency at shooting the ball |
| TS_PCT_RANK       | ranking of the variable **TS_PCT**       |
| USG_PCT ( 回合占有率)  | usage percentage: A statistic that estimate of the percentage of team plays used by a player while he was on the floor |
| USG_PCT_RANK      | ranking of the variable **USG_PCT**      |
| PACE (回合数)        | pace factor:  A statistic that estimate of the number of possessions per 48 minutes by a team |
| PACE_RANK         | ranking of the variable **PACE**         |
| PIE               | player impact estimate:  A statistic that shows what % of game events did that player or team achieve |
| PIE_RANK          | ranking of the variable **PIE**          |
| FGM               | field goals made                         |
| FGM_RANK          | ranking of the variable **FGM**          |
| FGA               | field goals attempted                    |
| FGA_RANK          | ranking of the variable **FGA**          |
| FGM_PG            | field goals made per game                |
| FGM_PG_RANK       | ranking of the variable **FGM_PG**       |
| FGA_PG            | field goals attempted per game           |
| FGA_PG_RANK       | ranking of the variable **FGA_PG**       |
| FG_PCT            | field goals percentage                   |
| FG_PCT_RANK       | ranking of the variable **PG_PCT**       |
| EFG_PCT           | effective field goal percentage:  A statistic used in NBA basketball that is similar to Field Goal Percentage, but adds an additional parameter. This parameter adjusts for the fact that 3-point field goals are worth 50 percent more than 2-point field goals. |
| EFG_PCT_RANK      | ranking of the variable **EFG_PCT**      |
| PTS               | points per game                          |
| SAL               | salary of the player in million          |

### CHOOSING IMPORTANT VARIABLES

| METHOD                             | VARIABLES CHOSED                         |
| ---------------------------------- | ---------------------------------------- |
| Stepwise Selection                 | AGE, PIE, MIN_RANK, AST_PCT_RANK, TS_PCT_RANK, TWI |
| Forward Selection                  | AGE, PIE, MIN_RANK, AST_PCT_RANK, TS_PCT_RANK, TWI |
| Backward Elimination               | GP, OFF_RATING, NET_RATING, AST_PCT, DREB_PCT, EFG_PCT, TS_PCT, PACE, PIE, FGM_PG, W_RANK, MIN_RANK, NET_RATING_RANK, OREB_PCT_RANK, REB_PCT_RANK, FGM_RANK, FGA_RANK, FGM_PG_RANK, FGA_PG_RANK, TWI |
| C(p) Selection Method              | AGE, PIE, GP_RANK, AST_PCT_RANK, AST_RATIO_RANK, FGM_RANK, FGA_RANK, TWI |
| Adjusted R-Square Selection Method | AGE, MIN, OFF_RATING, NET_RATING, AST_TO, AST_RATIO, DREB_PCT, EFG_PCT, TS_PCT, PACE, PIE, FGA, W_PCT_RANK, MIN_RANK, OFF_RATING_RANK, NET_RATING_RANK, AST_TO_RANK, OREB_PCT_RANK, REB_PCT_RANK, FGM_RANK, FGA_RANK, FGM_PG_RANK, FGA_PG_RANK, TWI |

Finally, we decided to use the variables chosed by the stepwise selection.

### BUILD THE MODEL

final model: SAL = -11.297 + 0.4439 AGE + 94.168 PIE - 0.0304 MIN_RANK + 3.114 TWI + 0.0149 TS_PCT_RANK + 0.0082 AST_PCT_RANK

In the final model, the variables AGE, PIE, TS_PCT_RANK and AST_PCT_RANK have the positive influence to the salary, while the MIN_RANK has the negative influence to the salary.

- VIF (variance inflation faction)

Before we did the variable selection, the VIF is very high which means there is serious multicollinearity. However, after doing the selection, as the diagram showed the below, all the VIF is less than 10. So we can conclude there is no multicollinearity.

![image](https://github.com/DavidZing/SAS/blob/master/VIF/屏幕快照%202017-12-23%20下午12.44.47.png?raw=true)

- Adjusted R-square

Compared to R square, adjusted R-square can give a more accuracy judgement to model. As the adjusted R-square fro the model is 0.6338. It represents that 63.88% of the data can be explained by the regression model.

## FURTHER ANALYSIS

 

### RESIDUAL ANALYSIS

We will use student residual to judge whether there are outliers in the dataset. All the student residual is less than three which means there is no outlier in the dataset.

### INFLUENTIAL POINT ANALYSIS

In order to judge influential point, we have totaly five ways

- Cook's Distance

### FOUR ASSUMPTION

- $E(\varepsilon_i) = 0$





##APPENDIX



###SCATTER PLOT

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/1.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/2.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/3.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/4.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/5.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/6.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/7.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/8.jpg?raw=true)

![image](https://github.com/DavidZing/SAS/blob/master/SCATTER%20PLOT/9.jpg?raw=true)









