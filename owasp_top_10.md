# OWASP Top 10

Top 10 Vulnerabilities 

## Injection

- Injection flaws occur because user input in interpretted as actual commands or parameters by the application.
- SQL injection occurs when user inputs a SQL query.
- Command injection occurs when user input is passed to system commands.
- Main **defense** for preventing injection is to ensure that user controlled inputs is not interpreted as commands or queries.

### OS Command Injection

- Command injection occurs when server side code of web application makes a system call on hosting machine. 
- Attacker takes advantage of it 
- **Blink Command Injection** occurs when the system command made to the server does not return  the response to the user.
- **Active Command Injection** always returns the response back.

## Broken Authentication

- Some common flaws in authentication mechanisms are :
    - Brute Force attacks
    - Use of weak credentials
    - Weak session cookies

- Mitigations for broken authentication mechanisms :
    - To avoid password guessing, enforce a **strong password policy**
    - To avoid brute force attacks, enforce a **automatic lockout** after a certain amount of attempts
    - Implement multi factor authentication

## Sensitive Data Exposure 

- When a webapp accidentally divulges sensitive information.
- Can be a man in the middle attack.
- may be because of weak encryption on any transmitted data that may be intercepted by the attacker

### Flat File Databases

- When the data is stored in a file in the web server itself then it is called flat file database
- when the flat file database is stored in root directory of the server then it can be queried by the outside user
- The most common format of flat file database is an sqlite database.
- use **sqlite3 {databasename}** to access the DB
- see tables using .tables command
- you can get some passwords in hashed forms

### Cracking Hashes

- CrackStation is an online tool for crackin weak password hashes.

## XML External Entity (XXE)

- XXE attack is a vulnerability that abuses the features of XML parsers/data
- In-band XXE attack is the one in which the attacker recieves an immediate response to XXE payload
- Out-band XXE attack aka blind XXE, there is no response from the web app
- Attacker has to reflect the output of the XXE payload to some other file or own server.

### Basics about XML

- eXtensible Markup Language defines a set of rules for encoding documents in a format that is both human-readable and machine-readable.
- It is a markup language for storing and transporting data.
- Data stored in XML can be changed at any point of time without affecting the data presentation
- XML allows validation using DTD and Schema. 

### DTD

- DTD stands for Document Type Definition
- DTD defines the structure and the legal elements and attributes of the XML document

## Broken Access Control

- A common user gets the access to the resources and data that only administrator user was supported to have access to.

### Scenarios demonstrating access control weaknesses 

- Scenario 1 : The app uses unverified data in SQL call that is accessing account information
        ``` 
            pstmt.setString(1, request.getParameter('acct));
            ResultSet results = pstmt.executeQuery();
        ```
    An attacker simply modifies the 'acct' parameter in the browser to send whatever account number they want. 

-  Scenario 2 : An attacker simply forces browsers to target URLs. Admin rights are required to access the admin page.

    ```
        http://example.com/app/getappinfo
        http://example.com/app/admin_getappinfo
    ```

    if unauthenticated user can access the either page, it a flaw.

Simply put, broken access control allows attackers to bypass authorization which can allow them to view sensitive information or perform tasks of a privileged user.

### IDOR Challenge

- IDOR or Insecure Direct Object reference, is the act of exploiting  a misconfiguration in the way user input is handled, to access the resources you wouldn't ordinarily be able to access.


## Security Misconfiguration

Security Misconfiguration includes

- Poorly configured permissions on cloud services, like S3 buckets
- Having unnecessary features enabled, like services, pages, privileges
- Default accounts with unchanged passwords
- Error messages that are overly detailed and allow the user to find out more about the system.
- Not using HTTPS security headers.

This vulnerability can lead to more vulnerabilities, such as default credentials, XXE or command injection.

## Cross Site Scripting (XSS)

It is a security vulnerability which allows the attacker to execute malicious scripts and have it execute on a victim's machine.

### Types of Cross Site Scripting (XSS)

1. Stored XSS : the most dangerous type of XSS. Often happens when a website allows user input that is not sanitized when inserted into the database.
2. Reflected XSS : malicious payload is part of the victims request to the website. Here, attacker needs to trick the victim to click on URL to execute payload.
3. DOM Based XSS : 

### XSS Payload 

- Some payload types are :
    - Popup's
        ```
            <script>alert("Hello, world!");</script>
        ```
        Creates a hello world popup on users browser

    - XSS keylogger : You can log all keystrokes of the user, capturing the password and other sensitive information they type in website.
    
    - Port Scanning 

    - Popup that reflects the machines IP address
        ```
            <script>alert(window.location.hostname);</script>
        ```

    - Pop up to reflect cookies 
     
           ```
            <script>alert(document.cookies);</script>
        ```

## Insecure Deserialization

- Replacing data processed by an application with malicious code, allowing anything from DOS to RCE.
-  ***Serialization*** is the process of converting objects used in programming into simpler, compatible formatting for transmitting between systems or networks for storage of processing.
- ***Deserialization*** is the reverse of this, converting serialized info into objects.
- Insecure deserialization occurs when data from an untrusted website gets executed because there is no validation or filtering.

### Cookies

- Cookies stores usernames and passwords and other information , but they are mostly temporary and ends after some time. 
- Some important attributes of cookies are :
    - Cookies Name : Name of the cookie to be set
    - Cookie Value : Value of the cookie, plaintext or encoded
    - Secure Only : If set, cookies will be only set over HTTPS
    - Expiry : Timestamp of the cookie to expire
    - Path : Specific URL which sets the cookie