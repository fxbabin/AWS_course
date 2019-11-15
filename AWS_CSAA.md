# AWS Certified Solutions Architect Associate (CSAA)

1. [Introduction](#intro)
    1. [Cloud](#intro-cloud)
    2. [AWS](#intro-aws)
2. [AWS Account](#account)
    1. [Account creation](#account-creation)
    2. [Console](#account-console)
    3. [Billing Alarm](#account-billing)
3. [Identity and Access Management (IAM)](#iam)
3. [end](#iam)

<div id='intro'/></div>

# Introduction

<div id='intro-cloud'/></div>

## Cloud Computing

Cloud computing is the on-demand delivery of IT resources and applications via the Internet
with pay-as-you-go pricing. In reality, a cloud server is in a data center all around the world.

<p align="center">
<img src="AWS_CSAA_imgs/cloud_computer.png" width="300">
</p>

Whether you run applications that share photos to millions of
mobile users or deliver services that support the critical operations of your business, the
cloud provides rapid access to flexible and low-cost IT resources. With cloud computing, you
don’t need to make large up-front investments in hardware and spend a lot of time managing
that hardware. Instead, you can provision exactly the right type and size of computing
resources you need to power your newest bright idea or operate your IT department. With
cloud computing, you can access as many resources as you need, almost instantly, and only
pay for what you use.

In its simplest form, cloud computing provides an easy way to access servers, storage,
databases, and a broad set of application services over the Internet. Cloud computing
providers such as AWS own and maintain the network-connected hardware required for these
application services, while you provision and use what you need for your workloads.

### Example

For a company if they are using their own servers, they have an architecture on premise.

If the company has 1000 users in 2016 and 2000 users in 2017 then some other servers will be needed. In the future the company might also want to install servers in order to anticipate the future number of user. If you use an architecture on premise and have less users than you thought some of the servers you bought are becoming useless.

<p align="center">
<img src="AWS_CSAA_imgs/onpremise_archi.png" width="450">
</p>

Whereas using the cloud, the infrastructure can be scaled to fit the need of the company.

<p align="center">
<img src="AWS_CSAA_imgs/cloud_archi.png" width="450">
</p>

As seen previously, Cloud computing has some real benefits :
* **variable expense** : we don't need to invest in huge data centers you may not use. You pay for how much you consume !
* **available in minutes** : new IT ressources can be accessed within minutes.
* **economies of scale** : because of the number of users. Cloud providers can achieve higher economies of scale translating in lower prices.
* **global in minutes** : cloud architectures can be deployed really easily all around the world.

Deployments using the cloud can be `all-in-cloud-based` (the entire infrastructure is in the cloud) or `hybrid` (using on premise and cloud).

<div id='intro-aws'/></div>

## Amazon Web Services (AWS)

Amazon Web Service (AWS) is a cloud service provider, also known as infrastructure as a service (`IaaS`). AWS is the clear market leader in this domain and offers many services compared to other cloud providers.

AWS has some interesting proporties as :
* **High availability** : Any file can be accessed from anywhere
* **Fault tolerance** : If an AWS server fails. You can still retrieve the file (the fault tolerancy is due to redundancy)
* **Scalibility** : Possibility to add more servers when needed
* **Elasticity** : Possibility to grow or shrink infrastructure

### Global Infrastructure

AWS provides a highly available technology infrastructure platform with multiple locations
worldwide. These locations are composed of `regions` and `availability zones`. 

Each region is a separate geographic area. Each region has multiple, isolated locations known as availability zones. An availibity zone is a physical data center geographically seperated from other availibility zones.

<p align="center">
<img src="AWS_CSAA_imgs/aws_regions.png" width="300">
</p>

We can achieve high availability by deploying your application across multiple availability zones. 

### Security

The AWS infrastructure has been designed to provide the highest availability while putting strong safeguards in place regarding customer privacy and segregation. When deploying systems on the AWS Cloud computing platform, AWS helps by sharing the security
responsibilities with the organization. AWS manages the underlying infrastructure, and the organization can secure anything it deploys on AWS. This affords each organization the
flexibility and agility they need in security controls.

### Compliance

When customers move their production workloads to the AWS Cloud both parties become responsible for managing the IT environment. Customers are responsible for setting up their
environment in a secure and controlled manner. Customers also need to maintain adequate governance over their entire IT control environment.

Organizations retain complete control and ownership over the region in which their data is physically located, allowing them to meet regional compliance and data residency requirements.

<div id='account'/></div>

# AWS Account

<div id='account-creation'/></div>

## AWS account creation

When we create a new account on AWS, we have an AWS Free Tier. It allows us to use some of AWS ressources for free each month during one year.

In order to create an AWS account, we must go to the following address [aws.amazon.com](aws.amazon.com).

Then we click on the create an account button and fill the following form.

<p align="center">
<img src="AWS_CSAA_imgs/account_2.png" width="400">
</p>

We choose a `personnal` account type and fill the rest of the forms.

<p align="center">
<img src="AWS_CSAA_imgs/account_3.png" width="300">
<img src="AWS_CSAA_imgs/account_4.png" width="300">
</p>

Then we choose the `basic plan`, which is free.

To connect to aws we use our email and password. We will then access to your root account. The root account must not be used directly when using AWS ressources for security purposes. We will later create IAM users to use AWS ressources more safely.

<div id='account-console'/></div>

## AWS console

The console allows to search for specific services. by default they are sorted by group but can be sorted alphabetically.

<p align="center">
<img src="AWS_CSAA_imgs/console.png" width="400">
</p>

We notice there is a link for ressource group. Ressource groups allow us to take a collection of aws ressources and assign a tag (a label) to them so we can manage them as a group.

The pushpin is for one-click navigation. It allows us to create shortcuts for most commonly used ressources.

<p align="center">
<img src="AWS_CSAA_imgs/pushpin.png" width="400">
</p>

The alarm icon allows us to see all system alerts. If we click we will see more details about the issues and their current status.

<p align="center">
<img src="AWS_CSAA_imgs/alerts.png" width="150">
</p>

Then we have account information and the selected AWS regions we are working on (all ressources are not available for every regions).

Support center allows us to create cases when we encounter problems (we can see support plan here, which will influence aws response time).

<div id='account-billing'/></div>

## Creating a billing Alarm

We first type `billing` into aws search services bar. 

<p align="center">
<img src="AWS_CSAA_imgs/billing.png" width="400">
</p>

Then we can go in `Billing preferences` section and validate `Receive Free Tier Usage Alerts` (we have to enter an email). We can also set `Receive Billing Alerts` then we have to save preferences. We can now receive billing alerts !

Now we need to go CloudWatch to configure a billing alert. Cloudwatch is the AWS monitoring system use to track performances of used AWS ressources.

We go into `CloudWatch` section. We go into the `Alarm/Billing` subsection. Then we can `create alarm`. 

<p align="center">
<img src="AWS_CSAA_imgs/account_alarm.png" width="500">
</p>

We have to `select metric`. Two types of metric exists : `by service` or `Total estimated charges`. We are going to select `Total estimated charges` and `USD` as currency. The threshold we want is `static` and `greater or equal` to 1 $.

<p align="center">
<img src="AWS_CSAA_imgs/account_alarm_cond.png" width="500">
</p>

On the configure actions page. we are going to keep `in alarm`. For the notification we use SNS (Simple Notification Service). We are going to `create a new topic` with the name "BillingAlarm" and we need to enter to enter our email address. Then we can create the SNS topic.

For the SNS topic to work, we need to confirm our email address (confirmation in the AWS email).

Then we can select `select an existing SNS topic` with "BillingAlarm".

We can then add the name and the description of the alarm. Our alarm is finally created !

<p align="center">
<img src="AWS_CSAA_imgs/billing_alarm_created.png" width="500">
</p>


<div id='iam'/></div>

# Identity and Access Management (IAM)






