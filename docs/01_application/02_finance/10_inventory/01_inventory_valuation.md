---
title: Inventory Valuation Configuration
summary: Inventory Valuation Configuration
authors: Wilson Loh
date: 2022-04-20
---

Inventory valuation refers to how you value your stock. It’s a very important aspect of a business as the inventory can be the biggest asset of a company. Inventory valuation implies two main choices:
    - The cost method you use to value your goods (standard, fifo, avco)
    - The way you record this value into your accounting books (manually or automatically)

Those two concepts are explained in the sections below.

## Costing Methods: Standard, FIFO, AVCO
The costing method is defined in the product category. There are three options available. Each of them is explained in detail below.

### Standard Price

| Operation                 |  Unit Cost            | Qty On Hand | Delta Value  |  Inventory Value       |
| ------------------------- | --------------------- | ----------- | -----------  | ---------------------- |
|                           |  $              10.00 | 0           |              |  $                   - |
| Receive 8 Products at $10 |  $              10.00 | 8           | +8 \* 10     |  $              80.00  |
| Receive 4 Products at $16 |  $              10.00 | 12          | +4 \* 10     |  $            120.00   |
| Deliver 10 Products       |  $              10.00 | 2           | -10 \* 10    |  $              20.00  |
| Receive 2 Products at $9  |  $              10.00 | 4           | +2 \* 10     |  $              20.00  |
    
In **Standard Price**, any product will be valued at the cost that you __defined manually__ on the product form. Usually, this cost is an estimation based on the material and labor needed to obtain the product. This cost must be reviewed periodically.

### Average Cost (AVCO)

| Operation                 |  Unit Cost            | Qty On Hand | Delta Value  |  Inventory Value       |
| ------------------------- | --------------------- | ----------- | -----------  | ---------------------- |
|                           |  $               0.00 | 0           |              |  $               0.00  |
| Receive 8 Products at $10 |  $              10.00 | 8           | +8 \* 10     |  $              80.00  |
| Receive 4 Products at $16 |  $              12.00 | 12          | +4 \* 16     |  $             144.00  |
| Deliver 10 Products       |  $              12.00 | 2           | -10 \* 12    |  $              24.00  |
| Receive 2 Products at $9  |  $               9.00 | 4           | +2 \* 6      |  $              36.00  |
    
In **AVCO (Average Cost)**, each product has the same value and this value is the average purchase cost of the product. With this costing method, the cost of the product is recomputed as each receipt.
<br/><br/>
The average cost does not change when products leave the warehouse.
<br/><br/>

### FIFO (First In First Out)

| Operation                 |  Unit Cost            | Qty On Hand | Delta Value  |  Inventory Value       |
| ------------------------- | --------------------- | ----------- | -----------  | ---------------------- |
|                           |  $               0.00 | 0           |              |  $               0.00  |
| Receive 8 Products at $10 |  $              10.00 | 8           | +8 \* 10     |  $              80.00  |
| Receive 4 Products at $16 |  $              12.00 | 12          | +4 \* 16     |  $             144.00  |
| Deliver 10 Products       |  $              16.00 | 2           | -10 \* 12 <br /> -2 \* 16   |  $              32.00  |
| Receive 2 Products at $9  |  $              11.00 | 4           | +2 \* 6      |  $              44.00  |
    
In FIFO (First In First Out), the products are valued at their purchase cost. When a product leaves the stock, that’s the “First in, first out” rule that applies.
<br /><br />
Pay attention, that this is a __financial FIFO__. The first value “in” is the first value “out”, no matter the storage location, warehouse or serial number.
<br /><br />
FIFO is advised if you manage all your workflows into PerfectWORK (Sales, Purchases, Inventory). It suits any kind of users.

## Inventory Valuation: Automated or Manual
There are two ways to record your inventory valuation in your accounting books. As the costing method, this is defined in your product category. Those two methods are detailed below.It is important to also note that the accounting entries will depend on your accounting mode: it can be **continental** or **anglo-saxon**. 
<br /><br />
In continental accounting, the cost of a good is taken into account as soon as the product is received in stock. 
<br /><br />
In anglo-saxon accounting, the cost of a good is only recorded as an expense when this good is invoiced to a final customer. In the tables below, you can easily compare those two accounting modes.Usually, based on your country, the correct accounting mode will be chosen by default.

