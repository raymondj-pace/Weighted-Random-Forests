Weighted Weak Learners for Random Forests


Ray Jennings III
Computer Science Department, Pace University, New York, NY, USA
rj07609p@pace.edu

The predictions from a random forest are based on the aggregate votes from the set of weak learners that comprise the random forest. The aggregation is commonly done by using majority voting where each weak learner has a vote of 1 for the class that it predicted. The class with the largest number of votes is used for the final prediction. The weak learners can sometimes be created with varying degrees of performance. This can, at times, be caused by the data selected during the bootstrapping where some weak learners might not see the entire set of classes. Previous works have shown that using a weighted vote instead of a majority vote can frequently improve the accuracy of a random forest. One technique [1] is to use only a subset of the weak learners where the subset is chosen based on a similarity measure between instances already seen. This technique requires additional execution time for the similarity calculation, plus additional memory to save the information at every leaf node. Another technique used [2] is to weight each of the weak learners by the performance based on the OOB data. I propose a method where a weight for each weak learner is assigned as:

〖weight〗_i=〖(〖accuracy〗_i)〗^p

Values for p typically range from 1 to 10. The accuracy of each weak learner is computed during the validation phase. Like [2], the final predicated class is the one with the highest score. The best value of p is highly dependent upon the variance of the dataset. The higher the value of p puts more emphasis on the higher accuracy trees and less emphasis on the lower accuracy trees. When the accuracy is known for a non-weighted random forest, then an appropriate value for p can be selected. Multiple datasets were chosen to test this proposal. Each test uses a 5 k-fold cross validation. The table below shows the accuracies for a standard random forest (RF), this version of the weighted random forest with p = 5 (WRF) and Scikit-learn’s Random Forest Classifier (SKL) [4] used as a benchmark. The Sonar Rock or Mine dataset [3] was used. 
![image](https://user-images.githubusercontent.com/94663542/213304980-b3c270bf-4ec7-4770-8fdb-e2fc0a2b9ce1.png)
