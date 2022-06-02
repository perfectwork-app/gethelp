---
title: Manual Inventory Valuation
summary: Manual Inventory Valuation
authors: Wilson Loh
date: 2022-04-21
---

In this case, goods receipts and deliveries won’t have any direct impact on your accounting books. Periodically, you create a manual journal entry representing the value of what you have in stock. To know that value, go in Inventory ‣ Reporting ‣ Inventory Valuation.This is the default configuration in PerfectWORK and it works out-of-the-box. Check following operations and find out how PerfectWORK is managing the accounting postings.

## Continental Accounting

### Vendor Bill

Selling product for $50 with 7% GST Tax

|                               | Debit | Credit |
| ----------------------------- | ----- | ------ |
| Assets: Inventory             | 50    |        |
| Assets: Deferred Tax Assets   | 3.50  |        |
| Liabilities: Accounts Payable |       | 53.50  |

!!!note
    **Configuration**:<BR />
        - _Purchased Goods_: defined on the product or on the internal category of related product (Expense Account field) <BR/>
        - _Deferred Tax Assets_: defined on the tax used on the purchase order line<BR/>
        - _Accounts Payable_: defined on the vendor related to the bill<BR/>

### Goods Receptions

!!!note
    _There is no journal entry generated_
    
At the end of the month/year, your company does a physical inventory or just relies on the inventory in PerfectWORK to value the stock into your books.  Create a journal entry to move the stock variation value from your Profit & Loss section to your assets.

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Assets: Inventory                       |   X   |        |    
| Expenses: Inventory Variation           |       |    X   |
<br /><br />
If the stock value decreased, the **Inventory** account is credited and the **Inventory Variations** debited.

### Customer Invoice

Selling product for $100 with 7% GST Tax

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Revenue: Sold Goods                     |       |   100  |
| Liabilities: Deferred Tax Liabilities   |       |     9  |
| Assets: Accounts Receivable             |  109  |        |

!!!note
    **Configuration**:
        <br /><br />
        - Revenues: defined on the product or on the internal category of related product (Income Account field) <BR />
        - Deferred Tax Liabilities: defined on the tax used on the invoice line <BR />
        - Accounts Receivable: defined on the customer (Receivable Account)
        <br /><br />
    The fiscal position used on the invoice may have a rule that replaces the Income Account or the tax defined on the product by another one.

### Customer Shipping

!!!note
    _There is no journal entry generated_

At the end of the month/year, your company does a physical inventory or just relies on the inventory in PerfectWORK to value the stock into your books.  Create a journal entry to move the stock variation value from your Profit & Loss section to your assets.

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Assets: Inventory                       |   X   |        |    
| Expenses: Inventory Variation           |       |    X   |
<br /><br />
If the stock value decreased, the **Inventory** account is credited and the **Inventory Variations** debited.


### Manufacturing Orders

!!!note
    _There is no journal entry generated_

At the end of the month/year, your company does a physical inventory or just relies on the inventory in PerfectWORK to value the stock into your books.  Create a journal entry to move the stock variation value from your Profit & Loss section to your assets.

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Assets: Inventory                       |   X   |        |    
| Expenses: Inventory Variation           |       |    X   |
<br /><br />
If the stock value decreased, the **Inventory** account is credited and the **Inventory Variations** debited.

## Anglo-Saxon Accounting 

### Vendor Bill

Selling product for $50 with 7% GST Tax

|                               | Debit | Credit |
| ----------------------------- | ----- | ------ |
| Assets: Inventory             | 50    |        |
| Assets: Deferred Tax Assets   | 3.50  |        |
| Liabilities: Accounts Payable |       | 53.50  |

!!!note
    **Configuration**:<BR />
        - _Purchased Goods_: defined on the product or on the internal category of related product (Expense Account field) <BR/>
        - _Deferred Tax Assets_: defined on the tax used on the purchase order line<BR/>
        - _Accounts Payable_: defined on the vendor related to the bill<BR/>

### Goods Receptions

!!!note
    _There is no journal entry generated_
    
At the end of the month/year, your company does a physical inventory or just relies on the inventory in PerfectWORK to value the stock into your books.
<br /><br />
Then you need to break down the purchase balance into both the inventory and the cost of goods sold using the following formula: _Cost of goods sold (COGS) = Starting inventory value + Purchases – Closing inventory value_
<br /><br />
To update the stock valuation in your books, record such an entry:

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Assets: Inventory (closing value)       |   X   |        |    
| Expenses: Cost of Good Sold             |   X   |        |  
| Expenses: Purchased Goods               |       |    X   |    
| Assets: Inventory (starting value)      |       |    X   |  



### Customer Invoice

Selling product for $50 with 7% GST Tax

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Revenue: Sold Goods                     |       |   100  |
| Liabilities: Deferred Tax Liabilities   |       |     9  |
| Assets: Accounts Receivable             |  109  |        |

!!!note
    **Configuration**:
        <br /><br />
        - Revenues: defined on the product or on the internal category of related product (Income Account field) <BR />
        - Deferred Tax Liabilities: defined on the tax used on the invoice line <BR />
        - Accounts Receivable: defined on the customer (Receivable Account)
        <br /><br />
    The fiscal position used on the invoice may have a rule that replaces the Income Account or the tax defined on the product by another one.

### Customer Shipping

!!!note
    _There is no journal entry generated_
    
At the end of the month/year, your company does a physical inventory or just relies on the inventory in PerfectWORK to value the stock into your books.
<br /><br />
Then you need to break down the purchase balance into both the inventory and the cost of goods sold using the following formula: _Cost of goods sold (COGS) = Starting inventory value + Purchases – Closing inventory value_
<br /><br />
To update the stock valuation in your books, record such an entry:

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Assets: Inventory (closing value)       |   X   |        |    
| Expenses: Cost of Good Sold             |   X   |        |  
| Expenses: Purchased Goods               |       |    X   |    
| Assets: Inventory (starting value)      |       |    X   |  

### Manufacturing Orders

!!!note
    _There is no journal entry generated_
    
At the end of the month/year, your company does a physical inventory or just relies on the inventory in PerfectWORK to value the stock into your books.
<br /><br />
Then you need to break down the purchase balance into both the inventory and the cost of goods sold using the following formula: _Cost of goods sold (COGS) = Starting inventory value + Purchases – Closing inventory value_
<br /><br />
To update the stock valuation in your books, record such an entry:

|                                         | Debit | Credit |
| --------------------------------------- | ----- | ------ |
| Assets: Inventory (closing value)       |   X   |        |    
| Expenses: Cost of Good Sold             |   X   |        |  
| Expenses: Purchased Goods               |       |    X   |    
| Assets: Inventory (starting value)      |       |    X   |  

