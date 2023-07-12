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


## Scoping and Targeting

- Setting the scoping lets us define what to proxy and what to not.
- We can restrict Brup suite to only target the web application that we want to test.
- Switch to the target tab, right click on our target from the list and choose __Add to scope__.
- Burp will ask you whether to stop logging anything which is not in the scope.
- Say yes.

- We can check the scope in the scopes tab.
- We chose to disable logging out of scope traffic, but burp will still intercept them.
- To disable this, go to the proxy section and select Add URL Is in Target scope from intercept Client request section.
- With this option enabled, burp will intercept the traffic only when it is from the scope.

## Site Maps

- Site maps allow us to map our target application in a tree structure.
- Every page we browse, burp add it in the site map of that application automatically.


## Burpsuite Repeater 

- Repeater allows us to craft and/or relay intercepted request to the target.
- It means after intercepting the request from proxy, we can edit it and resend to the target.
- We can send the request from the proxy to the repeater by right clicking the request and selecting the **Send to repeater** option.

### Inspector

- Inspector is supplementary to the request and response fields of the Repeater window.
- Inspector shows the prettified breakdown of the request and response.