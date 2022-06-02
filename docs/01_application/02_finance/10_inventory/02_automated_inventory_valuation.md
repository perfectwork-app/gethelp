---
title: Automated Inventory Valuation
summary: Automated Inventory Valuation
authors: Wilson Loh
date: 2022-04-21
---

In that case, when a product enters or leaves your stock, an accounting entry will be automatically created. This means your accounting books are always up-to-date. This mode is dedicated to expert accountants and advanced users only. As opposed to periodic valuation, it requires some extra configuration & testing.
<br /><br />
First, you need to define the accounts that will be used for those accounting entries. This is done on the product category.

## Continental Accounting

!!!note
    **Configuration:**

    - Accounts Receivable/Payable: defined on the partner (Accounting tab)
    - Deferred Tax Assets/Liabilities: defined on the tax used on the invoice line
    - Revenues/Expenses: defined by default on product’s internal category; can be also set in product form (Accounting tab) as a replacement value.
    - Inventory Variations: to set as Stock Input/Output Account in product’s internal category
    - Inventory: to set as Stock Valuation Account in product’s internal category


### Vendor Invoice (PO $50, Invoice €50)

|                                  |  Debit           |  Credit         |
| -------------------------------- | ---------------- | --------------- |
| 1 Assets                         |                  |                 |
|   11000 Cash                     |                  |                 |
|   13100 Accounts Receivable      |                  |                 |
|   14000 Inventory                |                  |                 |
|   14100 Raw Materials Inventory  |                  |                 |
|   19000 Deferred Tax Assets      |  $          4.50 |                 |
| 2 Liabilities                    |                  |                 |
|   21000 Accounts Payable         |                  |  $        54.50 |
|   26200 Deferred Tax Liabilities |                  |                 |
| 3 Equity                         |                  |                 |
|   31000 Common Stock             |                  |                 |
| 4 Revenue                        |                  |                 |
|   41000 Goods                    |                  |                 |
| 5 Expenses                       |                  |                 |
|   51000 Purchased Goods          |  $        50.00  |                 |
|   52000 Purchased Services       |                  |                 |
|   58000 Inventory Variations     |                  |                 |
|   59000 Other Operating Expenses |                  |                 |


### Vendor Goods Reception (PO $50, Invoice $50)

|                                  |  Debit          |  Credit         |
| -------------------------------- | --------------- | --------------- |
| 1 Assets                         |                 |                 |
|   11000 Cash                     |                 |                 |
|   13100 Accounts Receivable      |                 |                 |
|   14000 Inventory                |  $        50.00 |                 |
|   14100 Raw Materials Inventory  |                 |                 |
|   19000 Deferred Tax Assets      |                 |                 |
| 2 Liabilities                    |                 |                 |
|   21000 Accounts Payable         |                 |                 |
|   26200 Deferred Tax Liabilities |                 |                 |
| 3 Equity                         |                 |                 |
|   31000 Common Stock             |                 |                 |
| 4 Revenue                        |                 |                 |
|   41000 Goods                    |                 |                 |
| 5 Expenses                       |                 |                 |
|   51000 Purchased Goods          |                 |                 |
|   52000 Purchased Services       |                 |                 |
|   58000 Inventory Variations     |                 |  $        50.00 |
|   59000 Other Operating Expenses |                 |                 |


### Vendor Invoice (PO $48, Invoice $50)
|                                  |  Debit           |  Credit         |
| -------------------------------- | ---------------- | --------------- |
| 1 Assets                         |                  |                 |
|   11000 Cash                     |                  |                 |
|   13100 Accounts Receivable      |                  |                 |
|   14000 Inventory                |                  |                 |
|   14100 Raw Materials Inventory  |                  |                 |
|   19000 Deferred Tax Assets      |  $          4.50 |                 |
| 2 Liabilities                    |                  |                 |
|   21000 Accounts Payable         |                  |  $        54.50 |
|   26200 Deferred Tax Liabilities |                  |                 |
| 3 Equity                         |                  |                 |
|   31000 Common Stock             |                  |                 |
| 4 Revenue                        |                  |                 |
|   41000 Goods                    |                  |                 |
| 5 Expenses                       |                  |                 |
|   51000 Purchased Goods          |  $        50.00  |                 |
|   52000 Purchased Services       |                  |                 |
|   58000 Inventory Variations     |                  |                 |
|   59000 Other Operating Expenses |                  |                 |


