# Driver Behaviour - Computer Vision Individual Assigment

## Goal

In this assignment you are given driver images, each taken in a car with a driver doing something
in the car (texting, eating, talking on the phone, makeup, reaching behind, etc). Your goal is to
predict what the driver is doing in each picture.

## Task

Given the 10 posisible classes each image can be, predict the class using different models and startegies.

- c0: safe driving
- c1: texting - right
- c2: talking on the phone - right
- c3: texting - left
- c4: talking on the phone - left
- c5: operating the radio
- c6: drinking
- c7: reaching behind
- c8: hair and makeup
- c9: talking to passenger

Data found at  https://drive.google.com/file/d/1l1pN5ZQ6gELeWR8H1uZr0V05hP3gfpg_/view?usp=sharing

## Metodologies

I used both *transfer learning* and created *CNN models* to find the best solution.

For transfer learning I used the Keras model with the following models:

- VGG16
- MobileNet V1
- MobileNet V2

> Best learning rate = 0.001, other values decrease the model accuracy and increase loss

> Best epoch number = 1, all the models did not yield significal improvements by increasing epoch number


> As weights I used ImageNet

For CNN I started with a model with a Conv2D, MaxPooling2D, Conv2D,MaxPooling2D, Flatten, Dense, optimizer but found that the second layer of Conv2D,MaxPooling2D did not improve the model. i also experiemented with different learning rates with the same results of the transfer learning.

## Results

1. Mobile_net_model_001: This model performs best out of all the models. It has the highest accuracy of 0.9817, and the lowest loss of 0.1163. This means the model predicts most of the test data correctly and has a small number of errors. Its precision, recall and f1-score are also consistently high across all classes (avg 0.98), suggesting that it is robust and performs well regardless of the specific class.

2. CNNmodel_001: It has the second highest accuracy of 0.9817, and the lowest loss of 0.0767. While also having a F1, Recall and Precision of 0.98. This means the model predicts most of the test data correctly and has a small number of errors. Important to notice that F1, Recall and precision are not always consistent across all classes.

3. Mobile_net_v2_model_001: This model also performs well, but it has a slightly lower accuracy (0.9734) and higher loss (0.1556) compared to the Mobile_net_model_001. Its precision, recall and f1-score are quite high, but slightly lower than the Mobile_net_model_001 and CNNmodel_001.

4. vgg16_model: This model has a lower accuracy (0.9697) and a higher loss (0.1341) than the previus models. Its precision, recall and f1-score are slightly lower than those of the previous models, indicating that it is not as accurate in its predictions.

5. Mobile_net_model_01: This model has the same accuracy as Mobile_net_v2_model_001, but significantly higher loss (2.5114), indicating more errors in prediction. While its precision, recall and f1-score are quite high but very incosistent.

6. CNNmodel_a_005 model: This model performs very poorly compared to the others. It has very low accuracy (0.1110) and a very high loss (2.3010), indicating a high number of errors. Its precision, recall and f1-score are also very low, showing poor performance across all classes.

In the context of deploying any of these model the two possible choises are either Mobile_net_model_001 or CNNmodel_001, but given the higher consistency of F1, Recall precision of Mobile_net_model_001, its higher accuracy and lower training time 2.28 (minutes) vs 3.01 (minutes), Mobile_net_model_001 is the optimal choice.