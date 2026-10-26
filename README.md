# Implementation-of-Simple-Linear-Regression-Model-for-Predicting-the-Marks-Scored

## AIM:
To write a program to predict the marks scored by a student using the simple linear regression model.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the standard Libraries.
2. Set variables for assigning dataset values.
3. Import linear regression from sklearn.
4. Assign the points for representing in the graph
5. Predict the regression for marks by using the representation of the graph.
6. Compare the graphs and hence we obtained the linear regression for the given datas.

## Program:
```
/*
Program to implement the simple linear regression model for predicting the marks scored.
Developed by: PRASANNA I
RegisterNumber: 212223220079
*/
```


```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from sklearn.metrics import mean_absolute_error, mean_squared_error
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression

import pandas as pd

df = pd.read_csv("exp_2_dataset_student_scores.csv")

print("First 5 rows:\n", df.head())
print("Last 5 rows:\n", df.tail())
# 2) Prepare input (X) and output (Y)
# Assume CSV columns: Hours (feature) and Scores (target)
X = df.iloc[:, :-1].values   # all rows, all columns except last -> shape (n_samples, 1)
Y = df.iloc[:, -1].values    # all rows, last column -> shape (n_samples,)
print("X (features):", X.flatten())
print("Y (targets):", Y)
# 3) Split data into training and testing sets
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=1/3, random_state=0)
print("\nTraining samples:", len(X_train), " Testing samples:", len(X_test))
# 4) Create and train the model
regressor = LinearRegression()
regressor.fit(X_train, Y_train)   # fit on training data
# 5) Predict on the test set
Y_pred = regressor.predict(X_test)
print("\nPredicted values:", np.round(Y_pred, 2))
print("Actual values   :", Y_tes
# 6) Plot training results
plt.figure(figsize=(6,4))
plt.scatter(X_train, Y_train, color="orange", label="Training data")
plt.plot(X_train, regressor.predict(X_train), color="red", label="Fitted line")
plt.title("Hours vs Scores (Training set)")
plt.xlabel("Hours")
plt.ylabel("Scores")
plt.legend()
plt.grid(True)
plt.show()
# 7) Plot testing results (use X_test sorted for a nicer line)
order = np.argsort(X_test.flatten())
X_test_sorted = X_test.flatten()[order]
Y_test_sorted = Y_test[order]
Y_pred_sorted = Y_pred[order]
plt.figure(figsize=(6,4))
plt.scatter(X_test, Y_test, color="blue", label="Test data")
plt.plot(X_test_sorted, Y_pred_sorted, color="green", label="Predictions")
plt.title("Hours vs Scores (Testing set)")
plt.xlabel("Hours")
plt.ylabel("Scores")
plt.legend()
plt.grid(True)
plt.show()
# 8) Evaluation metrics
mae = mean_absolute_error(Y_test, Y_pred)
mse = mean_squared_error(Y_test, Y_pred)
rmse = np.sqrt(mse)
print("\nMean Absolute Error (MAE):", mae)
print("Mean Squared Error (MSE):", mse)
print("Root Mean Squared Error (RMSE):", rmse)
# 9) Example: predict for new students
new_hours = np.array([[2.5], [8.0]])   # shape must be (n_samples, 1)
pred_new = regressor.predict(new_hours)
print("\nPredictions for new hours", new_hours.flatten(), "=>", np.round(pred_new,2))


```
## Output:

<img width="230" height="262" alt="image" src="https://github.com/user-attachments/assets/50c1b9df-f815-43b8-bbc9-7dd277b1253c" />

<img width="571" height="90" alt="image" src="https://github.com/user-attachments/assets/ff96393b-be3a-4d80-8adc-5e0a8fa0c465" />

<img width="308" height="43" alt="image" src="https://github.com/user-attachments/assets/a97b8109-7d79-4549-b37c-d06cf49cc52b" />

<img width="326" height="74" alt="image" src="https://github.com/user-attachments/assets/46ff3cb9-1113-4cc0-a859-0d397eb33ca6" />

<img width="500" height="54" alt="image" src="https://github.com/user-attachments/assets/e131b22f-b804-4594-89b3-8a1c527d3508" />

<img width="542" height="398" alt="image" src="https://github.com/user-attachments/assets/e2064e43-9fc2-4e76-aca9-28619d35a541" />

<img width="530" height="392" alt="image" src="https://github.com/user-attachments/assets/2e3aa875-b138-4656-9dc9-b2c81dc2e447" />

<img width="383" height="80" alt="image" src="https://github.com/user-attachments/assets/ca0d1f7a-597c-49a5-ab18-a74061e99eec" />

<img width="361" height="41" alt="image" src="https://github.com/user-attachments/assets/77e9eaf0-8534-44eb-b45a-9c5baa1c4883" />




## Result:
Thus the program to implement the simple linear regression model for predicting the marks scored is written and verified using python programming.