### Vendor Goods Reception (PO $48, Invoice $50)
|                                  |  Debit          |  Credit         |
| -------------------------------- | --------------- | --------------- |
| 1 Assets                         |                 |                 |
|   11000 Cash                     |                 |                 |
|   13100 Accounts Receivable      |                 |                 |
|   14000 Inventory                |  $        48.00 |                 |
|   14100 Raw Materials Inventory  |                 |                 |
|   19000 Deferred Tax Assets      |                 |                 |
| 2 Liabilities                    |                 |                 |
|   21000 Accounts Payable         |                 |                 |
|   26200 Deferred Tax Liabilities |                 |                 |
| 3 Equity                         |                 |                 |
|   31000 Common Stock             |                 |                 |
| 4 Revenue                        |                 |                 |
|   41000 Goods                    |                 |                 |
| 5 Expenses                       |                 |                 |
|   51000 Purchased Goods          |                 |                 |
|   52000 Purchased Services       |                 |                 |
|   58000 Inventory Variations     |                 |  $        48.00 |
|   59000 Other Operating Expenses |                 |                 |


### Customer Invoice ($100 + 9% tax)
|                                  |  Debit         |  Credit          |
| -------------------------------- | -------------- | ---------------- |
| 1 Assets                         |                |                  |
|   11000 Cash                     |                |                  |
|   13100 Accounts Receivable      |  $      109.00 |                  |
|   14000 Inventory                |                |                  |
|   14100 Raw Materials Inventory  |                |                  |
|   19000 Deferred Tax Assets      |                |                  |
| 2 Liabilities                    |                |                  |
|   21000 Accounts Payable         |                |                  |
|   26200 Deferred Tax Liabilities |                |  $          9.00 |
| 3 Equity                         |                |                  |
|   31000 Common Stock             |                |                  |
| 4 Revenue                        |                |                  |
|   41000 Goods                    |                |  $      100.00   |
| 5 Expenses                       |                |                  |
|   51000 Purchased Goods          |                |                  |
|   52000 Purchased Services       |                |                  |
|   58000 Inventory Variations     |                |                  |
|   59000 Other Operating Expenses |                |                  |


### Customer Shipping
|                                  |  Debit          |  Credit         |
| -------------------------------- | --------------- | --------------- |
| 1 Assets                         |                 |                 |
|   11000 Cash                     |                 |                 |
|   13100 Accounts Receivable      |                 |                 |
|   14000 Inventory                |                 |  $        50.00 |
|   14100 Raw Materials Inventory  |                 |                 |
|   19000 Deferred Tax Assets      |                 |                 |
| 2 Liabilities                    |                 |                 |
|   21000 Accounts Payable         |                 |                 |
|   26200 Deferred Tax Liabilities |                 |                 |
| 3 Equity                         |                 |                 |
|   31000 Common Stock             |                 |                 |
| 4 Revenue                        |                 |                 |
|   41000 Goods                    |                 |                 |
| 5 Expenses                       |                 |                 |
|   51000 Purchased Goods          |                 |                 |
|   52000 Purchased Services       |                 |                 |
|   58000 Inventory Variations     |  $        50.00 |                 |
|   59000 Other Operating Expenses |                 |                 |

## Anglo-Saxon Accounting

!!!note
    **Configuration:**

    - Accounts Receivable/Payable: defined on the partner (Accounting tab)
    - Deferred Tax Assets/Liabilities: defined on the tax used on the invoice line
    - Revenues: defined on the product category as a default, or specifically to a specific product.
    - Expenses: this is where you should set the “Cost of Goods Sold” account. Defined on the product category as a default value, or specifically on the product form.
    - Goods Received Not Purchased: to set as Stock Input Account in product’s internal category
    - Goods Issued Not Invoiced: to set as Stock Output Account in product’s internal category
    - Inventory: to set as Stock Valuation Account in product’s internal category
    - Price Difference: to set in product’s internal category or in product form as a specific replacement value

