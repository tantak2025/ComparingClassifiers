# ComparingClassifiers
Compare the performance of the classifiers (k-nearest neighbors, logistic regression, decision trees, and support vector machines) 

Input variables:
# bank client data:
1 - age (numeric)
2 - job : type of job (categorical: 'admin.','blue-collar','entrepreneur','housemaid','management','retired','self-employed','services','student','technician','unemployed','unknown')
3 - marital : marital status (categorical: 'divorced','married','single','unknown'; note: 'divorced' means divorced or widowed)
4 - education (categorical: 'basic.4y','basic.6y','basic.9y','high.school','illiterate','professional.course','university.degree','unknown')
5 - default: has credit in default? (categorical: 'no','yes','unknown')
6 - housing: has housing loan? (categorical: 'no','yes','unknown')
7 - loan: has personal loan? (categorical: 'no','yes','unknown')
# related with the last contact of the current campaign:
8 - contact: contact communication type (categorical: 'cellular','telephone')
9 - month: last contact month of year (categorical: 'jan', 'feb', 'mar', ..., 'nov', 'dec')
10 - day_of_week: last contact day of the week (categorical: 'mon','tue','wed','thu','fri')
11 - duration: last contact duration, in seconds (numeric). Important note: this attribute highly affects the output target (e.g., if duration=0 then y='no'). Yet, the duration is not known before a call is performed. Also, after the end of the call y is obviously known. Thus, this input should only be included for benchmark purposes and should be discarded if the intention is to have a realistic predictive model.
# other attributes:
12 - campaign: number of contacts performed during this campaign and for this client (numeric, includes last contact)
13 - pdays: number of days that passed by after the client was last contacted from a previous campaign (numeric; 999 means client was not previously contacted)
14 - previous: number of contacts performed before this campaign and for this client (numeric)
15 - poutcome: outcome of the previous marketing campaign (categorical: 'failure','nonexistent','success')
# social and economic context attributes
16 - emp.var.rate: employment variation rate - quarterly indicator (numeric)
17 - cons.price.idx: consumer price index - monthly indicator (numeric)
18 - cons.conf.idx: consumer confidence index - monthly indicator (numeric)
19 - euribor3m: euribor 3 month rate - daily indicator (numeric)
20 - nr.employed: number of employees - quarterly indicator (numeric)

Output variable (desired target):
21 - y - has the client subscribed a term deposit? (binary: 'yes','no')

#### Summary of Numerical Feature Analysis

Based on the descriptive statistics and distribution plots of the numerical features, the following observations can be made:

*   **Age:** The age distribution appears to be somewhat normally distributed, centered around 40, with a range from 17 to 98 years. There are no obvious outliers.
*   **Duration:** This feature is highly right-skewed, with most contact durations being short. As previously noted, the minimum duration of 0 seconds is particularly important due to its implications for data leakage.
*   **Campaign:** The number of contacts made during this campaign is also highly right-skewed, indicating that most clients were contacted only a few times. A small number of clients were contacted many times.
*   **Pdays:** This feature is heavily concentrated at 999, which signifies that the client was not previously contacted. This suggests that 'pdays' might be better represented as a categorical or binary feature (contacted previously vs. not contacted).
*   **Previous:** Similar to 'campaign', this feature is right-skewed, with most clients having had zero previous contacts before this campaign.
*   **Economic Indicators (emp.var.rate, cons.price.idx, cons.conf.idx, euribor3m, nr.employed):** These macroeconomic variables show varied distributions. Some might exhibit multiple modes, indicating different economic periods, while others might be more uniformly distributed across certain ranges. These features will be crucial for capturing external influences on term deposit subscriptions.


The Support Vector Machine took significantly longer to train, while the K-Nearest Neighbors was the fastest. In terms of test accuracy, Logistic Regression and Support Vector Machine performed similarly to the baseline. The Decision Tree had the highest training accuracy but a lower test accuracy, indicating potential overfitting. KNN achieved a slightly better training accuracy than the baseline, but a slightly worse test accuracy.
