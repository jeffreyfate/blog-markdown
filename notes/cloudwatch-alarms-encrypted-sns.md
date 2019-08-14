AWS CloudWatch alarms are the lifeblood of any AWS devops process. They're great! They can alert you when all your s**t is on fire.

But, if you want to encrypt all the things, you run into a problem.

Most of the time, I send my CW alarm messages to a SNS topic which allows me to subscribe to it by whatever I want alerting me. Email, Slack, whatever.

Recently, I couldn't figure out why my alert wasn't being picked up by subscribers. Everything looked good:

![Topic History](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/topic-history.png)

But, looking at the details of this message revealed everything was not good:

`{
  "actionState": "Failed",
  "stateUpdateTimestamp": 1564596878595,
  "notificationResource": "arn:aws:sns:us-west-2:xxxxxxxxxxxxx:xxxxxxxxxx",
  "publishedMessage": null,
  "error": "null (Service: AWSKMS; Status Code: 400; Error Code: AccessDeniedException; Request ID: d0bc98c7-xxxx-xxxx-xxxx-9b1d0a389f53)"
}`

Hey! Why did it fail? Did I not have permission to send a message to this topic? No. Oh, it is encrypted. So, yeah, [you can't send a CW message to an encrypted SNS topic](https://aws.amazon.com/blogs/compute/encrypting-messages-published-to-amazon-sns-with-aws-kms/):

![Can't send CW alarms to encrypted SNS](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/encrypted-sns.png)

I'm sure if enough people complain, AWS will fix that, but for now be warned.

# 🐾