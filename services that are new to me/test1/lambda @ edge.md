ambda[@Edge](https://portal.tutorialsdojo.com/members/edge/) lets you run Lambda functions to customize the content that CloudFront delivers, executing the functions in AWS locations closer to the viewer. The functions run in response to CloudFront events, without provisioning or managing servers. You can use Lambda functions to change CloudFront requests and responses at the following points:

– After CloudFront receives a request from a viewer (viewer request)

– Before CloudFront forwards the request to the origin (origin request)

– After CloudFront receives the response from the origin (origin response)

– Before CloudFront forwards the response to the viewer (viewer response)

![Cloudfront Events that Trigger Lambda Functions](https://media.tutorialsdojo.com/cloudfront-events-that-trigger-lambda-functions.png)

In the given scenario, you can use Lambda[@Edge](https://portal.tutorialsdojo.com/members/edge/) to allow your Lambda functions to customize the content that CloudFront delivers and to execute the authentication process in AWS locations closer to the users. In addition, you can set up an origin failover by creating an origin group with two origins with one as the primary origin and the other as the second origin which CloudFront automatically switches to when the primary origin fails. This will alleviate the occasional HTTP 504 errors that users are experiencing.

Therefore, the correct answers are:

**–**  **Customize the content that the CloudFront web distribution delivers to your users using Lambda[@Edge](https://portal.tutorialsdojo.com/members/edge/), which allows your AWS Lambda functions to execute the authentication process in AWS locations closer to the users.**

**–**  **Implement an origin failover by creating an origin group that includes two origins. Assign one as the primary origin and the other as secondary, which enables CloudFront to automatically switch to if the primary origin encounters specific HTTP status code failure responses.**