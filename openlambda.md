# OpenLambda (2016)

### What is the problem being solved?

This paper is trying to demonstrate the performance between the classical server-based models (applications deployed on backend servers) vs serverless computing. In so doing, it is trying to push for open-source efforts in the serverless computing paradigm.

### How was this problem solved previously?

Prior to this, servers were used to back online applications (emphasis on the entire application). There are several pain points: (1) servers are difficult to configure and manage e.g. many configuration parameters Elastic BS has 20 and (2) their startup time limits application scaling. 

### What is the main idea?

The main idea is to have a new programming model - the Lambda model. Developers create functions that run in response to events (e.g. the function can be a RPC handler that responses to an event which is a RPC call from a web application). This allows scaling, because the functions can be load-balanced and executed on any worker.

### What are the key results?

The paper shows that AWS Lambda (serverless) beats Elastic BS (server-based) in terms of lower response time, due to better scaling; also less configurations. The paper also analysed server-based workloads and compared it with an upper bound on the serverless paradigm. The results are convincing in terms of performance and scalability. 

### What are the main limitations of this paper?

The paper did not account for the cost / business model of serverless vs server-based models, as that might ultimately determine whether serverless models are taken up by the industry. Also, there are concerns about the limitations due to the stateless properties of the functions e.g. whether it can support longer-lived states or share states across many sessions.

### Why did this paper have an impact?

The paper provided convincing performance and scalability benefits of serverless models. It also classified many possible research directions. Also, it is open-sourced. I actually wonder how this project could become open-sourced without the backing of a company with servers, because ultimately they require a major stakeholder's influence.
