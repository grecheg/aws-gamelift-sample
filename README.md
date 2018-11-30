

# aws-gamelift-sample
This workshop contains a sample game project using Amazon GameLift and AWS services including DynamoDB, Lambda, SQS, S3, EC2, ElastiCache and API-Gateway. This is a simple board game called [Gomoku](https://en.wikipedia.org/wiki/Gomoku), but it is technically and functionally identical to a real-time session-based online game.  It is similar to connect 4 except that it is played on a Go board and the objective of the game is to connect five pieces in a row. 

<img src="web/gomoku.png" width="600" height="600"/>

 - For infrastructure engineers and system administrators, this workshop demonstrates how to leverage multiple AWS managed services (Gamelift, DynamoDB, Elasticache, etc.) to build a session-based online game on AWS.
 - For game developers, this workshop goes through architectural best practices in implementing session-based online games, empowering developers to integrate these services into their code.


## Sample Game Architecture
![Architecture Overview](web/gomoku_arch.png)


## Deployment

 - Play and Deployment guide [here](deployment/deployment-step-1/deployment-step-1.md)


## Serverless version with FlexMatch
 - Functionally identical, but re-implemented in a Serverless way using FlexMatch can be found in [here](https://github.com/awslabs/aws-gamelift-sample/tree/FlexMatch)


## Future Work
 - Developing a Hands-on Technical Workshop to demonstrate the use of Amazon GameLift with AWS managed components for game services.
 - Developing Monitoring for GameLift Services
 - Developing a CloudFormation template for a one-click deployment