### Vendor Bill (PO $50, Invoice €50)

|                                      |  Debit          |  Credit         |
| ------------------------------------ | --------------- | --------------- |
| 1 Assets                             |                 |                 |
|   11000 Cash                         |                 |                 |
|   13100 Accounts Receivable          |                 |                 |
|   14000 Inventory                    |                 |                 |
|   14100 Raw Materials Inventory      |                 |                 |
|   14600 Good Issued (Stock Output)   |                 |                 |
|   19000 Deferred Tax Assets          |     4.50        |                 |
| 2 Liabilities                        |                 |                 |
|   21000 Accounts Payable             |                 |    54.50        |
|   23000 Stock Received (Stock Input) |    50.00        |                 |
|   26200 Deferred Tax Liabilities     |                 |                 |
| 3 Equity                             |                 |                 |
|   31000 Common Stock                 |                 |                 |
| 4 Revenue                            |                 |                 |
|   41000 Goods                        |                 |                 |
| 5 Expenses                           |                 |                 |
|   51000 Cost of Good Sold            |                 |                 |
|   52000 Manufacturing Overhead       |                 |                 |
|   53000 Price Difference             |                 |                 |



### Vendor Goods Reception (PO $50, Invoice $50)

|                                      |  Debit          |  Credit         |
| ------------------------------------ | --------------- | --------------- |
| 1 Assets                             |                 |                 |
|   11000 Cash                         |                 |                 |
|   13100 Accounts Receivable          |                 |                 |
|   14000 Inventory                    |       50        |                 |
|   14100 Raw Materials Inventory      |                 |                 |
|   14600 Good Issued (Stock Output)   |                 |                 |
|   19000 Deferred Tax Assets          |                 |                 |
| 2 Liabilities                        |                 |                 |
|   21000 Accounts Payable             |                 |                 |
|   23000 Stock Received (Stock Input) |                 |      50         |
|   26200 Deferred Tax Liabilities     |                 |                 |
| 3 Equity                             |                 |                 |
|   31000 Common Stock                 |                 |                 |
| 4 Revenue                            |                 |                 |
|   41000 Goods                        |                 |                 |
| 5 Expenses                           |                 |                 |
|   51000 Cost of Good Sold            |                 |                 |
|   52000 Manufacturing Overhead       |                 |                 |
|   53000 Price Difference             |                 |                 |


### Vendor Bill (PO $48, Invoice $50)

|                                      |  Debit          |  Credit         |
| ------------------------------------ | --------------- | --------------- |
| 1 Assets                             |                 |                 |
|   11000 Cash                         |                 |                 |
|   13100 Accounts Receivable          |                 |                 |
|   14000 Inventory                    |                 |                 |
|   14100 Raw Materials Inventory      |                 |                 |
|   14600 Good Issued (Stock Output)   |                 |                 |
|   19000 Deferred Tax Assets          |     4.50        |                 |
| 2 Liabilities                        |                 |                 |
|   21000 Accounts Payable             |                 |    54.50        |
|   23000 Stock Received (Stock Input) |    48.00        |                 |
|   26200 Deferred Tax Liabilities     |                 |                 |
| 3 Equity                             |                 |                 |
|   31000 Common Stock                 |                 |                 |
| 4 Revenue                            |                 |                 |
|   41000 Goods                        |                 |                 |
| 5 Expenses                           |                 |                 |
|   51000 Cost of Good Sold            |                 |                 |
|   52000 Manufacturing Overhead       |                 |                 |
|   53000 Price Difference             |     2.00        |                 |


