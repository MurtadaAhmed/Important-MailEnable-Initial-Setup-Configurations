# MailEnableSetup
1. download and install mailenable from here: https://www.mailenable.com/standard_edition.asp
2. Open MailEnable from start menu >> Mail Enable >> MailEnable
3. From the left side Message Manager >> Post Offices >> yourwebsite.com >> Mailboxes >> New Mailbox (create the user and the password, in the Mailbox type mark it as ADMIN). Each user we create here represent an email account (username@yourwebsite.com).
4. Give the admin access:
From the left side Message Manager >> Post Offices >> yourwebsite.com. Right click on yourwebsite.com >> Properties >> Web Admin tab >> enable all the options and click ok.
4. To configure the urls for the webmail and webmailadmin:
- open IIS manager in windows server >> sites >> in both "WebEnable WebAdmin" and "WebEnable Webmail" options click on the right site option "Binding":
- set the ip address to the local ip address
- set the host names:
webmail.yourwebsite.com >> this is for "WebEnable Webmail"
webmailadmin.website.com >> this is for "WebEnable WebAdmin"
5. Add webmail and webmailadmin subdomains in your DNS manager (cloudflare for example) as A records.
6. You can access the links webmail.yourwebsite.com & webmailadmin.website.com and login with the userinformation that we set up in step 3.
7. Test sending and receiving emails using webmail.yourwebsite.com.
