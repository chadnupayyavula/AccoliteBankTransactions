# AccoliteBankTransactions


Basic Bank system requirements

To do this assignment I have created my own web api it queries form the sql database which I created and hosted both in azure.

SQL Database diagram

 

•	Account number in users table is primary key and applied identity on it.
•	two tables have relationship on account number column
You can find the web api swagger   htps://accolitebanktransactions.azurewebsites.net/swagger/index.html

It has 2 controllers with different api’s

 

PUT in Bank Transactions  :
1.	It takes json as input returns and returns string response
2.	If there are no matched accounts it will return “No record found with this customerId”
3.	API returns 500 error when  we pass invalid amount i.e negative numbers,  try to withdraw more than 90% of the balance ,  your valance less than 100$ by withdrawal  and If you try to deposit more than 10000$ 
4.	It returns Success message on successful request.

{
  "customerId": 100022,
  "type": 0,    // credit = 0 and withdraw  1
  "amount": 100
}
{
Get in Bank Transactions  :
1.	It takes the url parameter and returns the json array
2.	If no match found return empty list

Response body
[
  {
    "customerId": 10021,
    "credit": 100,
    "debit": 0,
    "balance": 100,
    "lastUpdated": "2023-11-04T10:22:50"
  }
]]

Post in user Registration

1.	It takes json as the request and returns account numbers 
2.	 API returns 500 When pass empty value for customer name and When you update multipleaccounts to true but pass number of accounts = 0 
3.	On Successful Creation, it creates a record for default balance of 100.

Get in user Registration

1.	It takes 2 parameters one is account number and Name
2.	We need to pass either of the parameters 
3.	If we pass account number it fetches only one account
4.	If we pass Name it fetches all matched accounts with the name



Response Body:e
ResRe [
  {
    "customerId": 10220,
    "customerName": "Chandu"
  },
  {
    "customerId": 10221,
    "customerName": "Chandu"
  },
  {
    "customerId": 10222,
    "customerName": "Chandu"
  }
  ]
  "amount": 100



Delete In User Registration:
1.	It takes 2 parameters one is account number and Name
2.	We need to pass either of the parameters 
3.	If we pass account number it deletes only one account
4.	If we pass Name it deletes all matched accounts with the name
5.	If we pass name or account number which does not exist it returns 500 error
6.	On successful deletion It deletes the records in Transaction table first then In Users table as we have primary and foreign key relationship between two tables
