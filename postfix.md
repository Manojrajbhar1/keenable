**[POSTFIX]{.underline}**

Postfix is designed to be fast, secure, and easy to configure, making it
a preferred choice for many system administrators and organisations to
handle their email services. It is part of the standard set of
mail-related packages found in most Linux distributions, including
Ubuntu.

Features of postfix:-

Here are some key points about Postfix in Ubuntu:

1.  **Mail Transfer Agent**: Postfix acts as a mail transfer agent,
    > handling the routing and delivery of emails between different mail
    > servers.

2.  **Alternative to Sendmail**: Postfix is often used as an alternative
    > to Sendmail, another popular MTA. Many system administrators
    > prefer Postfix due to its simpler configuration and enhanced
    > security features.

3.  **Configuration:** Postfix can be configured through its main
    > configuration file located at \"/etc/postfix/main.cf.\"
    > Administrators can customise various settings to tailor the mail
    > server behaviour to their specific needs.

4.  **Security Features:** Postfix is designed with a strong focus on
    > security, aiming to prevent common email-related vulnerabilities
    > and unauthorised access.

5.  **Easy Setup:** Ubuntu provides straightforward package installation
    > and setup for Postfix, which makes it easier for users to get
    > their email server up and running.

6.  **Compatibility:** Postfix supports standard email protocols such as
    > SMTP (Simple Mail Transfer Protocol) and can work with other
    > mail-related software like Dovecot (an IMAP/POP3 server) to
    > provide a complete email service.

Overall, Postfix in Ubuntu is a powerful and reliable solution for
managing email services, making it a fundamental component for many
servers and organizations that require email communication capabilities.

**Installation of Postfix:-**

**Step 1**: Update package lists Open a terminal and run the following
command to make sure your package lists are up to date:

**Sudo apt update**

**Step 2:** Install Postfix Now, we can install Postfix using the
following command:

**sudo apt install postfix**

**Step 3:** Configuration Once the installation is complete, we may need
to do some additional configuration. Postfix\'s main configuration file
is located at /etc/postfix/main.cf.

To configure Postfix interactively, we can run:

**sudo dpkg-reconfigure postfix**

**Step 4:** Verify Postfix After the installation and configuration,
Postfix should be up and running. we can check its status with the
following command:

**sudo systemctl status postfix**

**Step 5:** Basic testing

we can perform a basic test by sending a test email to a local user.
Replace username with the actual username of a local user on your
system:

**echo \"This is a test email\" \| sudo mail -s \"Test Email\"
username**

To view the received email, you can use the mail command:sudo mail

Verify postfix is running;

**Systemctl status postfix**

![](media/image7.png){width="6.267716535433071in"
height="4.694444444444445in"}

**Testing for Postfix:-\
**

**ubuntu\@mail:\~\$ telnet localhost smtp**

Trying 127.0.0.1\...

Connected to localhost.

Escape character is \'\^\]\'.

220 mail.keenable.com ESMTP

**ehlo localhost**

250-mail.keenable.com

250-PIPELINING

250-SIZE 10240000

250-VRFY

250-ETRN

250-ENHANCEDSTATUSCODES

250-8BITMIME

250-DSN

250-SMTPUTF8

250 CHUNKING

**mail from:test**

250 2.1.0 Ok

**rcpt to:test3**

250 2.1.5 Ok

**data**

354 End data with \<CR\>\<LF\>.\<CR\>\<LF\>

**test smtp testing is done**

**.**

250 2.0.0 Ok: queued as 90D6F12022C

**quit**

221 2.0.0 Bye

Connection closed by foreign host.

![](media/image4.png){width="6.267716535433071in"
height="4.694444444444445in"}

**[Dovecot]{.underline}**

Dovecot is an open-source email server software that works in
conjunction with Postfix or other mail transfer agents (MTAs). It is
responsible for handling incoming email messages and allowing users to
access their email securely.

**Features of dovecot:-**

Here are the features of Dovecot explained in simple terms:

1.  IMAP and POP3 Support: Dovecot provides support for both IMAP
    > (Internet Message Access Protocol) and POP3 (Post Office Protocol
    > version 3), allowing users to access their emails from email
    > clients such as Thunderbird, Outlook, or mobile devices.

2.  Secure Authentication: It offers various authentication methods like
    > plain text, encrypted passwords, and secure mechanisms like
    > SSL/TLS (Transport Layer Security) for secure and encrypted user
    > login.

3.  Mailbox Organization: Dovecot organizes users\' emails into
    > mailboxes, allowing them to manage their emails effectively,
    > create folders, and keep their messages organised.

4.  Fast and Efficient: It is designed to be fast and
    > resource-efficient, enabling smooth email retrieval and access for
    > users even with large mailboxes.

5.  Mailbox Indexing: Dovecot maintains index files, making email
    > searches and folder navigation faster and more efficient.

