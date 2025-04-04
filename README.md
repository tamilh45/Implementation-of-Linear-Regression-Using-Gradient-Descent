# Implementation-of-Linear-Regression-Using-Gradient-Descent

## AIM:
To write a program to predict the profit of a city using the linear regression model with gradient descent.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start
2. Import numpy as np
3. Plot the points
4. IntiLiaze thhe program

## Program:
```
/*
Program to implement the linear regression using gradient descent.
Developed by: Tamil Pavalan M
RegisterNumber:  212223110058
*/
```
```
import numpy as np
import pandas as pd
from sklearn.preprocessing import StandardScaler

def linear_regression(X1,y,learning_rate = 0.1, num_iters = 1000):
    X = np.c_[np.ones(len(X1)),X1]
    
    theta = np.zeros(X.shape[1]).reshape(-1,1)
    
    for _ in range(num_iters):
        
        #calculate predictions
        predictions = (X).dot(theta).reshape(-1,1)
        
        #calculate errors
        errors=(predictions - y ).reshape(-1,1)
        
        #update theta using gradiant descent
        theta -= learning_rate*(1/len(X1))*X.T.dot(errors)
    return theta
                                        
data=pd.read_csv("C:/classes/ML/50_Startups.csv")
data.head()

#assuming the lost column is your target variable 'y' 

X = (data.iloc[1:,:-2].values)
X1=X.astype(float)

scaler = StandardScaler()
y=(data.iloc[1:,-1].values).reshape(-1,1)
X1_Scaled = scaler.fit_transform(X1)
Y1_Scaled = scaler.fit_transform(y)
print(X)
print(X1_Scaled)

#learn modwl paramerers

theta=linear_regression(X1_Scaled,Y1_Scaled)

#predict target value for a new data
new_data=np.array([165349.2,136897.8,471784.1]).reshape(-1,1)
new_Scaled=scaler.fit_transform(new_data)
prediction=np.dot(np.append(1,new_Scaled),theta)
prediction=prediction.reshape(-1,1)
pre=scaler.inverse_transform(prediction)
print(prediction)
print(f"Predicted value: {pre}")
```

## Output:

DATA.HEAD()

![362697035-763022ca-616b-4141-942a-109ee33e04461](https://github.com/user-attachments/assets/574a5186-7491-4ba2-b19f-124cf3995c28)

X VALUE

![362702072-83d89cce-8fa6-491b-9c3f-6c18f2c63c3c2](https://github.com/user-attachments/assets/7909075d-474a-4598-ad46-92cc968f45b2)

X1_SCALED VALUE

![362702263-0920d359-e997-46a2-844c-740ef89f149a3](https://github.com/user-attachments/assets/399a9cb7-70c8-4b78-a80a-ba2c7838de64)

PREDICTED VALUES:

![362703268-eb585b7f-3b99-40c0-ab3a-9c6072a7ed394](https://github.com/user-attachments/assets/03d50b3b-98e2-4834-8dd0-07efd16f4943)

## Result:
Thus the program to implement the linear regression using gradient descent is written and verified using python programming.
