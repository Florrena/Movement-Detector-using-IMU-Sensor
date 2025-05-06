# Movement-Detector-using-IMU-Sensor
Predicts movement based on IMU data (accelerometer and gyroscope)

## 1. Collect & Prepare Data
I collected the data from free android/IOS app called "Sensor Logger" that tracks your activity. With this app i recorded 4 different movements in outdoor environment, each for 30 seconds - standing, walking, jogging and running. I retried it couple of times but in the end i chose the ones that were collected during a more natural sessions, making it more representative of real-world conditions.
Each data point includes readings from accelerometer and gyroscope.
![image](https://github.com/user-attachments/assets/29eadee0-1518-4a28-a6f1-afee65f6ff6b)
For this project I will be using the accelerometer.csv and gyroscope.csv and combining them together in python. I will use the callibrated files for higher data accuracy. Once they're combined I save them in a new .csv file. I repeat this process for every movement that i tracked.
