<h1> Bank_Customer_Churn_Classification </h1>
# Bank-Customer-Segmentation
<h3> Project Description</h3><br>
<p> In this project the goal is to identify the customers that are going to churn. We get the data set from <a href=https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers>Kaggle</a>, which contains customer features and whether they have churned the bank or they are still active members. In this data set, we can detect the future customers that are going to churn the bank, using a classification algorithm. By doing so, banks can identify the customers that are capable of leaving, and do prohibitive actions. I used the same dataset in a previous repository to identify different customers' behaviour.</p>
<h3>Road Map for Solving the Problem</h3>
<p> We use the following steps to identify customers who are going to leave the bank:<br>
  <ol>
    <li> Use data processing tools to identify missing values, and convert the string columns into numerical values (using onehotencoding). I also use a transformation for other data types used (i.e., used minmax transformation for integer data types and standard scaler for float data types)</li>
    <li>I use feature selection to identify important features having important effect on the resulting output classes. I do feature selection based on the nature of the features and predictions. For the features that take continuous numbers, I use a t-test (because there are only two output classes) to determine whether that feature has important effect on the model output. For the integer data type (i.e., categorical data types), I use a chi-squared test to evaluate whether the corresponding features have significant effects on the corresponding classes.</li>
    <li> I use some explanatory data analysis to obtain some relationship between different features and between features and the output classes. </li>
    <li>Use a classification algorithm to fit a classification algorithm. By doing so, the bank compnay can identify their customers who are going to leave the company. I did this algorithm by using a random forest algorithm.</li>
    
  </ol>
<h3> Data preprocessing </h3>
<p> The initial data set for this data analysis problem is shown as follows:<br>
  <img src='https://github.com/kaveh7293/Bank-Churn-Customer-Prediction/blob/main/Screenshot%202022-07-11%20140037.png' width="850" height="200"><br>
  <img src='https://github.com/kaveh7293/Bank-Churn-Customer-Prediction/blob/main/Screenshot%202022-07-11%20140723.png' width="850" height="200"><br>
  As can be seen, three different data types are available (i.e., float, integer and string (categorical)). I used a column transformation to convert these columns into their corresponding numerical values. Note that, the data shown in the above tables are not all the columns in the data. For the sake of brevity, we did not show all the columns. 
  
</p>
