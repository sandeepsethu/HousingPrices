# HousingPrices

In this EDA is conducted on a manually put together dataset of economic and demographic factors to understand its effects on House Price Index.

Correlation between the variables were calculated and we obtained this 

![image](https://user-images.githubusercontent.com/29595951/177474536-7a99bef2-6a3e-4001-93c9-1a4caa84279d.png)

Here we can see how the different variables are correlated to each other.

More specifically, the correlation between price and the different variables are as follows:


price           1.000000
expenses        0.864376
income          0.861527
rent            0.827607
tax             0.810845
insurance       0.808030
popln           0.776034
sav_rate        0.392359
for_sale        0.231722
mortage         0.223710
house_supply    0.174870
month_cosin     0.015736
houses_Sold    -0.040696
month_sin      -0.044992
emp_rate       -0.070566
gdp            -0.071009
own_rate       -0.384955
Name: price, dtype: float64


However, this causation doesnt imply correlation.


After XGBoost modelling, the important features were identified as follows:


![image](https://user-images.githubusercontent.com/29595951/177474754-1082f945-2ae7-427d-aa92-cba1e83ee317.png)

Income and insurance which ranked high in terms of correlation, also found its way into the feature importance list. This signifies that income and insurance are key factors which affect the house price index. 

To further understand its effects, Linear regression as well as Ridge and Lasso regularizations were applied.


Ridge regression scores best in terms of prediction, however,Linear Regression isnt too far behind. 


Following Lasso Regression, the following variables were deemed of no importance:


'sav_rate', 'houses_Sold', 'house_supply', 'mortage', 'tax',
       'emp_rate', 'popln', 'gdp', 'own_rate', 'rent', 'month_sin',
       'month_cosin'
       

Lasso meanwhile scores the worst which might explain that removing features makes the model perform much worse. This could mean that the variables are necessary for explaining the model.


According to OLS, the effects of the different dependent variables can be identified from the table below:


variables	coef
income	-0.2885
insurance	0.2702
sav_rate	0.0471
houses_Sold	0.1897
for_sale	0.5381
house_supply	-0.0286
expenses	0.1472
mortage	0.0097
tax	0.2649
emp_rate	-0.1091
popln	0.1729
gdp	0.0495
own_rate	0.0094
rent	0.4782
month_sin	-0.0172
month_cosin	0.0085


According to Ridge:

variables	coef
const	0.0029
income	-0.2861
insurance	0.2737
sav_rate	0.0462
houses_Sold	0.189
for_sale	0.5378
house_supply	-0.0285
expenses	0.1493
mortage	0.0097
tax	0.2643
emp_rate	-0.1097
popln	0.1667
gdp	0.0494
own_rate	0.0087
rent	0.4767
month_sin	-0.0172
month_cosin	0.0085


According to Lasso:

variables	coef
const	0.0071
income	0.0793
insurance	0.4608
sav_rate	0
houses_Sold	0
for_sale	0.3675
house_supply	0
expenses	0.3372
mortage	0
tax	0
emp_rate	0
popln	0
gdp	0
own_rate	0
rent	0
month_sin	0
month_cosin	0


The coefficient tells you how much the dependent variable is expected to increase when that independent variable increases by one, holding all the other independent variables constant.
