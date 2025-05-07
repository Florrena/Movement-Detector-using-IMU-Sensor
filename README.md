# Movement-Detector-using-IMU-Sensor
Predicts movement based on IMU data (accelerometer and gyroscope)

## 1. Collect & Prepare Data
I collected the data from free android/IOS app called "Sensor Logger" that tracks your activity. With this app i recorded 4 different movements in outdoor environment, each for 30 seconds - standing, walking, jogging and running. I retried it couple of times but in the end i chose the ones that were collected during a more natural sessions, making it more representative of real-world conditions.
Each data point includes readings from accelerometer and gyroscope.
![image](https://github.com/user-attachments/assets/29eadee0-1518-4a28-a6f1-afee65f6ff6b)
For this project I will be using the accelerometer.csv and gyroscope.csv and combining them together in python. I will use the callibrated files for higher data accuracy. Once they're combined I save them in a new .csv file. I repeat this process for every movement that i tracked. The raw and unedited data is stored in the folder dataset.
## 2. Splitting and cleaning the data
Accuracy on train test set **before** fine-tuning the model.
![image](https://github.com/user-attachments/assets/9833fa1a-24a3-4a35-9732-11e4599a5933)

Accuracy on train test set **after** fine-tuning the model.
![image](https://github.com/user-attachments/assets/6c615a72-b57c-47a8-b5fc-7ca5309231df)

Model performance on validation data after tuning it with test data set.
![image](https://github.com/user-attachments/assets/b680db23-bc68-4fe4-bb89-57faf33e733c)
