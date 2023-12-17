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
8. to increase the attachment upload size:
  - From the MailEnableAdmin in Windows >> servers >> localhost >> services and Connections >> right click on "WebMail" and select "Properties" >> from the tab "Advanced" increse the upload limit and then ok.
  - Navigate to C:\Program Files\MailEnable\BIN\NETwebmail or C:\Program Files (x86)\Mail Enable\Bin\NETWebMail and open the file "web.config >> edit this line to increase the limit:
     <httpRuntime maxRequestLength="10240" executionTimeout="3600" /> // 10240 is the upload limit in kb

9. enabling SSL server:
a. from IIS manager >> select the server >> from the section ISS select "Server Certificates" >> from the right side select "Create Self-Signed Certificate":
add certificate name and then ok.
b. from the MailEnable Admin in Windows >> Servers >> right click on "localhost" and select Properties >> select SSL tab and from the menu Defaul SSL Cerificate select the certificate.

c. from the MailEnable Admin in Windows >> Servers >> Services and Connections >> right click on SMTP and select Properties >> select the tab "Inbound" >> from the Port Settings section select "Settings" >> under the section Submission Port mark the options "Require SSL" and "Require connections to authenticate before sending email" and in the drop down menue select "Only allow secure authentication (using SSL or TLS)".
*** In the inbound tab also we have advanced settings. There we can set the message size as well.
