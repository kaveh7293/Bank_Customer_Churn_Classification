<h1> Bank_Customer_Churn_Classification </h1>
# Bank-Customer-Segmentation
<h3> Project Description</h3><br>
<p> In this project the goal is to identify the customers that are going to churn. We get the data set from <a href=https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers>Kaggle</a>, which contains customer features and whether they have churned the bank or they are still active members. In this data set, we can detect the future customers that are going to churn the bank, using a classification algorithm. By doing so, banks can identify the customers that are capable of leaving, and do prohibitive actions. I used the same dataset in a previous repository to identify different customers' behaviour.</p>
<h3>Road Map for Solving the Problem</h3>
<p> We use the following steps to identify customers who are going to leave the bank:<br>
  <ol>
    <li> Use data processing tools to identify missing values, and convert the string columns into numerical values (using onehotencoding). I also use a transformation for other data types used (i.e., used minmax transformation for integer data types and standard scaler for float data types)</li>
    <li>I use feature selection to identify important features having important effect on the resulting output classes. I do feature selection based on the nature of the features and predictions. For the features that take continuous numbers, I use a t-test (because there are only two output classes) to determine whether that feature has important effect on the model output. For the categorical data types, I use a chi-squared test to evaluate whether the corresponding features have significant effects on the corresponding classes.</li>
    <li> I use some explanatory data analysis to obtain some relationship between different features and between features and the output classes. </li>
    <li>Use a classification algorithm to fit a classification algorithm. By doing so, the bank compnay can identify their customers who are going to leave the company. I did this algorithm by using a random forest algorithm.</li>
    
  </ol>
<h3> Data preprocessing </h3>
<p> The initial data set for this data analysis problem is shown as follows:<br>
  <img src='https://github.com/kaveh7293/Bank-Churn-Customer-Prediction/blob/main/Screenshot%202022-07-11%20140037.png' width="850" height="200"><br>
  <img src='https://github.com/kaveh7293/Bank-Churn-Customer-Prediction/blob/main/Screenshot%202022-07-11%20140723.png' width="850" height="200"><br>
  As can be seen, three different data types are available (i.e., float, integer and string (categorical)). I used a column transformation to convert these columns into their corresponding numerical values. Note that, the data shown in the above tables are not all the columns in the data. For the sake of brevity, we did not show all the columns. 
  
<h3> Feature Selection and Explanatory Data Analysis (EDA) </h3>
<p>I do feature selection and EDA simultaneously because I think these two steps should be done together. For the categorical features, I did a F test in the scipy library. To do that, I first created a cross table using pandas. Then, I evaluate whether especific cateogries have influence on the outcomes. I do not show all the results for the sake of brevity. A summary of the results can be found as follows:
<ol>  
  <li> I evaluated whether members from different genders (e.g., men and women) have an influence on our outcome. I first created a cross table:<br><br>

<img src='https://github.com/kaveh7293/Bank_Customer_Churn_Classification/blob/main/Screenshot%202022-07-19%20150753.jpg'><br>
  
  Using this cross table, I did a F-test and the corresponding p-value obtained 0.0002, so the effect of  geder types on the output is significant. We can also obtain this conclusion based on the countplot below:<br><br>
 <img src='https://github.com/kaveh7293/Bank_Customer_Churn_Classification/blob/main/download.png' width='400' height='300'><br>
  As shwon, women are more likely to leave the bank compared to men customers.</li>
  <li>I also did a F-test to determine whether level of education has important effects on the output. The <strong>p-value </strong> for this statistical test obtained <strong> 0.051 </strong> which is very <strong> close </strong> to the typical <strong> critical value of 0.05 </strong>. As a result, depending on the financial loss for the type one error or type two error, we can either maintain this feature or do not involve it for model predictions. For example, if the education level does not really influence the outcome, but we consider it for training a model, we only spend some computation time (i.e., <strong> the corresponding costs for type 1 error is negligible </strong>). However, if the education level, in reality, does influence the customer behaviour and we ignore it (i.e., <strong> type 2 error </strong>), the corresponding financial loss could be large (i.e., bank could save so much money by preventing the customers to leave). As a result,<strong> since the financial loss for type 2 error is less, I keep feature corresponding to the education level </strong>. </li>
  <li> Effect of income category on the output is significant because the corresponding p-value is 0.025. However, the effect of Card type and martial status is negligible because the corresponding p-values are 0.52 and 0.11. For example, the normalized catplot:<br>
    <img src='https://github.com/kaveh7293/Bank_Customer_Churn_Classification/blob/main/Class_2.png'><br>
   
   <p>As shown, there is not a signficant relationship between the customers with different credit cards and the corresponding outputs.</p>
   <li> I also used a one-way ANOVA test to determine whether numeric features have a significant relationship with the output. The followin results were obtained using a for loop for all the columns containing numerical values:<br>
     <ul>
       <li>Effect of <strong>Customer_Age </strong> is <strong> significant</strong>.</li>
       <li>Eeffect of  <strong>Dependent_count </strong>  is <strong> significant</strong>.</li>
       <li>Effect of <strong>Months_on_book </strong> is <strong> not significant </strong>.</li>
       <li>Effect of <strong>Total_Relationship_Count </strong> is <strong> significant.</strong></li>
       <li>Effect of <strong>Months_Inactive_12_mon </strong> is <strong> significant</strong>.</li>
       <li>Effect of <strong>Contacts_Count_12_mon </strong> is <strong> significant</strong>.</li>
       <li>Effect of <strong>Total_Trans_Ct </strong> is <strong> significant</strong>.</li>
       <li>Effect of <strong>Credit_Limit </strong> is <strong> significant </strong>.</li>
       <li>Effect of <strong>Total_Revolving_Bal</strong> is <strong> significant</strong>.</li>
       <li>Effect of <strong>Avg_Open_To_Buy </strong> is <strong> not significant </strong>.</li>
       <li>Effect of <strong>Total_Amt_Chng_Q4_Q1 </strong> is <strong>significant</strong>.</li>
       <li>Effect of <strong>Total_Trans_Amt</strong>  is <strong> significant</strong>.</li></ul>
     </ol>
     <p> Note that, a critical value of 0.1 is considered because the financial loss corresponding to encountering with type 2 error is higher. The <strong> p-values </strong> for the features that have not been selected were <strong> 0.16 </strong>and <strong>0.97 </strong>.

     
  
  
  
  
  </li>
  </ol> 
</p>
