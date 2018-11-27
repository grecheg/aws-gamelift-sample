## Step 4 Architecture Overview
![Step 4 Architecture Overview](./gomoku_arch_step_4.png)

This part is getting the Server binary and configuring the Gamelift service to work together. The server binary is precompiled, so there is no need to alter anything. However, if you like to, you can compile and use your binary as the source code is included with the distribution.

1.	First, we will need to create a new IAM user so can be used by the server binary. The user will need SQS access to the queue we created at Section 1.
2.	Open IAM console at https://console.aws.amazon.com/iam and create a new user. We will create a user with Programmatic access only, since this user is to be used by the matchmaking server binary.
 
![IAM Add User](./iam-add-user.png)

3.	Head to next page by clicking Next: Permissions button.
4.	In the Permissions page, select to Attach existing policies directly, and choose to allow AmazonSQLFullAccess.

![IAM User Permissions](./iam-user-permissions.png)
 
5.	Then, click Create user to create a new user.
6.	When the user is created, you will see the AccessKeyID, and associated Secret access key. Take note of the ID and the key. 

![IAM User Creds](./iam-user-creds.png)
 
7.	Download the pair by clicking the download button.
8.	Now, we need to grab the binaries. For this lab, the binaries are all prepared in the binary folder. Note that if you want to compile the binary yourself, please refer to Appendix B.
9.	From the folder, you can see files, GomokuServer.exe, aws-cpp-sdk-*.dll, config.ini, install.bat, aws-cpp-sdk-gamelift-server.dll, vc_redist_x64.exe inside the GomokServer folder.
10.	Using your favorite text editor, edit the config.ini file. File has 4 configuration elements. SQS_REGION is where we put the queue. SQS_ACCESSKEY and SQS_SECRETKEY are account information we made from above. And finally, SQS_ENDPOINT is the end point address for the queue. Save and close the file.

![SQS Config](./config-ini.png)





- To proceed to the next step, click [here](../deployment-step-5/deployment-step-5.md)