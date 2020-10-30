+++
title = "d. Create the serverless function"
date = 2019-09-18T10:46:30-04:00
weight = 150
tags = ["tutorial", "serverless", "ParallelCluster", "Lambda", "Slurm"]
+++


Serverless functions, such as AWS Lambda, allow you to run code without provisioning or managing servers. It can be particularly useful to automate tasks or an infrastructure. In the present case we will use our Lambda function to interpret the HTTP requests received by API gateway into Slurm command and execute them on our cluster through a secure channel provided by AWS Systems Manager (SSM). This avoid the need for our cluster to be exposed to the end users. If we were to add a new cluster or use a different scheduler, users could connect with the same interface with all the logic being managed through Lambda.

In this section we will create our first Serverless function, in the next section we will add the code of our function, then we will create an IAM Role and attach it to our function to allow it to connect to the cluster and access the bucket we created earlier.

1. First open the AWS Management Console, in **Services**, select **Lambda**. You can use the **Search** field as well.

2. Click on **Create function**.

![Lambda Create Function](/images/serverless/lambda-create.png)

3. Leave all default settings except for the field **Function name** were you can enter **SlurmFrontEnd** and the field **Runtime**, choose **Python 3.8**.

4. Once done click on **Create function** to create it.

![Lambda Create Function](/images/serverless/lambda-create2.png)

You will be presented with an overview of your function and its different settings. In this panel. You can use it to configure which services or API call can trigger your function, layers to embed 3rd party libraries that your function may call, and destinations which in your case will be SSM.

![Lambda Create Function](/images/serverless/lambda-create3.png)

Let's now go to the next section and add some code to our function.




{{% notice tip %}}
If you would like to dive deeper on AWS Lambda, please visit [this page](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html).{{% /notice %}}