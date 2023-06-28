# OWASP Juice shop 4 star challanges

1. Poison Null Byte Challange (__4 Star__)

- Go to /ftp route to see all ftp services of the server.
- Try to download package.json.bak file.
- We will get a 403 error, which says that we can download only .md and .pdf files.
- To overcome this problem, we will use a character bypass called __Poison Null Byte__.
- %00 is the poison null byte.
- We have to encode it into url.
- Add %2500.md at the end of the url.
- It bypasses the 403 error and downloads the file.

- __Explanation__ : 
    - A poison Null byte is actually a NULL terminator.
    - By placing a NULL character in the string at a certain byte, the string will tell the server to terminate at the point nulling the rest of the string.