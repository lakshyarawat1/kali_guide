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