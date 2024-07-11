# Spatial Reasoning Assessment: A Game-based Approach

## Abstract
Game-based assessment, which involves using games for learning purposes, is seen as a different way to assess students' knowledge and skills. Although there is a lot of research supporting the educational advantages of using GBA, there is not enough study on how valid and applicable these systems are in different contexts. Our goal was to design a game to find a possible correlation between the performance of participants in the game and the results of their paper tests by analyzing the data obtained from the participants. <br>
Our study suggests that the game we designed can effectively evaluate spatial reasoning abilities, as there was a strong relationship between the outcomes.

## Introduction
### Problem Statement
Spatial visualization skills and mental rotation abilities are essential for success in technical and engineering professions (Norman ,1994) [1]. These skills are crucial for manipulating objects and using computer-aided design effectively. Understanding the significance of spatial abilities in engineering and technology education, it is imperative for students with weak spatial skills to enhance them through suitable instructional methods. <br>
Recent research suggests that spatial reasoning skills can be improved through training, with the effects lasting long-term and transferring to various types of spatial tasks (Uttal et al., 2013) [2]. Furthermore, a study has shown that middle-school students who receive spatial reasoning skills training alongside their regular curriculum experience academic benefits (Sorby, 2009) [3]. There are limited resources and options for training and evaluating spatial reasoning skills compared to other cognitive skills like mathematical or verbal abilities (Uttal et al., 2013) [2]. To address this issue, it is important to create game- based assessments that can also effectively improve and develop specific spatial reasoning skills. <br>
Evaluating a learner's spatial abilities is important for ensuring that they can apply what they have learned, and it is crucial to use the right teaching methods to support their growth. There are various tools available for assessing a learner's spatial skills. One of the most common test is the Mental Rotation Test (MRT) which assesses spatial visualization and mental rotation components. The MRT consists of a series of five line drawings showing a target figure on the left followed by two rotated versions of the target and two distractors. The task is to identify which two drawings are the accurate rotated replicas of the target figure. <br>
According to the above statements, the paper test is a reliable method for assessing spatial reasoning. Therefore, it is necessary to have a very strong correlation between the results of any new method used to evaluate this skill and the paper test. In that case, we can be sure improving performance in the game has resulted in a better score without the need for paper testing.

## Related Work
Kim et al. (2023) [4] designed a game called Shadowspect with the intention of assessing fundamental Geometry standards and spatial reasoning skills, as well as key attributes and behaviors that have long-term impacts, like persistence. Additionally, two assessments of spatial reasoning were conducted: the Spatial Reasoning Instrument (SRI) and the Santa Barbara Solids Test (SBST), which is a test that assesses spatial reasoning across various dimensions. To determine if Shadowspect can effectively assess spatial reasoning skills, they created Random Forest regression models using scikit-learn. These models were used to evaluate the correlation between Shadowspect features (such as persistence and competency scores) and external measures of spatial reasoning. Additionally, the models helped identify which features were most important in predicting spatial reasoning abilities. Two separate models were developed for each of the external measures, SRI and SBST. The overall performance of the two Random Forest regression models can be seen in the table below.

| Model      | r | R^2 | MAE (% of error) | MSE (% of error) |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| SRI      | 54% | 28% | 4.4 (15%) | 5.0 (17%) |
| SBST   | 31% | 0.2% | 5.7 (19%) | 7.0 (23%) |

## Methodology
### Data Acquisition
The experiment was conducted at the Mechatronics Laboratory of Khaje Nasir Toosi University with the participation of students from this university. In this experiment, which was done in two stages, each participant first did a paper test (MRT) and then was required to play the designed game. The method is as follows: on a display located on the right side of the participant, a three-dimensional image made with a number of cubes is shown. While watching this image, both hands of the participant are placed under the table. The goal is for the participant to reconstruct the image using the smallest number of cubes that are placed in front of them on the table. Each participant completed a total of six different tasks. <br>
To obtain raw data, the hands and faces of the participants were recorded by a camera. In the video processing stage, specific points on the face and hands were considered and the positions of each of these points were stored in three dimensions. In addition, a parameter was considered to determine whether the participant's hand is visible to the camera or not. Also, the yaw and pitch angles of the face were also stored in a separate file.

