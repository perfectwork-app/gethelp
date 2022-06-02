---
title: Email Communication
summary: Email Communication
authors:
    - Wilson Loh
date: 2022-03-18
---
## Send and Receive Emails in PerfectWORK with an Email Server

### If you are a user of PerfectWORK Online

You have nothing to do! PerfectWORK sets up its own mail servers for your database. Outgoing and incoming emails work out-of-the-box!
<br><br>
Unless you plan to send large batches of mass mailing that could require the use of an external mail server, simply enjoy your new PerfectWORK database.

### Scope of this documentation
This document is mainly dedicated to PerfectWORK on-premise users who don’t benefit from an out-of-the-box solution to send and receive emails in PerfectWORK, unlike PerfectWORK Online.

!!!Warning

    If no one in your company is used to manage email servers, we strongly recommend that you opt for those PerfectWORK hosting solutions. Their email system works instantly and is monitored by professionals. Nevertheless you can still use your own email servers if you want to manage your email server’s reputation yourself.

You will find here some useful information on how to integrate your own email solution with PerfectWORK.

!!!Note

    Office 365 email servers don’t easily allow to send external emails from hosts like PerfectWORK. Refer to Microsoft’s documentation to make it work.


### How to manage outbound messages
As a system admin, go to **Settings ‣ General Settings** and check _External Email Servers_. Then, click _Outgoing Mail Servers_ to create one and reference the SMTP data of your email server. Once all the information has been filled out, click on _Test Connection_.
<br><br>
Here is a typical configuration for a G Suite server.


Then set your email domain name in the General Settings.

!!!Note

    If you get a [AUTHENTICATIONFAILED] Invalid credentials (Failure) warning when you Test Connection on a Gmail address, activate the Less secure app access option. A direct link can be accessed here.
    <br><br>
    In addition to that, enable the IMAP setting on your Gmail account.

#### Can I use an Office 365 server
You can use an Office 365 server if you run PerfectWORK on-premise. Office 365 SMTP relays are not compatible with PerfectWORK Online unless you configure PerfectWORK to force the outgoing “From” address .

Please refer to Microsoft’s documentation to configure a SMTP relay for your PerfectWORK’s IP address.

#### How to use a G Suite server
You can use an G Suite server for any PerfectWORK hosting type. To do so you need to setup the SMTP relay service. The configuration steps are explained in Google documentation.

#### Restriction
Please note that port 25 is blocked for security reasons on our PerfectWORK Online platform. Try using 465 or 587.

#### Use a default “From” email address
Sometimes, an email’s “From” (outgoing) address can belong to a different domain, and that can be a problem.
<br><br>
For example, if a customer with address mary@customer.example.com responds to a message, PerfectWORK will try to redistribute that same email to other subscribers in the thread. But if the domain customer.example.com forbids that kind of usage for security, the PerfectWORK’s redistributed email would get rejected by some recipients’ mail servers.
<br><br>
To avoid those kind of problems, you should make sure all emails use a “From” address from your authorized domain.
<br><br>
If your MTA supports SRS (Sender Rewriting Scheme), you can enable it to handle these situations. However, that is more complex and requires more technical knowledge that is not meant to be covered by this documentation.
<br><br>
Instead, you can also configure PerfectWORK to do something similar by itself:

-  Set your domain name in the General Settings.
-  Click on Outgoing Mail Servers
-  Create a new one.
-  Fill its From Filter.

      1. Use a domain (such as mycompany.example.com) to keep the original “From” address for mails that come from that domain.

      2. Use an address (such as outgoing@mycompany.example.com) to allow only that outgoing address.

      3. Keep it empty to use this server for any email address.

  With this configuration in place, if PerfectWORK sends an email that doesn’t match any of the from filters, it will alter the email’s “From” before sending it to the MTA.
  <br><br>
  It will use the default outgoing email address, composed like this: {mail.default.from}@{mail.catchall.domain}.

-  In developer mode, go to Settings ‣ Technical ‣ Parameters ‣ System Parameters.

-  Add these system parameters:

     1. mail.default.from: local part of default outgoing email address.

     2. mail.catchall.domain: domain part of default outgoing email address.

