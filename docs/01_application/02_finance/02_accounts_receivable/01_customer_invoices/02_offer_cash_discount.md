---
title: Offer Cash Discounts
summary: Offer cash discounts
authors: Wilson Loh
date: 2022-01-18
---
Cash discounts are incentives you can offer to customers to motivate them to pay within a specific time frame. For instance, you offer a 2% discount if the customer pays you within the first 5 days of the invoice, when it is due in 30 days. This approach can greatly improve your average collection period.

## Set up a cash discount
To set up a cash discount, go to **Accounting ‣ Configuration ‣ Management ‣ Payment Terms** and click on *Create*. Add a Percent type of term with a corresponding value (e.g. 98% of the total price for a 2% discount) and the number of days during which the offer is valid. You can also change the default balance term if needed.

![](2022-01-18-17-53-48.png)

## Start offering the cash discount
Now, you can create a customer invoice and select the cash discount payment term you added. Once the invoice is validated, PerfectWORK will automatically split the account receivables part of the journal entry into two installments having different due dates. Since the discounted price is already calculated, your payment controls will be simplified.

![](2022-01-18-17-54-11.png)

## Grant the cash discount
The customer fulfilled the payment terms and therefore benefits from the cash discount. When you process the bank statement, match the payment with the related journal entry. Then, select the remaining cash discount and click on Create Write-off to reconcile it.

![](2022-01-18-17-54-33.png)

!!! tip "Tip"
    1. You can also create a dedicated reconciliation model to make the process easier. In this case, you should add a tax to the model based on the taxes applied to your invoices. This means that if you handle multiple tax rates, you need to create several reconciliation models. Note that depending on your localisation, you might already have a Cash Discount model available by default.

## Register the full payment
In this case, the customer has not fulfilled the payment term and cannot benefit from the cash discount. When you process the bank statement, match the payment with the two related journal entries.

![](2022-01-18-17-56-31.png)
