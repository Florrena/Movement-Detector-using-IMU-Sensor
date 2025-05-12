# Movement-Detector-using-IMU-Sensor
Predicts movement based on IMU data (accelerometer and gyroscope)

## 1. Collect & Prepare Data
I collected the data from free android/IOS app called "Sensor Logger" that tracks your activity. With this app i recorded 4 different movements in outdoor environment, each for 30 seconds (Which turned out to be around 13k of data, which after windowing and splitting the data turned out to be not enough to train my model correctly WILL BE UPDATED) - standing, walking, jogging and running. I retried it couple of times but in the end i chose the ones that were collected during a more natural sessions, making it more representative of real-world conditions.
Each data point includes readings from accelerometer and gyroscope.
![image](https://github.com/user-attachments/assets/29eadee0-1518-4a28-a6f1-afee65f6ff6b)
For this project I will be using the accelerometer.csv and gyroscope.csv and combining them together in python. I will use the callibrated files for higher data accuracy. Once they're combined I save them in a new .csv file. I repeat this process for every movement that i tracked. The raw and unedited data is stored in the folder dataset.
## 2. Splitting and cleaning the data + Chosen model
I decided to go with UniMTS model (it can be found from here https://github.com/xiyuanzh/UniMTS/tree/main). I downloaded it, created new environment and updated the required libraries from requirements.txt file. 
I had to adjust my data to match the one used in the repository. I followed these steps:

Prepare Custom Dataset for Evaluation
Prepare time series as npy files of shape (number_of_samples, sequence_length, channel_dimension). For channel_dimension, follow the order of (acc_x, acc_y, acc_z, gyro_x, gyro_y, gyro_z).
Prepare a json file for label descriptions as shown above.
Normalize time series measurements (
m
/
s
2
 for acceleration).

All the preparation of my data can be found in cleaning.ipynb, preparation.ipynb files.


After the preparation i run the model and got results from wandb.ai which looked as followed:

Accuracy on train test set **before** fine-tuning the model.
![image](https://github.com/user-attachments/assets/9833fa1a-24a3-4a35-9732-11e4599a5933)

Accuracy on train test set **after** fine-tuning the model.
![image](https://github.com/user-attachments/assets/6c615a72-b57c-47a8-b5fc-7ca5309231df)

Model performance on validation data after tuning it with test data set.
![image](https://github.com/user-attachments/assets/b680db23-bc68-4fe4-bb89-57faf33e733c)
