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

3. Accessing administration section (__2 Star__)

- Open the Debugger ( in Firefox ) and Sources ( in Chrome ).
- Refresh the page and see the __main.js__ file.
- Go to /main.js file.
- Find `path:administration` in main.js file.
- This shows that admin panel is at /administration route of the app.
- Login as admin using the password or by bypassing the login.
- Go to the /administration page.

4. Viewing other person's cart (__2 Star__)

- Log In with any account and open your basket.
- Capture the request using burpsuite.
- Change the destination from basket/1 to basket/2
- Forward the request.

- You will see the other profile's basket.

5. Perform a reflected XSS attack (__2 Star__)

- Login as admin
- Go to orders history page.
- Click on the truck icon
- This led you to the tracking your order page.
- See the url : ` .....id=5012_31491 `
- Replace the value of the id with the following code.
    - ``<iframe src="javascript:alert(`xss`)" > ``

- __Explanation__ :
    - The server looks for the id of the order in the database.
    - This query is not sanitized thus vulnerable to xss.


6. Deprecated Interface (__2 Star__)

- Use a deprecated B2B interface that was not properly shut down.
- Login as any user.
- Go to the complain section and fill the complain form.
- Click on file upload button.
- You will see that only PDF and ZIP files can be uploaded.
- Trying to upload another file will probably give you an error message on the UI stating Forbidden File type.
- Open the main.js file in the devTools and file allowedMIMEType and you will notice "application/xml" and "text/xml" along with the expected pdf and zip files.
- This means that we can add xml file to the system.
- Try to choose any XML file.
- The auto Filter will remove any other file without pdf and zip extension.
- Choose show all files, and choose any xml file available.
- Upload the file and submit the form to solve the challange.

7. Five-star Feedback (__2 Star__)

- Get rid of all five star ratings from the web app.
- Solve the **access administration page** challange.
- Go to the admin page.
- Manually delete any 5 star ratings from the list of ratings.

8. Login MC Safesearch (__2 Star__)

- Log In with MC Safesearch's original user credentials
- Google mc safesearch and get to the music "Protect Ya' Passwordz".
- Watching the video we get to know that MC used the name of his dog "Mr.Noodles" as the password.
- He later changed the o's in the password with 0's.
- So the password will be "Mr. N00dles".
- Login as this password to solve the challange.
- This is an example of sensitive data exposure.

9. Visual Geo Stalking (__2 Star__)

- Get the answer to the security question of Emma.
- Go to photo wall.
- See the photo of the user e=ma2
- Open the photo in a new tab.
- Zoom on the photo to see a logo of the company called ITsec.
- Enter ITsec as the answer to the security question.
- Press submit to solve the challange.

10. Meta Geo Stalking (__2 Star__)

- Get the answer to the security question of John.
- Go to photo wall.
- See the photo of the user j0hn.
- See the meta data of the photo using any tool like exiv2 or exiftool.
- See the coordinates of the photo.
- Search the coordinates on google maps.
- The coordinates are of Daniel Boone National Forest.
- Enter the answer as Daniel Boone National Forest to solve the challange.


11. Wierd Crypto (__2 Star__)

- Inform the shop about the algorithm or library that it should not be using.
- Forge a coupon code that gives you a discount of at least 80%.
- This shows the z85 exploit.
- Some other exploits are of base64, hashid, md5 and base85.
- Go to the customer feedback.
- Give a feedback mentioning the z85 exploit or any other.
- Submit the feedback to solve the challange.

12. Empty User Registration (__2 Star__)

- Register a user with the email address and password as empty fields.
- Go to the register page.
- Enter the email and password as empty fields.
- Enter other fields.
- Inspect the element and remove the disabled property from the submit button.
- Click on the submit button.
- Solve the captcha.
- Challenge solved.