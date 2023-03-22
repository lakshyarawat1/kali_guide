# Burpsuite

Burpsuite is a framework written in Java that provides a one-stop-shop for penetration testing

# Features in burpsuite community edition

- Proxy : Burpsuite allows us to intercept and modify requests/responses when interacting with web applications
- Repeater : allows us to capture, modify and then resend the same request numerous times.
- Intruder : It allows us to spray and endpoint with requests. Often used for brute force attacks
- Decoder : It decodes the captured information or encodes the payload
- Comparer : compares two pieces of data. 
- Sequencer : We use it when assessing the randomness of tokens such as session cookie values. If the algorithm is not generating random values then it may be vulnerable.


# Burp Proxy

- allows us to capture requests and responses and manipulate them too.
- captures the packets when intercept is on
- even if intercept is off burpsuite keeps a track of the requests and responses in http history subsection
- it also captures and logs the websocket connections in websocket history subsection
- any request captured can be sent to other tools in the framework by right clicking them

## Proxy traffic through burpsuite

There are two ways to do so

- We can use embedded browser
- We can configurate our local browser to proxy traffic through Burp

## Configuring local browser for burp

- burp proxy works by opening localhost:8080
- we need to direct all our traffic through this port
- we can use a firefox extension called Foxy Proxy
- click Add button and fill the details and save
- activate this config now

## Proxying HTTPS 

- to proxy HTTPS we need to manually add a **Certificate Authority** certificate to our list of trusted certificates
- download a file **cacert.der** and save it
- next type ```about:preferences``` in firefox search bar and search for certificates.
- import a new certificate and select a file we just downloaded.
- Select Trust this CA to identify sites
- Done

## Burpsuite browser

- Uses a proxyed chromium browser


## Scoping and targetting

- A lot of information comes in front of us out of which a lot is not useful
- Adding a **scope** filters the results
- Go to target tab and select add a scope