### How to manage inbound messages
PerfectWORK relies on generic email aliases to fetch incoming messages.

- **Reply messages** of messages sent from PerfectWORK are routed to their original discussion thread (and to the inbox of all its followers) by the catchall alias (catchall@).

- **Bounced messages** are routed to bounce@ in order to track them in PerfectWORK. This is especially used in PerfectWORK Email Marketing to opt-out invalid recipients.

- **Original messages**: Several business objects have their own alias to create new records in PerfectWORK from incoming emails:

    - Sales Channel (to create Leads or Opportunities in PerfectWORK CRM),

    - Support Channel (to create Tickets in PerfectWORK Helpdesk),

    - Projects (to create new Tasks in PerfectWORK Project),

    - Job Positions (to create Applicants in PerfectWORK Recruitment),

    - etc.

Depending on your mail server, there might be several methods to fetch emails. The easiest and most recommended method is to manage one email address per PerfectWORK alias in your mail server.
<br><br>

- Create the corresponding email addresses in your mail server (catchall@, bounce@, sales@, etc.).

- Set your domain name in the General Settings.

- If you use PerfectWORK on-premise, create an Incoming Mail Server in PerfectWORK for each alias. You can do it from the General Settings as well. Fill out the form according to your email provider’s settings. Leave the Actions to Perform on Incoming Mails blank. Once all the information has been filled out, click on _TEST & CONFIRM_.

- If you use PerfectWORK Online or PerfectWORK.sh, We do recommend to redirect incoming messages to PerfectWORK’s domain name rather than exclusively use your own email server. That way you will receive incoming messages without delay. Indeed, PerfectWORK Online is fetching incoming messages of external servers once per hour only. You should set redirections for all the email addresses to PerfectWORK’s domain name in your email server (e.g. catchall@mydomain.ext to catchall@mycompany.PerfectWORK.com).

!!!Tip

    **All the aliases are customizable in PerfectWORK**.
    <br><br>
    Object aliases can be edited from their respective configuration view. To edit catchall and bounce aliases, you first need to activate the developer mode.
    <br><br>
    Then go to **Settings ‣ Technical ‣ Parameters ‣ System Parameters** to customize the aliases (mail.catchall.alias & * mail.bounce.alias*).

!!!Note
    
    By default inbound messages are fetched every 5 minutes in PerfectWORK on-premise. You can change this value in developer mode. Go to **Settings ‣ Technical ‣ Automation ‣ Scheduled Actions** and look for _Mail: Fetchmail Service_.


### Set up different dedicated servers for transactional and mass mails
PerfectWORK is subject to a **daily email limit** to prevent abuse. However, if needed, you can use a separate Mail Transfer Agent (MTA) servers for transactional e-mails and mass mailings. Example: use PerfectWORK’s own mail server for transactional e-mails, and Sendgrid, Amazon SES, or Mailgun for mass mailings. Another alternative is to use Postmark for transactional e-mails, and Amazon SES or Sendgrid for mass mailings.

!!!Note
    A default outgoing email server is already configured. You should not create an alternative one unless you want to use a specific external outgoing email server for technical reasons.

To do this, you should first activate the developer mode and then go to **Settings ‣ Technical ‣ Outgoing** e-mail servers. There you have to create two e-mail MTA server settings. One for transactional e-mails and one for mass mail servers. Be sure to mark the priority of transactional e-mail servers as low as the mass email servers.

Now, go to **Email Marketing ‣ Settings** and enable Dedicated Server. With these settings, PerfectWORK uses the server with the lower priority for transactional emails, and the server here selected for mass mails. Note that in this case, you have to set your domain’s Sender Policy Framework (SPF) records to include both transactional and mass mail servers. If your server resides with xxxx.PerfectWORK.com, the available options are Sendinblue and Mailchimp, as your e-mails would be originated from the xxxx.PerfectWORK.app domain.


