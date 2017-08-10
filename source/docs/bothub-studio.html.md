# BotHub Studio

## Why BotHub Studio?

### Backend Free

You can find many '*Make a chatbot in 10 minutes*' kind of articles today. Even BotHub.Studio says that too.

But, getting more traction, you face many hard engineering problems.

1. You should handle increasing *throughput*
1. Send *massive messages* to messenger platform efficiently to keep reasonable *responsiveness*
1. Sometimes message *orders messed up*
1. Someday you need *a scheduler*
1. Someday you need *a database*. Moreover, each user needs their own persistent properties
1. You need a *deployment automation* to eliminate SPOF to improve a reliability
1. Someday you need a *logging system*
1. ... And statistics, and *analytics* based on that

You need a complex backend architecture and a skilled backend software engineer to solve these tough issues. Hiring those engineer is not so easy with a limited budget.

Think about this. Many backend software engineers all over the world solve same issues in their own company. How inefficient it is. You can use your energy to solve better, more important, more productive issues.

BotHub.Studio is operated by senior backend engineers, we improve a backend of BotHub.Studio by every day. We only charge only a dozens of dollars per month. You pay tens of dollars per month, we can build a more robust backend, so everyone can enjoy the platform.


### Take Code Ownership

There are many services already on chatbot ecosystem. Some of them are great, especially for UI chatbot builder enables non-developer can build a chatbot with ease.

But we are developers. You can't bear our efforts are melted into specific commercial service, which can't be expressed in the form of code, be stored to GitHub. Sometimes you want a flexibility to mix several tools the service doesn't have yet.

You don't have enough time and money to make every part of chatbot from scratch. So you search some tools or frameworks which can help you. And you also want to have ownership of most important part.

BotHub.Studio helps you to deploy and run our own chatbot code. We only provide a chatbot backend. You can own important core of your chatbot and control it.


### Start Lean

We offer elastic pricing plans.

Start with a Start Plan. With it, you can build up to 5 chatbots, 50k interactions per month. Always with BotHub.Studio advertisement.

When you build serious chatbots, take a Pro Plan. With tens of dollars, you can build unlimited chatbots, usage-based pricing, earn a profit with an advertisement.


### Monetization

You may have or have not a monetization plan. BotHub.Studio helps you to earn a profit with an advertisement with ease. Just embed an ad code.


## Why Not...

There are some chatbot hosting alternatives.

### Why Not IaaS?

[AWS EC2](https://aws.amazon.com/ec2/pricing/on-demand/), the no 1 IaaS solution. It offers you a free tier for year.

| Product        | free tier | t2.micro | t2.small |
| -------------- | --------: | -------: | -------: |
| EC2            | $0        | $8.64    | $16.56   |
| RDS            | $0        | N/A      | $29.52   |
| Total          | $0        | $8.64    | $46.08   |

Moreover, you need to handle system engineering stuffs like linux kernel parameters, OS update, configuration automation for auto-scaling by yourself. BotHub.Studio manages not only low-level OS things but also many other infrastructures for you.


### Why Not PaaS?

[Heroku](https://www.heroku.com/pricing) is a wonderful PaaS solution. It offers a free plan for starter, and can be upgraded to paid plan afterward. Heroku has plans for hobbyist and professionals. Oh, you probably need a database too.

| Product  | free plan | Hobby plan | Standard plan (*1) |
| -------  | --------: | ---------: | -----------------: |
| Dyno     |        $0 | $7.00      | $25.00             |
| Database |        $0 | $9.00      | $50.00             |
| Total    |        $0 | $16.00     | $75.00             |

Heroku is a little expensive than EC2 but make many things easier. You don't need to struggle with OS stuffs, scaling issues. You just deploy your code and click a button to add a Dyno.

But, Heroku is not designed for chatbot. Chatbot need a several components to run serious chatbot such as a conversation management, user state management, analytics for chat, job scheduling. But Heroku is a general Paas solution so you should build such things by your hands.

BotHub.Studio offers all in one environment for chatbot hosting. We offers bot handlers and simple key/value database, job scheduling(coming soon), chat analytics, and more update comes.


### Why Not FaaS?

[AWS Lambda](https://aws.amazon.com/lambda/pricing/), the rising star of server and serverless world. No VM, only charges for number and duration of execution and it is soooo cheap! Just $0.408 per 1 million request (request charge + duration charge).

| Product           | Price (per 1M) |
| ----------------- | -------------: |
| Lambda (request)  |  $0.200        |
| Lambda (duration) |  $0.208        |
| Total             |  $0.408        |
| RDS (t2.small)    | $29.520        |
| Grand total       | $29.928        |

But you have to struggle with AWS jungle. Make an IAM account and grant proper permissions to it with strange AWS policy language, setup API Gateway. You need to setup a VPC also to connect it to RDS. RDS begin with t2.small plan.
