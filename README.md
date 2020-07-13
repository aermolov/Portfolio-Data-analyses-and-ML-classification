# Analyses of loan history and predictions
Example of data analyses and ML classification problem performed on a small set of sales data.
The repository consists of only two files: dataset and jupyter notebook file which you can download on your local machine to run the script. All the explonations are also given inside
jupyter notebook file.

Description
- The data shows the sales made in 2019-2020
- Each line is a sale (Account) with a product (e.g. LPG3) and a loan associated with the product (Total amount = Downpayment + Loan Principal)
- Cycle indicates how many products the client has bought, 1 means this sale is the first one, 3 means is the third purchase for the same client
- TRP is a measure of how well the client is paying the loan, see below for definition. TRP stays for "Timely Repayment Percentage" and displays the number of loan installments that have been paid on time, as a percentage of the total number of loan installments that are due.
- Each client belongs to a Group of at least five members
- Each loan is a payment plan with a certain number of Installments which are paid monthly
- Each loan has a start date (Disbursed Date) and a date when it was fully paid (Final Payment Date), hence theoretical end date is Disbursed Date + N monthly Instalments


Using the data following points are investigated:
### 1. In which order clients that bought more than one product make their purchases? Do they first buy an LPG and then a stove or a solar lamp?
#### Distrubution of groups of products for clients who purchase more than one product
##### First product purchased
|LPG|Stove|Solar|Agricalture|
|-|-|-|-|
|1038|505|341|154|
##### Second products purchased:
|Stove|Agricalture|LPG|SOlar|
|-|-|-|-|
|613|584|436|405|
##### Third products purchased:
|Agricalture|Stove|Solar|LPG|
|-|-|-|-|
|32|27|25|18|

### 2. Any correlation/pattern between age of client and choice of product bought?
![boxplot](https://user-images.githubusercontent.com/42376293/87291872-48300580-c500-11ea-9926-0db8fe545e41.png)
#### There is a clear trend that older people more likely buy agricalture products.
|Product group|LPG|Stove|Agrecalture|Solar|
|-|-|-|-|-|
|Mean age|35|37|43|38|

### 3. Repayment behaviour measured with TRP and choice of product bought?
![boxplot_trp](https://user-images.githubusercontent.com/42376293/87292899-ca6cf980-c501-11ea-8a68-c895880198b4.png)
#### Agricalture and Stove products are puchased better compare to LPG and Solar. Possibly correlated with age
|Product group|LPG|Stove|Agrecalture|Solar|
|-|-|-|-|-|
|TRP (%)|50|60|60|50|

### 4. Any correlation/pattern between gender and choice of product bought?
#### There is a correlation between group of product and gender of the client: mens buy more often LPG and much less often Stoves compare to women. However LPG and Stoves are the most popular products for both genders. 
|Gender|Female|Male|
|-|-|-|
|Product groupd| | |
|Agricalture|0.145908|0.127807|
|LPG|0.423056|0.561427|
|Solar|0.136279|0.151145|
|Stove|0.294044|0.159511|

### 5. How long do clients really take to fully pay their loans, what is the distribution? Any difference between products?
#### Distrubution of the time that clients take to fully pay their loans for each product category are shown below:
![loan_payment_period_dist](https://user-images.githubusercontent.com/42376293/87293785-18363180-c503-11ea-90ea-28f2bdd4935a.png)
#### Stove product has the longest average payment period (189 days). The shortest is with Agricaltural and LPG products (144 and 147 days). 
|Product group|LPG|Stove|Agrecalture|Solar|
|-|-|-|-|-|
|Average payment period (days)|147|189|144|177|

### 6. Of all the products sold which ones would you push more given the historical demand and the repayment behaviour and why?
#### Customers, who buy stoves, show the best payment behavior, fraction of overdue payments are 14%.  Solar product category are paid the least carefully, with fraction of overdue payments of 19%.
#### LPG category has to pushed for sales. It is of very high demand (50% of the all products sold), has short payment period and low number of overdue payments. 
#### Stoves is the next product category that should be pushed. Despite the longest payment period, it has low fraction of overdue payments and relatevely high demand of 25%

### 7. Based on the most relevant features, biuld ML classifier that can predict which clients will pay the loan in time, define the most relevant features.

#### In classifier the following features are exploited:
* Total amount - Full loan amount
* Prepayment - paid by client in advance
* Cycle - 1 - if this is a first purchase, 2 - second purchase, etc.
* Installments - number of installments
* TRP - payment behavior (see above in the description)
* Age
* Gender
* Product group

#### Scikit-learn random forest classifier has been used with f1 score of 0.71. About 2/3 0f "not paid" loans are predicted.
#### The most important feature is the payment history of TRP, followed by prepayment amount and Age
|Feature|TRP|Prepayment|Age|Installment|Total Amount|Cycle|Product Group|Gender|
|-|-|-|-|-|-|-|-|-|
|Feature importance (%)|36|28.6|19.3|6.4|4.4|2|2|1.3|

#### Learning curve behaviour suggests that increasing number of observations can help improve accuracy of the model
![learning_curve](https://user-images.githubusercontent.com/42376293/87297107-29ce0800-c508-11ea-8aaa-28fbc62e4f9d.png)