## Sending emails with PerfectWORK
### Using your email domain in PerfectWORK
Documents in PerfectWORK (a CRM opportunity, a sales order, an invoice …) have a discussion thread, called chatter.
<br><br>
When you post a message in the chatter, this message is sent by email to the followers of the document. If a follower replies to the message, the reply updates the chatter, and PerfectWORK relays the reply to the followers.
<br><br>
Emails from your users to partners (customers, vendors) are sent from the email address of your users. Similarly, emails from partners to users are sent from the email address of the partners. This allows you to recognize at a glance who sent an email relayed by PerfectWORK.
<br><br>
If your database is hosted on our cloud (PerfectWORK Online), it is not necessary to add an outgoing email server to send emails from your custom domain. You can enjoy this feature by using the default PerfectWORK email server.

!!!Important
    The PerfectWORK server is subject to a daily email limit to prevent abuse. The default limit is 200 emails sent per day for databases with an subscription. This limit can be increased under certain conditions. See our FAQ or contact support for more information.

However, it is recommended that you configure your domain name to ensure that emails from your users reach your partners, rather than being considered spam.
<br><br>
For the same reason, we recommend that you always give your users an email address from a domain you manage, rather than a generic email address (gmail.com, outlook.com, etc.).

### Be SPF compliant
The Sender Policy Framework (SPF) protocol allows the owner of a domain name to specify which servers are allowed to send email from that domain. When a server receives an incoming email, it checks whether the IP address of the sending server is on the list of allowed IPs according to the SPF record of the sender.

!!! Note
    The SPF verification is performed on the domain mentioned in the Return-Path field of the email. In the case of an email sent by PerfectWORK, this domain corresponds to the value of the mail.catchall.domain key in the database system parameters.
    <br><br>
    See the documentation on incoming emails.

The SPF policy of a domain is set using a TXT record. How to create or modify a TXT record depends on the provider hosting the DNS zone of your domain name. In order for the verification to work properly, each domain can only have one SPF record.

If your domain name does not yet have an SPF record, the content of the record to create is as follows:
```
v=spf1 include:_spf.PerfectWORK.com ~all
```
If your domain name already has an SPF record, you need to update this record (and do not create a new one).
!!!Example
    If your TXT record is _v=spf1 include:_spf.google.com_ ~all, you need to edit it to add _include: _spf.perfectwork.app_: _v=spf1 include:_spf.perfectwork.app include:_spf.google.com ~~all_

