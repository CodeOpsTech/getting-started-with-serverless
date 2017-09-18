
## Serverless Principles

Five principles for building serverless applications by Peter Sbarski from his book “Serverless Architectures on AWS”: 

* Use a compute service to execute code on demand (no servers).

In serverless, all custom code should be isolated, independent and stateless. You should not need to use servers to perform any tasks. 

* Write single-purpose stateless functions.

The classic Single Responsibility Principle (SRP) applies for serverless functions. And they need to be stateless, i.e., give the same result no matter how many times called. Though lambda functions need not follow microservices style, most do follow this style. 

* Design push-based, event-driven pipelines.

Serverless functions are best suited for event-driven application architecture styles. You can trigger lambda functions based on events like file update, message arrival, notification receipt, etc. 

* Create thicker, more powerful front ends.

Serverless functions are designed to execute for short periods of time (e.g., max 5 minutes in AWS Lambda). Often backend services with "glue code" written with serverless functions are used. Such backends require a powerful thick clients. Modern JS frameworks are often used as frontends for backends written in serverless. 

* Embrace third-party services

## Drawbacks of AWS Lambda

* Vendor-lockin 
It may appear that functions help avoid vendor lock-in because we are just writing code and executing them in functions. However, our applications are tied to the the services the functions depend on in the cloud, for example, S3 or DynamoDB. 

* Limited control over the runtime environment 
  We cannot control much over the runtime environment except adjusting the limits for time duration for execution, memory, etc. 

* /tmp is limited to 500 MB size - that is a limiting factor for many kinds of applications. For example, if we want to convert a video from one format to another, then this limit matters. 

* Distributed systems
  Designing and implementing distributed systems in intrinsically hard. Testing for example - the logic in lambdas may be easily testable, how how the whole thing interacts with the cloud resources, and in asyncrhonous manner is hard.

* One technique is to use base64 to convert json to binary and pass it along and pass it along as context data. There is a python base64 library which does that.




