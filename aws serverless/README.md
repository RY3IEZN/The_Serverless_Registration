<!-- @format -->

# The Serverless registration form

![](/aws%20serverless/images/serverlessaws.JPG)

In this project, we will create a simple and basic serverless application, it takes a the registration data and uses lambda to update the table in aws dynamodb.

Here are the steps

1. Create DynamoDb Table
2. Create Lambda function with the code and IAM role
3. Create api gateway
4. Test the application
5. Clean up the resources

Nb. This is for test purpose to just get familiar with setting up serverless compute

# 1. Create DynamoDb Table

Login in to the aws console, on the dashboard on the top left search for dynamodb and select it, it will navigate to the dynamodb page and then click create table

![](/aws%20serverless/images/dynamodb1.png)

ensure to fill in the table name and partition key as both are required and cannot be left empty

![](/aws%20serverless/images/dynamodb2.png)

For now, we will leave the table settings as default

![](/aws%20serverless/images/dynamodb3.png)

As usual dont forget to tag your resources, then you can click create

![](/aws%20serverless/images/dynamodb4.png)

Great, we have our dynamodb table setup.

![](/aws%20serverless/images/dynamodb5.png)

# 2a. Create Lambda function IAM role

we will create the IAM role, on the dashboard on the top left search for IAM and select it, it will navigate to the IAM page

![](/aws%20serverless/images/iam1.png)

Click on "roles" on the left and then "create role" on the right

![](/aws%20serverless/images/iam2.png)

set the select trusted identity to "aws service" and set the "use case" to lambda and then click next

![](/aws%20serverless/images/iam3.png)

here we are going to attach 2 permissions

1. DynamodbFullAccess (to crud the db)

![](/aws%20serverless/images/iam4a.png)

2. CloudWatchFullAcess (to store the logs)

![](/aws%20serverless/images/iam4b.png)

hint: you can set both permissions before navigating to the next page at which you can put the name of the role

![](/aws%20serverless/images/iam5.png)

verify the 2 permissions has been added

![](/aws%20serverless/images/iam6.png)

As usual dont forget to tag your resources, then you can click create

![](/aws%20serverless/images/iam7.png).

then you should now see the role in the iam dashboard

![](/aws%20serverless/images/iam8.png).

we can now procced to write some code

# 2b. Create Lambda function code

we will create a Lambda, on the dashboard on the top left search for Lambda and select it, it will navigate to the Lambda page and cloick create a fucntion

![](/aws%20serverless/images/lam1.png)

on the next page we will author the lambda code from scratch, input the function name, set the runtime to python v3.9 and leave the architechure as x86.

![](/aws%20serverless/images/lam2.png)

add the roles we created earlier to the permissions

![](/aws%20serverless/images/lam3.png)

As usual dont forget to tag your resources, click on advanced enable tags, fill in the tags then you can click create

![](/aws%20serverless/images/lam4.png)

create and we should have our function

![](/aws%20serverless/images/lam5.png)

almost done, we can add our sample code,test&deploy

![](/aws%20serverless/images/lam6.png)

side test. i did a quick test here from the console and it shows its works, i updated the json with sample details.

![](/aws%20serverless/images/lam7.png)

check outcome

![](/aws%20serverless/images/lam8.png)

and at the db

![](/aws%20serverless/images/lam9.png)

next api gateway.

# 3. Create Api Gateway

we will create an api gateway, on the dashboard on the top left search for api gateway and select it, it will navigate to the api gateway page and click create

![](/aws%20serverless/images/apigw1.png).

for this project we will use REST Api go ahead and click build

![](/aws%20serverless/images/apigw2.png).

we will authur our api from scratch so click the rest protocol, select rest api, input the name and description and set the endpoint type to "regional"

![](/aws%20serverless/images/apigw3.png).

# 5. Clean up

So far we created 3 resources api gateway,lambda and dynamodb... go to the console page of each resource that was create and click delete on the top right.
