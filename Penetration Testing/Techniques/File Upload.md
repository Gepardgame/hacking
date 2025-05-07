```table-of-contents
```
## Defenses
### MIME
Checks File Ending
-> Just change the file ending
### Magic Number
more accurate than just file ending (UNIX uses that) 
### File Length Filtering
Mostly not issues for shells, as their quit small
### File Name Filtering
Can change file name to a random name, so uniqueness is given -> need to search your shell
### File Content Filtering
Very complicated -> no infos yet
## Client Side Bypass

### Turn off Javascript in your browser

This will deactivate the client side running javascript -> no checking here
But can render site unuseable
### Intercept and modify the incoming page
Simply remove the filter from the site before loading with Burp Suite
### Intercept and modify the file upload
Use Burp Suite to change the content of the file after the request is send from your browser.
### Send the file directly to the upload point
No Website = no filter
Just use curl with -F for appending a file


## Server Side Bypass

### File Extensions
If php is blocked, try php3-7 phps php-s pht  phar
also jpg.php can work
### Magic Numbers
List of [Magic Numbers](https://en.wikipedia.org/wiki/List_of_file_signatures)
Can be added with hexeditor

## Find Server-Side-Filtering
### File ending Black/Whitelist
Upload a valid file, with a some gibberish ending, like `.notaending`. If it goes through its a blacklist, if not its whitelist
### Magic Number
Some as above, but instead of ending a invalid magic number
### MIME
Some as above, but change the MIME type to php
### File length
Progressivly upload bigger files, until you reach the limit