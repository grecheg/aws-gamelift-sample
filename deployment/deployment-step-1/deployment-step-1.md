## Step 1 Architecture Overview
![Step 1 Architecture Overview](./gomoku_arch_step_1.png)

This Lab will be using DynamoDB as the source of all user information and their match results. We will be storing simple information and also will be used as a source of truth for the leader board, which can be access via web. In addition, we will put an ElastiCache on top of DynamoDB to serve the said leaderboard to the public, as we know your app will draw a lot of attention, so we don’t want to hammer the database with same request all the time. 

And all the match results? We will use SQS to queue up all the match results, and insert into the database using lambda, so we can post process the results before inserting into the table. This will also ensure the game flow will not wait on other component to finish, giving the players a better fluid experience. Imagine when you have many players and they all try to send out results to be processed in line. This can cause congestion and in turn lead to bad user experience.
So, we shall begin with creating our DynamoDB table. 
1.	Sign in to AWS Console and head to DynamoDB page at https://console.aws.amazon.com/dynamodb
2.	Identify your region, and take note of it. We want to make sure all service components reside within the same region for this lab.
3.	On the console, click on Create Table icon, to create a new DynamoDB table.
4.	Create a table with name of “GomokuPlayerInfo” and set Primary Key as “PlayerName” with data type of String, then click on Create.

![Create Table Settings](./dynamo_create_table.png)
 
5.	Once the table is created, we will create a stream by clicking Manage Stream button. By default, stream is disabled. 

![Table Overview](./dynamo_table_overview.png)
![Manage Stream](./dynamo_manage_stream_setting.png)

6.	Select New and old images as view type, and click enable.
7.	Now, we have the base complete. Now, let’s create a test data sample. In the table, open the Items tab.

![Table Items](./dynamo_table_items.png)

8.	Click Create Item button to create a new DynamoDB row item.
9.	From the Editor, you can click the + button, followed by Append, and the data type. We will repeat to insert something that looks like below.

![Item Dropdown](./dynamo_create_item_dropdown.png)

10.	 We will add some data like below, and click Save button to save.

![Sample Item](./dynamo_sample_item.png)

Preparation for DynamoDB is now completed. Now, let’s go for ElastiCache. This will store the ranking information of this stack so we don’t DDB for every query all the time.
1.	Again, from AWS Console, let’s head to https://console.aws.amazon.com/elasticache/
2.	Create a new ElastiCache cluster. We will use Redis engine.
3.	Enter the necessary information as below picture. (We won’t test cluster mode)
