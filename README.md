# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the required library and read the dataframe.
2. Write a function computeCost to generate the cost function.
3. Perform iterations og gradient steps with learning rate.
4. Plot the Cost function using Gradient Descent and generate the required graph.
 

## Program:
```
/*
Program to implement the linear regression using gradient descent. 
Developed by: Sangavi Suresh
RegisterNumber:  212222230130
*/
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

data=pd.read_csv("ex1.txt",header =None)

plt.scatter(data[0],data[1])
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City (10,000s)")
plt.ylabel("Profit ($10,000")
plt.title("Profit Prediction")

def computeCost(X,y,theta):

  m=len(y)
  h=X.dot(theta)
  square_err=(h-y)**2
  j=1/(2*m)* np.sum(square_err)
  return j

data_n=data.values
m=data_n[:,0].size
X=np.append(np.ones((m,1)),data_n[:,0].reshape(m,1),axis=1)
y=data_n[:,1].reshape(m,1)
theta=np.zeros((2,1))

computeCost(X,y,theta)

def gradientDescent(X,y,theta,alpha,num_iters):
  m=len(y)
  J_history=[]

  for i in range (num_iters):
    predictions=X.dot(theta)
    error = np.dot(X.transpose(),(predictions-y))
    descent=alpha*1/m * error
    theta-=descent
    J_history.append(computeCost(X,y,theta))

  return theta,J_history  

theta,J_history = gradientDescent(X,y,theta,0.01,1500)
print("h(x) ="+str(round(theta[0,0],2))+" + "+str(round(theta[1,0],2))+"x1" )

plt.plot(J_history)
plt.xlabel("Iteration")
plt.ylabel("$J(\Theta)$")
plt.title("Cost function using Grading Descent")

plt.scatter(data[0],data[1])
x_value=[x for x in range(25)]
y_value=[y*theta[1]+theta[0] for y in x_value]
plt.plot(x_value,y_value,color="r")
plt.xticks(np.arange(5,30,step=5))
plt.yticks(np.arange(-5,30,step=5))
plt.xlabel("Population of City(10,000s)")
plt.ylabel("Profit ($10,000")
plt.title("Profit Prediction")

def predict (x,theta):
  predictions=np.dot(theta.transpose(),x)
  return predictions[0]

predict1=predict(np.array([1,3.5]),theta)*10000
print("For population = 35,000,we predict a profit a profit of $"+str(round(predict1,0)))

predict2=predict(np.array([1,7]),theta)*10000
print("For population =70,000,we predict a profit a profit of $"+str(round(predict2,0)))

```

## Output:

**PROFIT PREDICTION**:

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/689fb3a8-fa17-45dc-b414-0681cab77c18)


**COST FUNCTION**:

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/f38024d8-4bd8-427d-b586-926dfc995dbb)

**GRADIENT DESCENT**:

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/e3c8135e-2af4-485b-bcd4-211829a1ce90)

**COST FUNCTION USING GRADIENT DESCENT**:

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/2f8fe145-230f-4fa9-8289-9db52ad06a05)

**GRAPH WITH BEST FIT LINE (PROFIT PREDICTION)**:

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/2e0a4ec9-7671-4366-ac5f-9f034ae748d7)

**PROFIT PREDICTION FOR A POPULATION OF 35,000**:

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/1d60c9c5-2666-4142-b851-7f015dfdb010)


**PROFIT PREDICTION FOR A POPULATION OF 70,000**

![image](https://github.com/Sangavi-suresh/Implementation-of-Linear-Regression-Using-Gradient-Descent/assets/118541861/533e1e75-ce99-4815-821c-f315a1374b97)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
