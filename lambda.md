## Serverless Lambda
- Reference https://cloud.spring.io/spring-cloud-function/reference/html/spring-cloud-function.html

<p> it means, we do not need to manage the server. its cloud provider who is gonna manage it. You only need to write the code and run it on cloud. </p>

### Advantage
- No need to manage server
- Flexibility-> Based on the incoming request autoscalling will happens automatically (scalling can be customized).
- If your application is not being used(it is idle) you don't have to pay anything

### where to use
- if you want to expose an endpoint, or any task without any sort of dependency on server or OS

## Builing Spring Boot Application And Deploy it on AWS 
### Create new Spring boot application(springboot-awslambda-app1)
- Create a new spring boot application with Spring Cloud Function dependency
- The spring cloud function dependency exposes the function as an HTTP endpoint. After we run the application, we can curl our target to test it locally.
- So now run the application and test it using postman or curl command.

### Deploy the above application on aws lambda
- add the following dependencies
  - ```spring-cloud-function-adapter-aws```
  - ```aws-lambda-java-events```
  - ```aws-lambda-java-core```
  - ```spring-boot-thin-layout``` Plugin for lightweight jar.
- Create a class ```TestHandler``` extending ```SpringBootRequestHandler``` class as shown below. Actually this helps spring to serialize and deserialiaze the object.
 ```
 public class MyStringHandlers extends SpringBootRequestHandler<String, String> { //String, String denotes that endpoint will take string as input and produce String as output

}
 ```
- Go to your aws console
- Create a lambda function(create lambda fun->author form scratch+function name+java8/11/ runtime)
  - Go to basic setting ->edit->Provide Request Handler class ```com.xyz.TestHandler```
  - In Environment variable give the function name as key value ex.  key ```Function_Name``` and Value ```toUpper```
- Lambda function is created, <your lambda function>-->action->upload zip jar
- Now test it Steps are give below
   - select a test event-> configure test event->give event name+pass the req param if needed else leave it as blank now cleck on create
   - click on test button on top right.
