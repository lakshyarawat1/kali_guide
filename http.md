# HTTP basics

- HTTP stands for Hypertext transfer protocol
- HTTPS is more secure approach to HTTP

# Requests and responses

Request format

- Method : specifies the method of the request like GET or POST
- Version : specifies the version of the HTTP
- Host : specifies the host i.e. the reciever
- Browser Version in user-agent field
- Referrer : specifies that the web page that we are reffering
- HTTP request always end with an empty line

Response format

- HTTP version
- Status Code
- Version number
- Current date, time and timezone
- Content-Type : tells the client what sort of content is sent
- Content-Length
- Blank line
- Content

# HTTP Methods

- GET : used to get information from a web server
- POST : used for submitting data to the web server and potentially creating new records
- PUT : submitting data to a web server to update information
- DELETE : used to delete information from a web server

# HTTP Status Codes

- 100-199 : Information Response ( tells the client to continue sending data )
- 200-299 : Success
- 300-399 : Redirection
- 400-499 : Client Error
- 500-599 : Server Error

# Cookies

- HTTP is stateless, i.e it doesn't remember previous requests and logs
- Cookies are used to store data for further use and make some statefullness in HTTP
