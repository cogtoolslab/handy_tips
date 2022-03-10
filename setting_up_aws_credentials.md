
## setting up your AWS credentials
**Author: Will McCarthy**

If you haven’t used AWS before there is one step that may be new to you, which is setting up a file on your local machine that stores your login credentials. This allows you to do things like upload stimuli to S3. I suggest doing this now, as it’s likely you’ll use S3 in the future.
To do this you need to make a directory in your home directory ~/.aws/  (yes, with a .). Then make a file within that directory called credentials (yes, no file extension- just credentials). If you have a single aws account, the contents of this should be as outlined in the email:
```
[default]
aws_access_key_id=COPY_IN_FROM_EMAIL
aws_secret_access_key=COPY_IN_FROM_EMAIL
```

This says that when trying to access S3, by default your machine should use these credentials.
If you have several aws accounts, you might want to use a different account at different times. To store credentials for different users, you can do the following:
```
[TYPE_OTHER_NAME_HERE]
aws_access_key_id=COPY_IN_FROM_EMAIL
aws_secret_access_key=COPY_IN_FROM_EMAIL
```

From what I understand, you can type any name in TYPE_OTHER_NAME_HERE, but I’ve been using my usernames e.g. LAX so I know which credentials are which. You’ll then be able to choose which account to use when you upload things to S3.
At the end of this process you should have something like this:
```
[user_1]
aws_access_key_id=XXXXXXXXXXXXXXXXXXXX
aws_secret_access_key=XXXXXXXXXXXXXXXXXXXX

[user_2]
aws_access_key_id=XXXXXXXXXXXXXXXXXXXX
aws_secret_access_key=XXXXXXXXXXXXXXXXXXXX
```
