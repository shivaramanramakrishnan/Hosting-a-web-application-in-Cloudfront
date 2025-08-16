<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Fetch Data with AWS Lambda

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-lambda)

**Author:** SHIVARAMAN RAMAKRISHNAN  
**Email:** shivaraman.r02@gmail.com

---

## Fetch Data with AWS Lambda

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_p9thryj2)

---

## Introducing Today's Project!

Now we will create a dynamoDB table for our lambda function to fetch data from. 

 Create a database table to store user data.
 Create a serverless function to retrieve user data.
 Write tests to validate if your function can fetch data from DynamoDB.
Secure your serverless function with proper permissions.
 Secure your database with an inline policy

### Tools and concepts

Today we learned how to create tables in DynamoDB service of AWS and learned it is seamless in terms of creating new columsn as and when required. We also learned how to test our lambda function to see if it can access the database created, updating its policies and creating new policy to limit the access as it is required.

### Project reflection

Not long

Yes

---

## Project Setup

To set up my project, I created a database using DynamoDB. We created a table in it called userdata  with the partition key userID which means its the primary key, the central sort of column.

In the table, i added a test data with 3 columns and its datas. The userid, name and email. This will create an entry for our testing. 

DynamoDB is schemaless which means that when initailly we added a initial key(column), it doesnt mean thats the only column we can use. We can add more attributes as we go which gives us a lot of flexibiliity.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_a112c3d5)

### AWS Lambda

AWS Lambda is a service that lets you run code without needing to manage any computers/servers - Lambda will manage them for you.

Lambda runs your code only when you need it to (so you're not paying for any idle time).

---

## AWS Lambda Function

The execution role makes sure the function only has the permissions it needs to do its job, minimizing the potential for security vulnerabilities.

My funtion takes a userId as input, grabs the corresponding data from the UserData table, and returns it to you.

The second half of the code (i.e. beginning with try {) handles potential errors during the database operation, so you get a tailored error message that tells you what went wrong.

The code uses AWS SDK, which is the AWS Software Development Kit (SDK) is a set of tools that let developers build apps that interact with AWS.

Think of it like a library of pre-written code that lets you use AWS services without having to write all the code yourself. 

Our code uses the AWS SDK to use pre-written functions for communicating with DynamoDB and getting data from a table. Without the SDK, you'd have to manually write the code to interact with AWS, which would be much more complex and error-prone.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_a1b2c3d5)

---

## Function Testing

To test whether my Lambda function works, I created a test event in the lambda function. The test is written in JSON which will fetch the userID 1 from our dynamodb table. If the test is successful, I'd see a green pop up showing it is successful in retriving a userid that we mentioned. 

The "success" message simply means the function itself could run (there are no errors with the code), it doesn't mean the function achieved what you want it to do! 
 we haven't given it explicit permission to access our DynamoDB table. This means DynamoDB is currently blocking off our Lambda function from reading the table's items!

Because Lambda can't read any items, it has no choice but to tell us that its access was denied.



![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_u1v2w3x4)

---

## Function Permissions

We will resolve the accessdenied error by giving permission to access the data and retrive them.

Neither provides the GetItem permission required to read data from the table.

We pick this one becauuse it has the neccessary function - GetItem which will fetch and retrive the data needed from our table

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_3ethryj2)

---

## Final Testing and Reflection

Now that we have added the dynamodb policy to get item to our lambda function, it will be successful to get any data from our table that is being requested

Web apps are a popular use case of using Lambda and DynamoDB. For example, I could help customers get product info or order histroy by fetching data from DynamoDB.
Lambda can help social media apps fetch user profiles or automatically retrieve all content (e.g. videos or images) linked with a profile.

Lambda can help news sites or blogs fetch articles based on user queries.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_p9thryj2)

---

## Enahancing Security

We are replacing the readonly access because there are still other permissions in that policy which are not necessary for us. We only need the get item permission. 

I used the visual method as it is easy and with just a few clicks you can set up exactly what you want it to do, that is just read the item from Userdata table

When updating a Lambda funciton's permission policies, you could risk the function loosing access to what is required and essentially failing. I validated the function still works by using the test event in the function and seeing if it fetches the requested data with the updated policies.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-lambda_1qthryj2)

---

---
