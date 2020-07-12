# Analyses of loan history and predictions
Example of data analyses and ML classification problem performed on a small set of sales data
The repository consists of only two files: dataset and jupyter notebook file. All the explonations are also given inside
jupyter notebook file

Description
- The data shows the sales made in 2019-2020
- Each line is a sale (Account) with a product (e.g. LPG3) and a loan associated with the product (Total amount = Downpayment + Loan Principal)
- Cycle indicates how many products the client has bought, 1 means this sale is the first one, 3 means is the third purchase for the same client
- TRP is a measure of how well the client is paying the loan, see below for definition. TRP stays for "Timely Repayment Percentage" and displays the number of loan installments that have been paid on time, as a percentage of the total number of loan installments that are due.
- Each client belongs to a Group of at least five members
- Each loan is a payment plan with a certain number of Installments which are paid monthly
- Each loan has a start date (Disbursed Date) and a date when it was fully paid (Final Payment Date), hence theoretical end date is Disbursed Date + N monthly Instalments


Using the data following points will be investigated:
1. In which order clients that bought more than one product make their purchases? Do they first buy an LPG and then a stove or a solar lamp?
2. Any correlation/pattern between age of client and choice of product bought?
3. Repayment behaviour measured with TRP and choice of product bought?
4. Any correlation/pattern between gender and choice of product bought?
5. How long do clients really take to fully pay their loans, what is the distribution? Any difference between products?
6. Of all the products sold which ones would you push more given the historical demand and the repayment behaviour and why? 1.
7. Based on the most relevant features, biuld ML classifier that can predict which clients will pay the loan in time, define the most relevant features.