You can check if your SPF record is valid with a free tool like [MXToolbox SPF](https://mxtoolbox.com/spf.aspx).

### Enable DKIM
The DomainKeys Identified Mail (DKIM) allows you to authenticate your emails with a digital signature.

When sending an email, the PerfectWORK server includes a unique DKIM signature in the headers. The recipient’s server decrypts this signature using the DKIM record in your domain name. If the signature and the key contained in the record match, this guarantees that your message is authentic and has not been altered during transport.

To enable DKIM, you must add a CNAME record to the DNS zone of your domain name:
```
PerfectWORK._domainkey IN CNAME PerfectWORK._domainkey.PerfectWORK.app.
```

!!!Tip
    If your domain name is mycompany.com, you need to create a subdomain PerfectWORK._domainkey.mycompany.com whose canonical name is PerfectWORK._domainkey.PerfectWORK.app.

How to create or modify a CNAME record depends on the provider hosting the DNS zone of your domain name. The most common providers are list below.

You can check if your DKIM record is valid with a free tool like DKIM Core. If a selector is asked, enter PerfectWORK.

### Check your DMARC policy
The Domain-based Message Authentication, Reporting & Conformance (DMARC) is a protocol that unifies SPF and DKIM. The instructions contained in the DMARC record of a domain name tell the destination server what to do with an incoming email that fails the SPF and/or DKIM check.

There are three DMARC policies: - _p=none_ - _p=quarantine_ - _p=reject_

_p=quarantine_ and _p=reject_ instruct the server that receives an email to quarantine that email or ignore it if the SPF and/or DKIM check fails.

If your domain name uses DMARC and has defined one of these policies, it is therefore imperative to be SPF compliant or to enable DKIM.

!!!Danger
    Yahoo or AOL are examples of email providers with a DMARC policy set to p=reject. We strongly advise against using an @yahoo.com or @aol.com address for your users. These emails will never reach their recipient.

_p=none_ is used for the domain owner to receive reports about entities using their domain. It should not impact the deliverability if the DMARC check fails.

You can check the DMARC record of a domain name with a tool like [MXToolbox DMARC](https://mxtoolbox.com/DMARC.aspx).

If one of your partners, customer or vendor, uses DMARC and has defined one of these policies, the PerfectWORK server cannot relay emails from this partner to your users.

You need to handle user notifications in PerfectWORK, or replace the email address of the partner with a default email address.

### Use a default email address
To force the email address from which emails are sent, you need to create the following key in the System Parameters of the database:
<br><br>
If mail.default.from is set, and contains a full email address, all outgoing emails are sent from the given address. This is a requirement to use Outlook with PerfectWORK.
<br><br>
You access the **System Parameters** in developer mode in the **Settings ‣ Technical ‣ Parameters ‣ System Parameters** menu.

## Email Templates
We all know writing good emails is vital to get a high response rate, but you do not want to rewrite the same structure every time, do you? That is where email templates come in. Without the need to rewrite the entire email structure every time, you save time to focus on the content. Multiple templates also let you deliver the right message to the right audience, improving their overall experience with the company.

!!!Note
    
    The email templates use QWeb. The composer allows you to edit emails in their final rendering, making customizations more robust as you don’t have to edit code.

### Defining a default reply to on your mail template
Although the field reply to is available within the mail templates, **this field is only used for mass mailing mode** (this means when sending templates on what we call bulk emailing). You can send emails in bulk in almost every app that has a list view. Select the records you want and click on the action button. If you have an option to send an email, you will see a mail composer with possible values to define:
<br><br>
You can also define them by default on the template:
<br><br>
Because of this, setting a value in this field is useless as the value defined will be totally ignored. The default reply-to value is the default catchall email address to ensure a communication between your customer and your PerfectWORK database. For more information about the way the catchall works, please check how to manage inbound messages.

### Transactional emails and corresponding URL for each company
When using PerfectWORK, multiple events trigger the sending of automated emails. These emails are known as transactional emails and sometimes contain links pointing to your PerfectWORK database.

By default, links generated by the database use the dynamic web.base.url key defined in the system parameters. More information about this parameter.

If the website application isn’t installed, the web.base.url key will always be the default parameter used to generate all the links.

It’s important to know that this key can only have a single value, meaning that in a multi-website/company database environment, even if you have a specific domain name for each website, the links generated to share a document or within a transactional email might remain the same, whatever the website/company related to the sending of the email/document.

This is not always the case as some PerfectWORK applications have a link established in the database with the website application, meaning that in this case, if a specific domain is defined for the websites, the URL generated in the email template will use the domain defined on the corresponding website of the company.

!!!Caution

    A document shared using the documents application will always use the web.base.url key, as the document shared isn’t associated with any particular website. Meaning that the URL will always be the same (the web.base.url key value), whatever the company it’s shared from, this is a known limitation!

On the other hand, sales orders made by a customer on one of your PerfectWORK e-commerce websites have a link established with the website from which the order was made. As a result, the e-mail sent for the sales orders uses the domain name defined for the corresponding website to generate the links.

For more information about how to configure your domains, we invite you to check our domain name documentation.

#### Updating translations within email templates
Email templates are automatically translated. Changing the translations shouldn’t be necessary. However, if for a specific reason you’d like to change some of the translations, this can be done.

Like any modification in the code, keep in mind that modifications that aren’t done correctly (for example modifications leading to bad syntax) can break the template, as a result, the template will appear blank.

In order to edit your translations, follow these steps from the template.

Click on the edit button, then on the language button

- Edit the language of a template
- A pop-up window with the different languages installed on the database will be displayed. From here, editing the translations will be possible. Don’t forget to hit the save button to preserve your changes.

## FAQ
This document contains an explanation of the most recurring mailing concerns.

We will start by addressing issues of outgoing emails (ex: my client has not received my email), and then, of incoming emails (ex: I do not receive responses from my customers in the database).

### Outgoing emails

#### What do you have to check if your email is not sent?
The first indicator showing you that the email has not been sent is the red envelope next to the date and time of the message.

##### Common error messages
You reached your daily limit:
```
Warning in PerfectWORK upon email limit reached
```
Each email service provider has its own email sending limits. The limits may be daily, hourly, and sometimes even per minute. This is the same for PerfectWORK, we have to limit our customers to prevent our e-mail servers from being blacklisted.

Here are the default limits for new databases:

- 200 emails/day for PerfectWORK Online and PerfectWORK.sh databases with an active subscription,

- 50 emails/day for one-app free and trial databases,

- in case of migration, your daily limit might be reset to 50 emails a day.

In case you hit the limit, you can:

- Ask our support team to increase your daily limit. We will analyze the situation of your database depending on (non-exhaustive list):

    - How many users in your database,

    - Which apps are installed,

    - Your bounce rate: the percentage of email addresses that did not receive your emails because it was returned by a mail server on its way to the final recipient. You can contact the support.

- Use your own outgoing email server to be independent of PerfectWORK’s mail limit (please refer to the corresponding documentation),

- Wait until 11pm UTC for the reset and click on the retry button: The Developer mode must be activated. Then, go to **Settings ‣ Technical ‣ Emails**


!!!Warning

    The daily limit is global to your database and can rise quickly! By default an internal message, a notification, a note, etc. counts as an email in your daily limit if it notifies someone.

You can mitigate this by receiving your notifications in PerfectWORK instead of by emails.

##### SMTP Error
You can find out why an email wasn’t transmitted successfully by reviewing the Simple Mail Transport Protocol (SMTP) error messages. SMTP is a protocol to describe the email structure and transmit it over the Internet, and the error messages generated by email services are helpful tools to diagnose and troubleshoot email problems.

##### No Error
PerfectWORK is not always capable of providing information for the reason it failed. The different providers implement a personalized policy of the bounce emails and it is not always possible for PerfectWORK to interpret it correctly.
<br><br>
If you have this problem on a recurring basis with the same client or the same domain, please do not hesitate to contact PerfectWORK Support for help in finding a reason.

Note: in such case, one of the most common reasons is related to SPF and/or DKIM configuration.

##### Why is my email sent late?
It may happen that you schedule an email campaign but it is not sent on time. We know that we use a delayed job to send emails that we consider as not urgent (Newsletters concept such as mass mailing, marketing automation, events). The system utility cron can be used to schedule programs to run automatically at predetermined intervals. We use that policy in order to avoid cluttering the mail servers and prioritize the communication.
<br><br>
The emails considered urgent (communication from one person to another one such as Sales Orders, Invoices, Purchase Orders, etc.) are sent directly.
<br><br>
By default, the Mass Mailing cron runs every 60 minutes. So, you should wait maximum an hour before the campaign is actually sent.

### Incoming emails
When you have an issue with incoming emails, there might not be an indication per se in PerfectWORK. This is the client who tries to contact a database who will get a bounce (most of the time 550: mailbox unavailable).

#### Emails are not received
Depending on the platform you are using:

#### Get help from support
In order to get helped efficiently, please provide as much information as possible. Here is a list of what can be helpful:

- The **EML** of the email, stating for Electronic Mail, is the file format containing all the technical information required for an investigation. The documentation of your own email provider might help you on how to get your EML files. Once you get the EML of the email, adding it in the attachment of your ticket is the most efficient way for us to investigate. The support will mainly focus on redundant issues.

- The exact flow you are following in order to normally receive those emails in PerfectWORK. Here are examples of questions whose answers can be useful:
    - Is this simply a reply from an email going out from PerfectWORK ?
    - Are you using an incoming email server or somehow redirecting?
    - Can you provide us with an example of an email that has been correctly forwarded ?

- Providing answers to the following questions:

    - Is it a generic issue or is it specific to a use case? If yes, which one exactly?
    - Is it working as expected? In case the email is sent using PerfectWORK, the bounce email should reach the PerfectWORK database and display the red envelope.