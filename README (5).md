<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Three-Tier Web App

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-compute-threetier)

**Author:** SHIVARAMAN RAMAKRISHNAN  
**Email:** shivaraman.r02@gmail.com

---

## Build a Three-Tier Web App

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_2b3c4d5e)

---

## Introducing Today's Project!

In this project we will create a 3 tier architecture web app with a presentation layer, logic tier, and data tier.

### Tools and concepts

In this project we learned how to host a 3 tier web application using AWS.

The presentation tier is the front end which is stored in an S3 bucket and hosted using Cloudfront.
The logic tier has a nodeJS script to fetch userdata created and a rest api is created using API Gateway to make sure the lambda function communicates with the data created in DynamoDB which is where the 3rd tier is.
DynamoDB, a noSQL database is used to create a table which is where the data would be stored at 

### Project reflection

Around 3 hours

Great

---

## Presentation tier

For the presentation tier, we will set up a bucket where the html file, css, js file are stored in a s3 bucket and distributed through cloudfront

I accessed my website by hosting it in cloudfront. It publishes the web page through cloud

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_3a4b5c6d)

---

## Logic tier

In this step, we are going to:

Create a Lambda function to fetch data from a DynamoDB table.

Write the code for your Lambda function.

Create an API Gateway REST API.

Create a resource and method to handle GET requests.

Deploy the API to make it accessible.



This code sets up a Lambda function that retrieves data from a DynamoDB table.

It looks for specific user data based on a userId and returns that data. If there's an error e.g. the userId doesn't exist in the database, it returns an error message.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_6a7b8c9d)

---

## Data tier

Now we will setup the data tier by creating a dynamoDB table and integrating it into other parts of our web app

The partition key is the unique identifier for all data that will be saved in the table

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_u1v2w3x4)

---

## Logic and Data tier

Now, it's time to connect them. We'll update our index.html file to make a request to our API Gateway endpoint and display the returned data.

Update our script.js file with JavaScript code to make an API request and Verify that the data is displayed on your website.

To test our API, we use the invoke url and append the \/users?userId=1 at the end of it to fetch just the details of the userId 1 row from our table

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_a112c3d5)

---

## Console Errors

The error is because the JS file of the web page has no link to our API invoke url. 

To resolve the error, we updated the hs file with our API invoke url and then reuploading to S3 which will automatically link with the cloudfront and should clear up the error

The CORS (Cross-Origin Resource Sharing) error you're encountering happens because your API Gateway is not configured to allow requests from your CloudFront URL.

API Gateway is only allowing requests directly from its Invoke URL!

To resolve this, you'll need to enable CORS on your API Gateway so that it can accept requests from the domain where your frontend is hosted.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_a1b2c3d5)

---

## Resolving CORS Errors

To resolve this, you'll need to enable CORS on your API Gateway so that it can accept requests from the domain where your frontend is hosted.

I also updated the Access-Control-Allow-Origin in our lambda code to the specific cloudfront link so that it allows any request from the weblink

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_1qthryj2)

---

## Fixed Solution

I verfied the connection between the API and cloudfront by opening the link and seeing if it fetches the data for userid 1.

![Image](http://learn.nextwork.org/motivated_lavender_quiet_boto/uploads/aws-compute-threetier_2b3c4d5e)

---

---
