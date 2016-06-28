# node-red-contrib-aws-sdk

A function block where you can write your own code to execute aws-sdk nodejs library.

**Example of using aws-sdk inside this function block:**
	
```javascript
		var s3 = new AWS.S3();<br/>
			s3.createBucket({Bucket: 'myBucket'}, function() {<br/>
			var params = {Bucket: 'myBucket', Key: 'myKey', Body: 'Hello!'};<br/>
			s3.putObject(params, function(err, data) {});<br/>
		});
```

Reference: http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-examples.html