### Vendor Goods Reception (PO $48, Invoice $50)
|                                      |  Debit          |  Credit         |
| ------------------------------------ | --------------- | --------------- |
| 1 Assets                             |                 |                 |
|   11000 Cash                         |                 |                 |
|   13100 Accounts Receivable          |                 |                 |
|   14000 Inventory                    |  $        48.00 |                 |
|   14100 Raw Materials Inventory      |                 |                 |
|   14600 Good Issued (Stock Output)   |                 |                 |
|   19000 Deferred Tax Assets          |                 |                 |
| 2 Liabilities                        |                 |                 |
|   21000 Accounts Payable             |                 |                 |
|   23000 Stock Received (Stock Input) |                 |  $        48.00 |
|   26200 Deferred Tax Liabilities     |                 |                 |
| 3 Equity                             |                 |                 |
|   31000 Common Stock                 |                 |                 |
| 4 Revenue                            |                 |                 |
|   41000 Goods                        |                 |                 |
| 5 Expenses                           |                 |                 |
|   51000 Cost of Good Sold            |                 |                 |
|   52000 Manufacturing Overhead       |                 |                 |
|   53000 Price Difference             |                 |                 |


### Customer Invoice ($100 + 9% tax)
|                                      |  Debit          |  Credit          |
| ------------------------------------ | --------------- | ---------------- |
| 1 Assets                             |                 |                  |
|   11000 Cash                         |                 |                  |
|   13100 Accounts Receivable          |  $      109.00  |                  |
|   14000 Inventory                    |                 |                  |
|   14100 Raw Materials Inventory      |                 |                  |
|   14600 Good Issued (Stock Output)   |                 |  $        50.00  |
|   19000 Deferred Tax Assets          |                 |                  |
| 2 Liabilities                        |                 |                  |
|   21000 Accounts Payable             |                 |                  |
|   23000 Stock Received (Stock Input) |                 |                  |
|   26200 Deferred Tax Liabilities     |                 |  $          9.00 |
| 3 Equity                             |                 |                  |
|   31000 Common Stock                 |                 |                  |
| 4 Revenue                            |                 |                  |
|   41000 Goods                        |                 |  $      100.00   |
| 5 Expenses                           |                 |                  |
|   51000 Cost of Good Sold            |  $        50.00 |                  |
|   52000 Manufacturing Overhead       |                 |                  |
|   53000 Price Difference             |                 |                  |


### Customer Shipping
|                                      |  Debit          |  Credit         |
| ------------------------------------ | --------------- | --------------- |
| 1 Assets                             |                 |                 |
|   11000 Cash                         |                 |                 |
|   13100 Accounts Receivable          |                 |         |
|   14000 Inventory                    |                 | $        50.00             |
|   14100 Raw Materials Inventory      |                 |                 |
|   14600 Good Issued (Stock Output)   |  $        50.00 |                 |
|   19000 Deferred Tax Assets          |                 |                 |
| 2 Liabilities                        |                 |                 |
|   21000 Accounts Payable             |                 |                 |
|   23000 Stock Received (Stock Input) |                 |                 |
|   26200 Deferred Tax Liabilities     |                 |                 |
| 3 Equity                             |                 |                 |
|   31000 Common Stock                 |                 |                 |
| 4 Revenue                            |                 |                 |
|   41000 Goods                        |                 |                 |
| 5 Expenses                           |                 |                 |
|   51000 Cost of Good Sold            |                 |                 |
|   52000 Manufacturing Overhead       |                 |                 |
|   53000 Price Difference             |                 |                 |

### Production Order
|                                      |  Debit           |  Credit         |
| ------------------------------------ | ---------------- | --------------- |
| 1 Assets                             |                  |                 |
|   11000 Cash                         |                  |                 |
|   13100 Accounts Receivable          |                  |                 |
|   14000 Inventory                    |  $        50.00  |                 |
|   14100 Raw Materials Inventory      |                  |  $        52.00 |
|   14600 Good Issued (Stock Output)   |                  |                 |
|   19000 Deferred Tax Assets          |                  |                 |
| 2 Liabilities                        |                  |                 |
|   21000 Accounts Payable             |                  |                 |
|   23000 Stock Received (Stock Input) |                  |                 |
|   26200 Deferred Tax Liabilities     |                  |                 |
| 3 Equity                             |                  |                 |
|   31000 Common Stock                 |                  |                 |
| 4 Revenue                            |                  |                 |
|   41000 Goods                        |                  |                 |
| 5 Expenses                           |                  |                 |
|   51000 Cost of Good Sold            |                  |                 |
|   52000 Manufacturing Overhead       |                  |                 |
|   53000 Price Difference             |  $          2.00 |                 |