6.  Sieve Filtering: It supports Sieve, a scripting language that allows
    > users to create mail filters and automatically sort or discard
    > incoming messages based on specific criteria.

7.  Quota Support: Dovecot can enforce mailbox quotas, limiting the
    > amount of storage space each user can consume to avoid excessive
    > disk usage.

8.  IPv6 Support: Similar to Postfix, Dovecot fully supports IPv6,
    > allowing communication over modern internet protocols.

9.  Integration with Postfix: Dovecot seamlessly integrates with Postfix
    > or other MTAs to provide a complete email server solution.

10. Pluggable Architecture: Dovecot\'s modular design allows for easy
    > extension and integration of additional functionalities or custom
    > plugins.

**How dovecot work:-**

Dovecot is an open-source email server that handles the retrieval (IMAP
and POP3) of messages from a remote mail storage server. When a user
requests their emails, Dovecot authenticates and accesses the stored
messages, then delivers them to the user\'s email client. It maintains
indexes for efficient searches and supports secure protocols like
SSL/TLS.

**For example**

when a user opens their email client and clicks on the inbox, Dovecot
connects to the remote mail server, retrieves the relevant emails, and
delivers them to the client for the user to view and manage**.**

**Dependency of postfix and dovecot:-**

Postfix and Dovecot work together in a typical email server setup. While
Postfix handles the email transfer and delivery aspects, Dovecot takes
care of user authentication, mailbox storage, and the retrieval of
emails for end-users.

When an email is sent to a domain hosted on a server with Postfix and
Dovecot installed, Postfix receives the email and stores it in the
appropriate mailbox directory. When a user\'s email client (like
Thunderbird, Outlook, or a smartphone\'s email app) wants to retrieve
emails, it connects to Dovecot, which then retrieves the emails from the
user\'s mailbox directory and presents them to the email client via the
IMAP or POP3 protocols.

In summary, Postfix and Dovecot are complementary components in an email
server setup. Postfix handles the mail transfer and delivery, while
Dovecot handles the retrieval and presentation of emails to users,
ensuring a complete and functional email service.

**Installation of Dovecot:-**

1.To install Dovecot on Ubuntu, you can follow these steps:

Update the package index:

**Sudo apt update**

2\. Install Dovecot:

Run the following command to install Dovecot and its necessary
dependencies:

**root\@mail:\~\# apt -y install dovecot-core dovecot-pop3d
dovecot-imapd**

3.Start and enable Dovecot service:

After the installation is complete, start the Dovecot service and enable
it to start automatically on system boot:

**root\@mail:\~\#sudo systemctl start dovecot**

**root\@mail:\~\#sudo systemctl enable dovecot**

4.Configure dovecot and follow below steps one by one in **vi
/etc/dovecot/dovecot.conf**

**root\@mail:\~\# vi /etc/dovecot/dovecot.conf**

**\# line 30 : uncomment**

**listen = \*, ::**

**5.**.Configure dovecot and follow below steps one by one in **vi
/etc/dovecot/conf.d/10-auth.conf**

**root\@mail:\~\# vi /etc/dovecot/conf.d/10-auth.conf**

**\# line 10 : uncomment and change (allow plain text auth)**

**disable\_plaintext\_auth = no**

**\# line 100 : add**

**auth\_mechanisms = plain login**

**6.** Configure dovecot and follow below steps one by one in **vi
/etc/dovecot/conf.d/10-mail.conf**

**root\@mail:\~\# vi /etc/dovecot/conf.d/10-mail.conf**

**\# line 30 : change to Maildir**

**mail\_location = maildir:\~/Maildir**

**7.**Configure dovecot and follow below steps one by one in **vi
/etc/dovecot/conf.d/10-master.conf**

**root\@mail:\~\# vi /etc/dovecot/conf.d/10-master.conf**

**\# line 107-109 : uncomment and add**

**\# Postfix smtp-auth**

**unix\_listener /var/spool/postfix/private/auth {**

**mode = 0666**

**user = postfix**

**group = postfix**

**}**

**8.A**fter complete all configuration,we need to restart dovecot
service

**root\@mail:\~\# systemctl restart dovecot**

**[SquirrelMail]{.underline} **

SquirrelMail is an open-source web-based email client designed to
provide users with a simple and easy-to-use interface for accessing
their email accounts through a web browser. In simple terms, it acts as
a bridge between a user and their email server, allowing them to read,
send, and manage their emails directly from a web browser, without the
need for dedicated email software like Outlook or Thunderbird.

**Role of SquirrelMail**

The role of SquirrelMail can be summarised as follows:

1.  Web-based Email Access: SquirrelMail allows users to access their
    > email accounts using a web browser, enabling them to check their
    > emails from any internet-connected device without installing any
    > additional software.

2.  Email Management: Users can read, send, and organize emails using
    > the SquirrelMail interface. It offers features like composing new
    > messages, replying to or forwarding emails, creating folders to
    > organize emails, and managing address books.

