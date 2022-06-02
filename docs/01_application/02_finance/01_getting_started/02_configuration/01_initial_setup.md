---
title: Initial Setup of PerfectWORK Accounting
summary: Initial Setup of PerfectWORK Accounting
authors: Wilson Loh
date: 2022-01-18
---
When you first open your PerfectWORK Accounting app, the Accounting Overview page welcomes you with a step-by-step onboarding banner, a wizard that helps you get started. This onboarding banner is displayed until you choose to close it.

The settings visible in the onboarding banner can still be modified later by going to **Accounting ‣ Configuration ‣ Settings8**.


???+ note "Note"

    - PerfectWORK Accounting automatically installs the appropriate Fiscal Localization Package for your company, according to the country selected at the creation of the database. This way, the right accounts, reports, and taxes are ready-to-go. Click here for more information about Fiscal Localization Packages.

## Accounting onboarding banner
The step-by-step Accounting onboarding banner is composed of four steps:

![](2022-01-18-15-37-09.png)


1. **1. Company Data**
2. **2. Bank Account**
3. **3. Accounting Periods**
4. **4. Chart of Accounts**

### Company Data
This menu allows you to add your company’s details such as the name, address, logo, website, phone number, email address, and Tax ID, or VAT number. These details are then displayed on your documents, such as on invoices.

![](2022-01-18-15-40-54.png)

???+ note "Note"
    - You can also change these settings by going to Settings ‣ General Settings ‣ Settings ‣ Companies and clicking on Update Info.

### Bank Account
Connect your bank account to your database and have your bank statements synced automatically. To do so, find your bank in the list, click on Connect, and follow the instructions on-screen.

If your Bank Institution can’t be synchronized automatically, or if you prefer not to sync it with your database, you may also configure your bank account manually by clicking on Create it, and filling out the form.

- **Name**: the bank account’s name, as displayed on PerfectWORK.
- **Account Number**: your bank account number (IBAN in Europe).
- **Bank**: click on *Create* and *Edit* to configure the bank’s details. Add the bank institution’s name and its Identifier Code (BIC or SWIFT).
- **Code**: this code is your Journal’s *Short* Code, as displayed on PerfectWORK. By default, PerfectWORK creates a new Journal with this Short Code.
- **Journal**: This field is displayed if you have an existing Bank Journal that is not linked yet to a bank account. If so, then select the *Journal* you want to use to record the financial transactions linked to this bank account or create a new one by clicking on *Create and Edit*.

!!! note "Note"

    - You can add as many bank accounts as needed with this tool by going to **Accounting ‣ Configuration**, and clicking on *Add a Bank Account*.
    - Click here for more information about Bank Accounts.

### Accounting Periods
Define here your **Fiscal Years**’ opening and closing dates, which are used to generate reports automatically, and your **Tax Return Periodicity**, along with a reminder to never miss a tax return deadline.

By default, the opening date is set on the 1st of January and the closing date on the 31st of December, as this is the most common use.

!!! note "Note"
    - You can also change these settings by going to **Accounting ‣ Configuration ‣ Settings ‣ Fiscal Periods** and updating the values.

### Chart of Accounts
With this menu, you can add accounts to your **Chart of Accounts** and indicate their initial opening balances.

Basic settings are displayed on this page to help you review your Chart of Accounts. To access all the settings of an account, click on the *double arrow button* at the end of the line.

![](2022-01-18-15-48-02.png)


!!! note "Note"
    - Click here for more information on how to configure your Chart of Accounts.

## Invoicing onboarding banner

There is another step-by-step onboarding banner that helps you take advantage of your PerfectWORK Invoicing and Accounting apps. The Invoicing onboarding banner is the one that welcomes you if you use the Invoicing app rather than the Accounting app.

If you have PerfectWORK Accounting installed on your database, you can reach it by going to **Accounting ‣ Customers ‣ Invoices**.

<br />
The Invoicing onboarding banner is composed of four main steps:
<br />

![](2022-01-18-15-49-29.png)

1. **1. Company Data**
2. **2. Invoice Layout**
3. **3. Payment Method**
4. **4. Sample Invoice**

### Company Data
This form is the same as **the one presented in the Accounting onboarding banner**.

### Invoice Layout
With this tool, you can design the appearance of your documents by selecting which layout template, paper format, colors, font, and logo you want to use.

You can also add your Company Tagline and the content of the documents’ footer. Note that PerfectWORK automatically adds the company’s phone number, email, website URL, and Tax ID (or VAT number) to the footer, according to the values you previously configured in the **Company Data**.

![](2022-01-18-15-50-44.png)


!!! tip "Tip"
    - Add your bank account number and a link to your General Terms & Condition in the footer. This way, your contacts can find the full content of your GT&C online without having to print them on the invoices you issue.

!!! note "Note"
    - These settings can also be modified by going to Settings ‣ General Settings, under the Business Documents section.

### Payment Method
This menu helps you configure the payment methods with which your customers can pay you.

!!! danger "Important"
    Configuring a Payment Acquirer with this tool also activates the Invoice Online Payment option automatically. With this, users can directly pay online, from their Customer Portal.

### Sample Invoice
Send yourself a sample invoice by email to make sure everything is correctly configured.