# Movement-Detector-using-IMU-Sensor
This project predicts types of movement using IMU sensor data (accelerometer and gyroscope).

## 1. Overview
This repository demonstrates how to collect, preprocess, and classify movement data using an IMU sensor. The data is collected via a mobile app, processed and put into the UniMTS deep learning model for classification.

## 2. Data Collection & Preparation
I collected the data from free android/IOS app called "Sensor Logger" that tracks your activity. With this app i recorded 4 different movements in outdoor environment, each for 30 seconds (Which turned out to be around 13k of data, which after windowing and splitting the data turned out to be not enough to train my model correctly **WILL BE UPDATED**) - standing, walking, jogging and running. I retried it couple of times but in the end i chose the ones that were collected during a more natural sessions, making it more representative of real-world conditions.
Each data point includes readings from accelerometer and gyroscope.
![image](https://github.com/user-attachments/assets/29eadee0-1518-4a28-a6f1-afee65f6ff6b)
Each data point contains 6 IMU features:
- Accelerometer: `acc_x`, `acc_y`, `acc_z`
- Gyroscope: `gyro_x`, `gyro_y`, `gyro_z`

  
For this project I will be using the accelerometer.csv and gyroscope.csv and combining them together in python. I will use the callibrated files for higher data accuracy. 
The `accelerometer.csv` and `gyroscope.csv` files were:
- Calibrated for better accuracy
- Combined in Python into a single `.csv` file per movement type
- Saved into a combined, cleaned dataset
  
## 3. Splitting and cleaning the data + Chosen model
I decided to go with UniMTS model (it can be found from here https://github.com/xiyuanzh/UniMTS/tree/main). I downloaded it, created new environment and updated the required libraries from requirements.txt file. 
I had to adjust my data to match the one used in the repository. 
My setup Steps:
1. Cloned UniMTS and created a new Python environment.
2. Installed required libraries from `requirements.txt`.
3. Converted custom dataset to `.npy` format:  
   Shape: `(num_samples, sequence_length, 6)` where 6 = `acc_x`, `acc_y`, `acc_z`, `gyro_x`, `gyro_y`, `gyro_z`
4. Created a `.json` file for label descriptions. (`labels.json`)
5. Normalized time series data (e.g., m/s² for acceleration).
6. Stored all the required data in data folder for UniMTS model.

All preprocessing steps are available in:
- `cleaning.ipynb`
- `preparation.ipynb`

Training and fine-tuning were done using Weights & Biases (wandb.ai)
After the preparation i run the model and got results which looked as followed:  
1. Accuracy on train test set **before** fine-tuning the model.
![image](https://github.com/user-attachments/assets/9833fa1a-24a3-4a35-9732-11e4599a5933)

2. Accuracy on train test set **after** fine-tuning the model.
![image](https://github.com/user-attachments/assets/6c615a72-b57c-47a8-b5fc-7ca5309231df)

3. Model performance on validation data after tuning it with test data set.
![image](https://github.com/user-attachments/assets/b680db23-bc68-4fe4-bb89-57faf33e733c)


**WORK IN PROGRESS**

License
`@misc{zhang2024unimtsunifiedpretrainingmotion,
      title={UniMTS: Unified Pre-training for Motion Time Series}, 
      author={Xiyuan Zhang and Diyan Teng and Ranak Roy Chowdhury and Shuheng Li and Dezhi Hong and Rajesh K. Gupta and Jingbo Shang},
      year={2024},
      eprint={2410.19818},
      archivePrefix={arXiv},
      primaryClass={eess.SP},
      url={https://arxiv.org/abs/2410.19818}, 
}`
