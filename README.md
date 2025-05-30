# Developing a Neural Network Classification Model

## AIM

To develop a neural network classification model for the given dataset.

## Problem Statement

An automobile company has plans to enter new markets with their existing products. After intensive market research, they’ve decided that the behavior of the new market is similar to their existing market.

In their existing market, the sales team has classified all customers into 4 segments (A, B, C, D ). Then, they performed segmented outreach and communication for a different segment of customers. This strategy has work exceptionally well for them. They plan to use the same strategy for the new markets.

You are required to help the manager to predict the right group of the new customers.

## Neural Network Model

![Screenshot 2025-05-26 104032](https://github.com/user-attachments/assets/f1e64058-8a47-4a94-af27-155d279a0766)



## DESIGN STEPS

### STEP 1:
Understand the classification task and identify input and output variables.

### STEP 2:
Gather data, clean it, handle missing values, and split it into training and test sets.

### STEP 3:
Normalize/standardize features, encode categorical labels, and reshape data if needed.

### STEP 4:
Choose the number of layers, neurons, and activation functions for your neural network.

### STEP 5:
Select a loss function (e.g., binary cross-entropy), optimizer (e.g., Adam), and metrics (e.g., accuracy).

### STEP 6:
Feed training data into the model, run multiple epochs, and monitor the loss and accuracy.

### STEP 7:
Save the trained model, export it if needed, and deploy it for real-world use.


## PROGRAM

### Name: ANU VARSHINI M B
### Register Number: 212223240010

```python
class PeopleClassifier(nn.Module):
    def __init__(self, input_size):
        super(PeopleClassifier, self).__init__()
        self.fc1 = nn.Linear(input_size, 32)
        self.fc2 = nn.Linear(10, 8)
        self.fc3 = nn.Linear(8, 5)
        self.fc4 = nn.Linear(5, 4)
    def forward(self, x):
        x=F.relu(self.fc1(x))
        x=F.relu(self.fc2(x))
        x=F.relu(self.fc3(x))
        x=self.fc4(x)
        return x
```
```python
# Initialize the Model, Loss Function, and Optimizer
model =PeopleClassifier(input_size=X_train.shape[1])
criterion =nn.CrossEntropyLoss()
optimizer =optim.Adam(model.parameters(),lr=0.001)
```
```python
def train_model(model,train_loader,criterion,optimizer,epochs):
  for epoch in range(epochs):
    model.train()
    for X_batch,y_batch in train_loader:
      optimizer.zero_grad()
      outputs=model(X_batch)
      loss=criterion(outputs,y_batch)
      loss.backward()
      optimizer.step()

  if(epoch+1)%10==0:
    print(f'Epoch [{epoch+1}/{epochs}],Loss:{loss.item():.4f}')
```
## Dataset Information

![Screenshot 2025-03-16 212227](https://github.com/user-attachments/assets/38628bb1-3047-478a-8084-ac71f55b5d62)

## OUTPUT
### Confusion Matrix

![Screenshot 2025-03-16 212321](https://github.com/user-attachments/assets/fc197f98-21dc-4811-866a-363bd0d0bc9d)


### Classification Report

![Screenshot 2025-03-16 212405](https://github.com/user-attachments/assets/55aeb822-dbd9-4d88-9da8-7398ac4035bd)

### New Sample Data Prediction

![Screenshot 2025-03-16 212456](https://github.com/user-attachments/assets/89ece0ef-eae7-4ea8-bbce-e7a0167f42fd)


## RESULT
Thus a neural network classification model for the given dataset is executed successfully.