### Data Used
It is necessary to prepare understandable quantities of raw data. The extracted parameters are as follows:
- The time interval between the first time the participant raised their hand from under the table until the last time they put their hand under the table again.
- The initial time of looking at the question before making any move.
- The number of times the participant looked at the question after starting to solve the puzzle.
- The number of times the participant stopped.
- The total time the participant hesitated in solving the question. To calculate this time,
a threshold value of 0.14 seconds was used, as the participant may be moving
themselves on the chair, which is meaningless to be includec in the analysis.
- Velocity and jerk of both hands. Initially, the instantaneous values of each were
calculated, and ultimately the average of all instantaneous values was taken.
- Velocity of head. Using the yaw and pitch angles, instantaneous angular velocities
were calculated. Finally, the average of all values was taken into consideration.
It is worth mentioning that all these values have been calculated for each of the six tasks, seperately. One approach was to take the average of the six values for each participant, but we preferred to keep the values to increase precision.

### Method
Initially, using a Random Forest regression model, the importance of each feature was calculated. In the diagram below, you can see the top ten important features from which the top five were chosen. <br>
<img width="787" alt="Screen Shot 2024-07-12 at 1 30 09 AM" src="https://github.com/user-attachments/assets/43ab04ee-5723-488d-8606-ffa492360551">
<br>
Two regression models, Random Forest and XGBoost, were constructed to examine how well they can perform in estimating MRT score. After tuning the hyperparameters using grid search of each model, they were k-fold cross-validated (k = 5) to ensure that the results are robust.

## Results
The results obtained from each model are presented in the table below.
| Model      | r | R^2 | MAE (% of error) | MSE (% of error) |
| ----------- | ----------- | ----------- | ----------- | ----------- |
| Random Forest | 66.9% | 39.7% | 3.76 (15%) | 4.76 (0.1%) |
| XGBoost | 94.36% | 84.37% | 1.98 (0.04%) | 2.44 (0.05%) |

Our findings demonstrate that we have sufficient evidence for the validity of our game as an assessment of spatial reasoning skills. Moreover, XGboost shows very promising results and a high correlation. We have succesfully indicated that our proposed work can be used to replace traditional paper-based tests.
## Discussion and Conclusion
We designed a game and investigated whether we could find a relationship between participants' performance and their spatial reasoning skills or not. The results indicate the very good ability of this game and its tasks in demonstrating participants' skills. Additionally, the XGBoost regression model exhibited a very high capability for prediction, which is much better than what was obtained in previous works.
Since the process of progress in spatial reasoning is gradual and requires consistency in practice, it is necessary for the designed game to be engaging for the player. Therefore, one of the improvements that can be made is to determine the level of satisfaction of the participants with the game and examine how enjoyment affects the results. (Kim et al., 2023). [4]

## References
[1] K. L. Norman, “Spatial Visualization—A Gateway to Computer-Based Technology,” Journal of Special Education Technology, vol.12, no.3, pp. 195-206, Mar 1994. <br>
[2] D. H. Uttal, N. G. Meadow, E. Tipton, L. L. Hand, A. R. Alden, C. Warren and N. S. Newcombe, “The Malleability of Spatial Skills: A Meta-Analysis of Training Studies,” Psychological Bulletin, vol. 139, no. 2, pp. 352-402, Mar 2013. <br>
[3] S. Sorby, “Developing Spatial Cognitive Skills Among Middle School Students,” Cognitive Processing, vol. 10, pp. 312-315, Aug 2009. <br>
[4] Y. J. Kim, M. A. Knowles, J. Scianna, G. Lin and J. A. Ruiperez-Valiente, “Learning Analytics To Examine Validity And Generalizability of Game-based Assessment For Spatial Reasoning,” British Journal of Educational Technology, vol. 54, pp. 355-372, Oct 2022

