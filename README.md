# Append row to Google Spreadsheet

Node.js module that makes it simple to append new rows to a spreadsheet.

* Integrates with [Google Spreadsheet API v3](https://developers.google.com/google-apps/spreadsheets/#adding_a_list_row)
* Authorization is done by OAuth 2.0 and JSON Web Token (JWT).
* ~~Uses ES6 generator functions for simple flow control.~~ (translated to ES5)

See more instruction here in this great blog post: [Accessing Google Spreadsheets from Node.js](http://www.nczonline.net/blog/2014/03/04/accessing-google-spreadsheets-from-node-js/).

![Example](example.png?raw=true)


## Installation

    npm install google-spreadsheet-append-es5
  

## Create a Service Account and share spreadsheet

1. Create a new project in [Google Developers Console](https://console.developers.google.com)
2. APIs > Enable Drive API & SDK
3. Credentials > "Create new Client ID"
4. Download private key and convet to PEM format: openssl pkcs12 -in downloaded-key-file.p12 -out your-key-file.pem -nodes
5. Copy the email address in Credentials > "Service Account"
6. Share a spreadsheet with service account email address
7. Copy the file ID from the spreadsheet URL: "https://docs.google.com/a/gmail.com/spreadsheets/d/{fileId}/edit"
8. The first row of your spreadsheet must contain the names of the fields (one per column) you're going to submit for each record
9. Note that the fields should be provided to the add() method in lowercase form.


## Example usage
  	var Spreadsheet = require('google-spreadsheets-append');
  	var spreadsheet = Spreadsheet({
    	auth: {
    		email: "abc@developer.gserviceaccount.com",
    		keyFile: "privatekey.pem"
    	},
    	fileId: {fileId}
  	});
  
  	// append new row
  	spreadsheet.add({timestamp: new Date(), email: "a@a.com"}, function(err, res){});
  

## MIT License

Copyright © 2014 Andreas Rimbe <a@rimbe.net> + Adrien Joly

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
