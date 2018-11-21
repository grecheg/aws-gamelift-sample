## Step 2 Architecture Overview
![Step 2 Architecture Overview](./gomoku_arch_step_2.png)

In the previous section, we have went through base service for the stack. Now we will be creating bonding lambda service which will deal with user’s activity and processing their result.
In this example, we will deal with 3 different lambda functions. 
1.	Open Lambda console at https://console.aws.amazon.com/lambda
2.	From console, click create function button to start creating our first function.
3.	For our functions, since we know what we are creating, click Author from scratch to create an empty Lambda function.
4.	Input game-sqs-process into the Name field.
5.	Select Python 2.7 as its runtime.
6.	Select Choose an existing role for Role and execute Create function after selecting Gomok-game-sqs-process as the said role.
7.	When the function is successfully created, you will see the Designer pane. From left side select CloudWatch Events as the trigger. 
 
8.	Lower in the screen, in Configure triggers section, in the Rule drop box, select “Create a new rule”Rule name, use any name you’d like to. For Rule type, choose Scheduled expression, and for the Scheduled expression itself, we want to make this Lambda to run every minute. So we will use rate expression as “rate(1 minute)”
