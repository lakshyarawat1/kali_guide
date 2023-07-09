# OWASP JUICE SHOP 1 Star Challanges

1. Access a confidential Data Challange (__1 Star__)

- go to /ftp directory to list all ftp server files.
- Download acquintions.md file to solve the challange.
- This is an example for  sensitive data exposure.

2. Bully Chatbot (__1 Star__)

- Sign In as any user.
- Go to the chatbot route and ask the chatbot for discounts.
- Ask some questions like Please can I get a discount coupan ?
- It will give you a discount coupon.

3. Perform a DOM XSS Using the Bonus Payload (__1 Star__)

- Put the below payload in the search bar of the home page.
- `<iframe width="100%" height="166" scrolling="no" frameborder="no" allow="autoplay" src="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/771984076&color=%23ff5500&auto_play=true&hide_related=false&show_comments=true&show_user=true&show_reposts=false&show_teaser=true"></iframe>`
- This is initiate the DOM XSS attack.

4. Provoke an unhandled error (__1 Star__)

- Here are two approaches to invoke such errors :

    - Visit http://localhost:3000/rest/qwerty

    - Log IN to application with single quote as the userName ' and anything as password.

- Both of these approaches will provoke an unhandled error.

5. Exposed Metrices (__1 Star__)

- This is a type of __Sensitive Data Exposure__.
- The metrics of any target are available in /metrics route of the app.
- Visit __http://localhost:3000/metrics__ to view the metrics of the juice shop.

6. Close multiple "Challange Solved" notifications in one go (__1 Star__)

- Read the success notification
- Shift and click the X button to close all notifications in one go.
- Problem solved

7. Retrieve the photo of Bjoern's cat in "melee combat-mode" (__1 Star__)

- Visit __http://localhost:3000/#/photo-wall__
- The photo is broken.
- Right click the photo and inspect the img tag.
- You can see that src attribute has got a value containing # keyword that is making the image to crash.
- Right click to open the src of the image in a new tab.
- Replace the two # signs with their relevent URL-encoded characters.
- %23 is the URL encoding of # sign.
- Open http://localhost:3000/assets/public/images/uploads/😼-%23zatschi-%23whoneedsfourlegs-1572600969477.jpg 
- Go back to application to save the progress.

8. Outdated Allow List (__1 Star__)

- Login as any user in the application.
- Go to your basket page and find donations and credit card option.
- See that all the donation links are passed to __redirect_to__ argument.
- Open the __main.js__ file from inspect and find the redirect_to property.
- Step through all the matches and find out three functions that are called from hidden buttons.
- Open any one of these urls to solve the challange.

9. Read the privacy Policy (__1 Star__)

- Simple go to your profile and read the privacy policy to solve the challange.

10. Repetitive registration (__1 Star__)

- Go to the user registration page.
- Fill the registration form except the password and confirm password field.
- Enter the password as any thing eg. 12345.
- Enter the confirm passwird as 12345.
- Now change the above password field as anything other than the confirm password.
- You will see that the password do not match error does not throw.
- Register the user to solve the challange.

11. Zero Stars (__1 Star__)

- Give a devastating zero star review.
- Place an order
- Go to the feedback form and fill the form except the stars section.
- You will see that the submit button is disabled.
- Inspect the button and remove the disabled property from the tag.
- Now the button is enabled.
- Submit the form to solve the challange.