3.  User-Friendly Interface: SquirrelMail is designed to be simple and
    > user-friendly, making it easy for users to navigate and interact
    > with their emails regardless of their technical expertise.

4.  Platform Independence: As a web-based application, SquirrelMail is
    > platform-independent, meaning it can be accessed from various
    > operating systems, such as Windows, macOS, or Linux, as long as
    > there is a compatible web browser available.

5.  Email Server Compatibility: SquirrelMail is compatible with a wide
    > range of email servers, including popular ones like Microsoft
    > Exchange, Gmail, and other IMAP and POP3-based email servers.

6.  Customizability: Users can customize the appearance and behavior of
    > SquirrelMail to some extent, allowing them to tailor the interface
    > according to their preferences.

Overall, SquirrelMail simplifies the process of managing emails by
providing a straightforward, browser-based solution that eliminates the
need for installing email client software on individual devices. It\'s
particularly useful for users who prefer a no-frills email experience
with basic functionalities.

**Install SquirrelMail**
========================

### **Prerequisites**

-   A domain name(e.g. www.example.com)

-   A fully working SMTP server(e.g. Postfix)

-   A fully working IMAP server (e.g. Dovecot)

-   A non root-user with sudo privileges

-   Apache web server

**Step 1: Download the latest version of SquirrelMail**
-------------------------------------------------------

First, cd to the ***'/tmp'*** folder by typing the command below:

**\$ cd /tmp**

Next, enter the command below to download SquirrelMail

**\$ wget**
http://downloads.sourceforge.net/project/squirrelmail/stable/1.4.22/squirrelmail-webmail-1.4.22.zip

**Step 2: Unzip the archive file and copy it to the root of your website**
--------------------------------------------------------------------------

First, let us install the unzip tool on our Ubuntu server:

**\$ sudo apt-get install unzip**

Then, we need to unzip the SquirrelMail archive file using the command
below:

**\$ sudo unzip squirrelmail-webmail-1.4.22.zip**

We then move the content of the ***'squirrelmail-webmail-1.4.22'***
directory to the root of our website:

**\$ sudo mv squirrelmail-webmail-1.4.22/ /var/www/html/mail**

**Step 3: Set the right directory permissions**
-----------------------------------------------

In order for Apache to be able to interact with SquirrelMail without
read/write problems, we should set the right directory and file
ownership permissions using the command below:

**\$ sudo chown -R www-data:www-data /var/www/html/mail**

**Step 4: Configure SquirrelMail**
----------------------------------

SquirrelMail has a default configuration file
(***'config\_default.php'***). We need to copy this file to config.php
using the command below:

**\$ sudo cp /var/www/html/mail/config/config\_default.php
/var/www/html/mail/config/config.php**

Next we need to edit the file using nano editor to make a few changes:

**\$ sudo nano /var/www/html/mail/config/config.php**

We need to set the values below:

**\$domain = \'yourwebsite.com\'; // eg.;- keenable.com**

**\$data\_dir = \'/var/www/html/mail/data/\';**

**\$attachment\_dir = \'/var/www/html/mail/attach/\';**

The data directory is created by default once you install SquirrelMail
but we need to create the attachments directory using the command below:

**\$ sudo mkdir /var/www/html/mail/attach/**

We can run the command below one more time to ensure the permissions are
updated on the directory:

**\$ sudo chown -R www-data:www-data /var/www/html/mail**

**Step 5: Open SquirrelMail on your browser**
---------------------------------------------

You can visit your SquirrelMail application using the address
***'www.keenable.com/mail'***. If the setup was completed without a
problem, you should see this login page:

![](media/image3.png){width="6.267716535433071in"
height="4.694444444444445in"}

Then, just enter your username and password associated with your email
account and you will be able to login to the SquirrelMail dashboard.

![](media/image1.png){width="6.267716535433071in"
height="2.2916666666666665in"}

**[Test-cases for Email server]{.underline}**

  **Sr no.**   **Test case**                                **Test Description**    **Test Result.**
  ------------ -------------------------------------------- ----------------------- ------------------
  1            user login                                   login user sucessfuly   Pass
  2            Send mail Without Attachment                 Mail send sucessfully   Pass
  3            Send mail with attachment                    Mail send sucessfully   Pass
  4            Send mail with attachment and text message   Mail send sucessfully   Pass

**1.User-login:-**

![](media/image6.png){width="6.267716535433071in"
height="4.694444444444445in"}

**2.Sent Text mail:-**

![](media/image2.png){width="6.267716535433071in"
height="4.694444444444445in"}

**3.Sent mail with Attachment:-**

![](media/image8.png){width="6.267716535433071in"
height="4.694444444444445in"}

**4.Sent mail with both (Attachment and text-massege)**

![](media/image5.png){width="6.267716535433071in"
height="4.694444444444445in"}
