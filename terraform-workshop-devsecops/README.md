# TerraOak.workshops Users-API 

As API’s are prevalent in today’s world to ensure rapid product feature, lets talk about how we can secure them during the SDLC.  Lets take a simple use-case of  Company X who has decided that they want to build out an simple Users API.  The users api will be able to get and set a user using Api-Gateway, lambda, DynamoDB and S3.  As we embark on this journey, we will build out terraform code using Terraform Cloud, learn about design gaps we encounter using run-tasks and also apply a fix to secure our design gaps to ensure we  create a “secure by design reference architecture”.  We will also fulfil all of the compliance frameworks that Company X has to adhere to creating a very mature devsecops pipeline for the future. 

## Table of Contents

* [Prerequistes Start Here](https://learn.oak9.io/workshops/terraform-cloud)


## Introduction 

Before you proceed, WARNING:
> :warning: terraOak.workshops is a test repo for creating Vulnerable resources, please use at your own discrention, Oak9 is not responsible for any damages. **DO NOT deploy TerraOak in a production environment or any AWS accounts that contain sensitive information.**

## Scenario

Lets Build a Users API using the below resources and secure using Oak9. 

* s3
* dyanmodb
* api-gateway
* lambda 

## Architecture Diagram

<figure><img src="workshop.png" alt=""></figure>

## Terraform Code 

The code in this repo should not be run inside of your company's aws accounts but rather in a playground account.   

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 4.55.0 |


* Ensure your create your backend bucket and table for terraform state file. This config will need to reside in a .tf file in the root directory. 

https://www.terraform.io/language/settings/backends/s3

## Getting Started Terraform Code Execution

* Download github code locally 
* Ensure requirements are met 
* Run terraform init 
* Run terraform plan/apply 
* Add a api user with following command 


# without token (POST)
`curl -X POST "$(terraform output -raw base_url)/set-user?id=0&name=john&orgid=xyx&plan=enterprise&orgname=xyzdfd&creationdate=82322"`

`curl "$(terraform output -raw base_url)/get-user?id=0"`

# with token (GET)
`curl -X POST "$(terraform output -raw base_url)/set-user?id=0&name=john&orgid=xyx&plan=enterprise&orgname=xyzdfd&creationdate=82322 -H "authorizationToken: allow"`

`curl "$(terraform output -raw base_url)/get-user?id=0" -H "authorizationToken: allow"`




 
