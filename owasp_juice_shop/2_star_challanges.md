1. Log In as Administrator (__2 Star__)

- Go to __/login__ page.
- Enter any data in login and password form and capture the POST request using burpsuite intercept.
- The data will be in this format : 
    - ` {"email":"a", "password":"a"} `

- Now switch off the intercept and enter the following data in form :
    - Email : ` 'or 1=1-- `
    - Password : anything (Doesnot matter !)

- __Explanation__ :

    - The request payload will look like this : 
        - ` {"email" : "'OR 1+1--", "password":"a"} `

    - The `'` character closes the brackets of the SQL query
    - The `OR` in SQL statement with 1+1 after it always returns true.
    - The `--` characters is used in SQL to comment out data, any restriction on login will no longer work as they are interpreted as comments.

- __Result__ : You get logged in as administrator in juice shop !.

2. Brute Force Admin Password (__2 Star__)

- Again send a login request with admin email as the payload.
- Intercept it on proxy
- This time, instead of forwarding, send the request to __Intruder__.
- Click __Clear $__ button to remove all burp quotes.
- Now add §§ to the password field inside quotes.
- These characters are the quotations implementation in burpsuite.
- Now set the __payload__ as __best1050.txt__
- You can find it here  :  ` /usr/share/wordlists/SecLists/Passwords/Common-Credentials/best1050.txt `
- Start the attack,
- 401 response will be a failed attempt.
- 200 Ok will be the successful login.
- Take the password from 200 OK request and login.

