## Managing Users

### Create New User

PerfectWORK defines a **user** as someone who has access to a database to perform daily tasks. You can add as many users as you need and, in order to restrict the type of information each user can access, rules can be applied. Users and access rights can be added and changed at any point.

### Add individual users

Go to **<span class="menuselection">Settings ‣ Manage Users</span>** and click on *Create*.

[![by default 2021-10-05 at 2.07.24 PM.png](https://gethelp.perfectwork.app/uploads/images/gallery/2021-10/scaled-1680-/wPlFf3TB39hc6Wd5-by-default-2021-10-05-at-2-07-24-pm.png)](https://gethelp.perfectwork.app/uploads/images/gallery/2021-10/wPlFf3TB39hc6Wd5-by-default-2021-10-05-at-2-07-24-pm.png)

Fill in the form with the needed information. Under the tab [<span class="doc">Access Rights</span>](https://www.odoo.com/documentation/14.0/applications/general/users/access_rights.html) choose the group within each application the user can have access to.<div id="bkmrk--0"><div id="bkmrk--1"><div id="bkmrk-the-list-of-applicat">The list of applications shown is based on the applications installed on the database.<div id="bkmrk--2">![View of a user’s form emphasizing the access rights tab in Odoo](https://www.odoo.com/documentation/14.0/_images/new_user.png)

When you are done editing the page and have *Saved* it, an invitation email is automatically sent to the user. The user must click on it to accept the invitation and create a login.

![View of a user’s form with a notification that the invitation email has been sent in Odoo](https://www.odoo.com/documentation/14.0/_images/invitation-email.png)

<p class="callout info">Remember that subscription prices follow the number of users.</p>

With the [<span class="std std-ref">developer mode</span>](https://www.odoo.com/documentation/14.0/applications/general/developer_mode.html#developer-mode) activated, *User Types* can be selected.

[![View of a user’s form in developer mode emphasizing the user type field in Odoo](https://www.odoo.com/documentation/14.0/_images/user-type.png)](https://www.odoo.com/documentation/14.0/_images/user-type.png)

The *Portal* and *Public* options do not allow you to choose access rights. Members have specific ones (such as record rules and restricted menus) and usually do not belong to the usual PerfectWORK groups.

### Deactivate users

Go to **<span class="menuselection">Settings ‣ Users &amp; Companies ‣ Users</span>**, open the user you want to deactivate, click on *Action*, and then on *Archive*.

<p class="callout danger">**Never** deactivate the main user (*admin*).</p>

### Passwords Management

#### <span id="bkmrk--8"></span>Reset passwords

###### <span id="bkmrk--9"></span>Enable password resets from login page

It is possible to enable password resets directly from the login page.

To do so, go to **<span class="menuselection">Settings ‣ Permissions</span>**, activate **Password Reset** and *Save*.

![Enabling Password Reset in Odoo Settings](https://www.odoo.com/documentation/14.0/_images/password-reset-login.png)



### Send reset instructions to users

Go to **<span class="menuselection">Settings ‣ Users &amp; Companies ‣ Users</span>**, select the user out of the list and click on *Send Password Reset Instructions* on its user form. An email is automatically sent to them.

<p class="callout info">The *Send Password Reset Instructions* button only appears if the Odoo invitation email has already been confirmed by the user.</p>

This email contains all the instructions needed to reset the password, along with a link redirecting the user to an Odoo login page.

![Example of an email with a password reset link for an Odoo account](https://www.odoo.com/documentation/14.0/_images/password-email.png)

#### Change users’ passwords

Go to **<span class="menuselection">Settings ‣ Users &amp; Companies ‣ Users</span>** and select a user to access its form. Click on the *Action* button and select *Change Password*.

![Change another user's password on Odoo](https://www.odoo.com/documentation/14.0/_images/change-password.png)Enter a new password and confirm by clicking on *Change Password*.

<p class="callout info">This operation only modifies the password of the users locally and does not affect their odoo.com account. If you want to change the odoo.com password, you can [<span class="std std-ref">send the password reset instructions</span>](https://www.odoo.com/documentation/14.0/applications/general/users/manage_users.html#users-reset-password-email).</p>

Click on *Change Password* one more time. You are then redirected to an Odoo login page where you can reaccess your database using your new password.



## Access Right

Activate the [<span class="std std-ref">developer mode</span>](https://www.odoo.com/documentation/14.0/applications/general/developer_mode.html#developer-mode), then go to **<span class="menuselection">Settings ‣ Users &amp; Companies ‣ Groups</span>.**

### Groups

<div><div>When choosing the groups the user can have access under [<span class="std std-ref">Access Rights</span>](https://www.odoo.com/documentation/14.0/applications/general/users/manage_users.html#users-add-individual), details of the rules and inheritances of that group are not shown, so this is when the menu *Groups* comes along. *Groups* are created to define rules to models within an application.</div><div></div><div>Under *Users*, have a list of the current ones. The ones with administrative rights are shown in black.</div><div></div></div>![View of a group’s form emphasizing the tab users in Odoo](https://www.odoo.com/documentation/14.0/_images/groups-users.png)*Inherited* means that users added to this application group are automatically added to the following ones. In the example below, users who have access to the group *Administrator* of *Sales* also have access to *Website/Restricted Editor* and *Sales/User: All Documents*.

[![View of a group’s form emphasizing the tab inherited in Odoo](https://www.odoo.com/documentation/14.0/_images/groups-inherited.png)](https://www.odoo.com/documentation/14.0/_images/groups-inherited.png)<p class="callout warning">Remember to always test the settings being changed in order to ensure that they are being applied to the needed and right users.</p>

The *Menus* tab is where you define which menus (models) the user can have access to.

[![View of a group’s form emphasizing the tab menus in Odoo](https://www.odoo.com/documentation/14.0/_images/groups-menus.png)](https://www.odoo.com/documentation/14.0/_images/groups-menus.png)*Access Rights* rules are the first level of rights. The field is composed of the object name, which is the technical name given to a model. For each model, enable the following options as appropriate:

- *Read*: the values of that object can be only seen by the user.
- *Write*: the values of that object can be edited by the user.
- *Create*: values for that object can be created by the user.
- *Delete*: the values of that object can be deleted by the user.

![View of a group’s form emphasizing the tab access rights in Odoo](https://www.odoo.com/documentation/14.0/_images/groups-access-rights.png)<div><div></div><div>As a second layer of editing and visibility rules, *Record Rules* can be formed. They overwrite, or refine, the *Access Rights*.</div><div>A record rule is written using a *Domain*. Domains are conditions used to filter or searching data. Therefore, a domain expression is a list of conditions. For each rule, choose among the following options: *Read*, *Write*, *Create* and *Delete* values.</div><div></div></div>![View of a group’s form emphasizing the tab record rules in Odoo](https://www.odoo.com/documentation/14.0/_images/groups-record-rules.png)<p class="callout warning">Making changes in access rights can have a big impact on the database. For this reason, we recommend you to contact your PerfectWORK Business Analyst or our Partners, unless you have knowledge about Domains in PerfectWORK.</p>



## Managing Companies

### Companies

A centralized management environment allows you to select multiple companies simultaneously and set their specific warehouses, customers, equipment, and contacts. It provides you the ability to generate reports of aggregated figures without switching interfaces, which facilitates daily tasks and the overall management process.

### Manage companies and records

Go to **<span class="menuselection">Settings ‣ Manage Companies</span>** and fill in the form with your company’s information. If a *Parent Company* is selected, records are shared between the two companies (as long as both environments are active).

![Overview of a new company's form in Odoo](https://www.odoo.com/documentation/14.0/_images/create_js_store_us.png) Tip

Activate the [<span class="std std-ref">developer mode</span>](https://www.odoo.com/documentation/14.0/applications/general/developer_mode.html#developer-mode) to choose a *Favicon* for each of your companies, and easily identify them by the browser tabs. Set your favicons’ files size to 16x16 or 32x32 pixels. JPG, PNG, GIF, and ICO are extensions accepted.

<div></div>Switch between or select multiple companies by enabling their selection boxes to activate them. The grayed company is the one which environment is in use. To switch environments, click on the company’s name. In the example below, the user has access to three companies, two are activated, and the environment in use is of *JS Store US*.

![View of the companies menu through the main dashboard in Odoo](https://www.odoo.com/documentation/14.0/_images/multi_companies_menu_dashboard.png)Data such as Products, Contacts, and Equipment can be shared or set to be shown for a specific company only. To do so, on their forms, choose between:

- *A blank field*: the record is shared within all companies.
- *Adding a company*: the record is visible to users logged in to that specific company.

![View of a product's form emphasizing the company field in Odoo Sales](https://www.odoo.com/documentation/14.0/_images/product_form_company.png)</section><section id="bkmrk-employees%E2%80%99-access-on">## Employees’ access

Once companies are created, manage your employees’ [<span class="doc">Access Rights</span>](https://www.odoo.com/documentation/14.0/applications/general/users/access_rights.html) for *Multi Companies*.

![View of an user form emphasizing the multi companies field under the access rights tabs in Odoo](https://www.odoo.com/documentation/14.0/_images/access_rights_multi_companies.png)<div><div></div><div>If a user has multiple companies *activated* on his database, and he is **editing** a record, the editing happens on the record’s related company.</div><div></div><div>Example: if editing a sale order issued under JS Store US while working on the JS Store Belgium environment, the changes are applied under JS Store US (the company from which the sale order was issued).</div><div>When **creating** a record, the company taken into account is:</div></div>- The current company (the one active) or,
- No company is set (on products and contacts’ forms for example) or,
- The company set is the one linked to the document (the same as if a record is being edited).

### Documents’ format

To set documents’ formats according to each company, *activate* and *select* the respective one and, under *Settings*, click on *Configure Document Layout*.

![View of the settings page emphasizing the document layout field in Odoo](https://www.odoo.com/documentation/14.0/_images/document_layout.png)

### Inter-Company Transactions

First, make sure each one of your companies is properly set in relation to:

- [<span class="doc">Chart of Accounts</span>](https://www.odoo.com/documentation/14.0/applications/finance/accounting/getting_started/initial_configuration/chart_of_accounts.html)
- [<span class="doc">Taxes</span>](https://www.odoo.com/documentation/14.0/applications/finance/accounting/taxation/taxes/default_taxes.html)
- [<span class="doc">Fiscal Positions</span>](https://www.odoo.com/documentation/14.0/applications/finance/accounting/taxation/taxes/fiscal_positions.html)
- [<span class="doc">Journals</span>](https://www.odoo.com/documentation/14.0/applications/finance/accounting/bank/setup/bank_accounts.html)
- [<span class="doc">Fiscal Localizations</span>](https://www.odoo.com/documentation/14.0/applications/finance/accounting/fiscal_localizations/overview/fiscal_localization_packages.html)
- [<span class="doc">Pricelists</span>](https://www.odoo.com/documentation/14.0/applications/sales/sales/products_prices/prices/pricing.html)
