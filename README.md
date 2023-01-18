## <p align="center">Weighted Weak Learners for Random Forests</p>
#### <p align="center">Ray Jennings III</p>
#### <p align="center">Computer Science Department, Pace University, New York, NY, USA</p>
#### <p align="center"><i>rj07609p@pace.edu</i></p>
<br>

The predictions from a random forest are based on the aggregate votes from the set of weak learners that comprise the random forest. The aggregation is commonly done by using majority voting where each weak learner has a vote of 1 for the class that it predicted. The class with the largest number of votes is used for the final prediction. The weak learners can sometimes be created with varying degrees of performance. This can, at times, be caused by the data selected during the bootstrapping where some weak learners might not see the entire set of classes. Previous works have shown that using a weighted vote instead of a majority vote can frequently improve the accuracy of a random forest. One technique [1] is to use only a subset of the weak learners where the subset is chosen based on a similarity measure between instances already seen. This technique requires additional execution time for the similarity calculation, plus additional memory to save the information at every leaf node. Another technique used [2] is to weight each of the weak learners by the performance based on the OOB data. I propose a method where a weight for each weak learner is assigned as:


<br>

$$\ weight_i=(accuracy_i)^p \$$

<br>

Values for p typically range from 1 to 10. The accuracy of each weak learner is computed during the validation phase. Like [2], the final predicated class is the one with the highest score. The best value of p is highly dependent upon the variance of the dataset. The higher the value of p puts more emphasis on the higher accuracy trees and less emphasis on the lower accuracy trees. When the accuracy is known for a non-weighted random forest, then an appropriate value for p can be selected. Multiple datasets were chosen to test this proposal. Each test uses a 5 k-fold cross validation. The table below shows the accuracies for a standard random forest (RF), this version of the weighted random forest with p = 5 (WRF) and Scikit-learn’s Random Forest Classifier (SKL) [4] used as a benchmark. The Sonar Rock or Mine dataset [3] was used.

<br>
<br>

**References**

[1]	Robnik-Šikonja, M. (2004), “Improving Random Forests,” Machine Learning: ECML 2004. ECML 2004. Lecture Notes in Computer Science(), vol 3201. Springer, Berlin, Heidelberg.

[2]	M. El Habib Daho, N. Settouti, M. El Amine Lazouni and M. El Amine Chikh, “Weighted vote for trees aggregation in Random Forest,” 2014 International Conference on Multimedia Computing and Systems (ICMCS), 2014, pp. 438-443, doi: 10.1109/ICMCS.2014.6911187.

[3]	Connectionist Bench (Sonar, Mines vs. Rocks). UCI Machine Learning Repository.

[4]	https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html
