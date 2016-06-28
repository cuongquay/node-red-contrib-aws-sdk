# node-red-contrib-aws-sdk

A function block where you can write your own code to execute aws-sdk nodejs library.

[![npm version](https://badge.fury.io/js/node-red-contrib-aws-sdk.svg)](https://badge.fury.io/js/node-red-contrib-aws-sdk)

**Example of using aws-sdk inside this function block:**
	
```javascript
// Create a bucket using bound parameters and put something in it.
// Make sure to change the bucket name from "myBucket" to something unique.
var s3bucket = new AWS.S3({params: {Bucket: 'myBucket'}});
s3bucket.createBucket(function() {
  var params = {Key: 'myKey', Body: 'Hello!'};
  s3bucket.upload(params, function(err, data) {
    if (err) {
      console.log("Error uploading data: ", err);
      msg.payload = err;
      callback(msg);
    } else {
      console.log("Successfully uploaded data to myBucket/myKey");
      msg.payload = data;
      callback(msg);
    }
  });
});
```

This node exposes the **AWS** object that is created by require('aws-sdk') into the function context. In order to process the asynchronous operation, a callback(msg) function must call to send the **msg** context to the next node.  

Reference: http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-examples.html