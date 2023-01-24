# Infrastructure as Code (IaC)

Now that we know what Cloud Computing is, we can start talking about Infrastructure as Code, which is very related to Cloud Computing because of the
management of computing resources on the cloud. Let's talk about a situation that could happen in our jobs as we did on the previous chapter.

Let's say that you have been assigned to a project as a Cloud Engineer because you're an expert on the cloud now, right? they ask you to design
a full infrastructure for running a microservice application just as we did before, but you need to do it for different environments such as one
environment for development, one for testing and one for production. Also, you need to make different ASG per microservice, all of these things 
manually... it doesn't look good, right? there's going to be a lot of items created that you'll need to maintain and monitor, there's a lot of room 
for human mistakes, it will be difficult to track changes on the infrastructure, etc. We can simplify all these tasks a lot with code, here's where 
**Infrastructure as Code** enters the game.

## What is Infrastructure as Code?

As its name says, Infrastructure as Code allows you to manage and prepare infrastructure through code using configuration files instead of doing it 
manually through a graphical user interface, you can build, change and manage your infrastructure in a safe, consistent and repeatable way defining
resource configurations that you can version, reuse and share.

By versioning your infrastructure configuration files you can distribute resource configurations more easily for collaborating and tracking the changes made to it. This will also help to track and fix errors on the infrastructure or wrong placed resources, you can revert your infrastructure to a previous state, standardize your infrastructure creation and even your deployment workflow. IaC allows you to guarantee that you can always prepare the same environment everytime you want to create it or replicate it, you can easily provide documentation for your infrastructure and erase all the resources you created automatically.

**Advantages**

* Allows you to manage IT infrastructure needs while improving consistency
* Reduce mistakes
* Reduce efforts on manual configuration
* Reduce costs
* Improves implementation speed
* Improves infrastructure consistency
* Avoid configuration mismatches 

**Disadvantages**

* Higher learning curve
* You need to learn how to use a tool for working with IaC, each tool may work differently. We recommend you to use **Cloud Agnostic** tools
* It's difficult to collaborate on IaC
    Taking for example Terraform, once you build your infrastructure you have a state file that you could share in order to work together with other
    people. The problem here is that once the infrastructure is created, you need to be careful of each action anyone will do on the infrastructure, 
    you can't create it while your partner is creating it, or modifying it, or erasing it, because there is only one status per infrastructure.

### IaC Tools

* **Chef (configuration management and IaC tool)**
* **Puppet (configuration management and IaC tool)**
* **Ansible (configuration management and IaC tool)**
* **Saltstack (configuration management and IaC tool)**
* **Terraform (IaC tool)**
* **AWS CloudFormation (IaC tool)**
* **CDK (IaC tool)**
* **Pulumi (Iac tool)**

## IaC Best Practices

As we are working with code now, there's a set of best practices that you can apply to your IaC scripts. Here we'll see some of them, but keep learning!
there'll be always room for improving your way of doing things!

* **Make your infrastructure immutable**: This is essential, after your infrastructure is deployed and created, it shouldn't be modified by any reason, this
will avoid configuration drift and improve tracking of errors, if something doesn't work on your infrastructure, it means that something is wrong with your
scripts, and not because someone changed the configuration you established in your IaC scripts.

* **Start versioning your IaC Scripts**: Just as any application, you should add your IaC scripts to a VCS and take advantage of all its benefits.

* **Add modularity in your Infrastructure design**: Similar to microservices in application design, you can implement your Infrastructure divided on modules
that will represent a section of your Infrastructure, for instance:
  * A module that will create the prerequisites required for creating an ASG, this would be: Launch template, Load balancer, target groups, etc.
  * A module that will create the ASG and needs to run after the previous module.
  * A module that will create your database with Amazon RDS.
  * A module that will create a single instance for running and provisioning your Ansible's control node.
This will help you keep things more organized, finding where something is failing and dividing your work on implementing your IaC Scripts.

* **Add tests to your IaC scripts!**: Yep! you read that right! you can create tests for your Infrastructure just as you could do to any application, that
would allow you to find errors earlier on your development lifecycle and ensuring that your IaC also has high quality standards, a quality application is
useless if you don't have a quality infrastructure.

* **Don't hard-code secrets in your scripts!**: Be really careful with this, it happens all the time and it's a really bad practice and a big security
flaw, because it facilitates attackers to steal your passwords and attack your infrastructure and your applications compromising user's information.
Instead of hard-coding secrets, use a secure secret storage service, here you can check some examples of this kind of services:
  * GitHub Encrypted Secrets: https://docs.github.com/en/enterprise-cloud@latest/actions/security-guides/encrypted-secrets
  * AWS Secrets Manager: https://aws.amazon.com/es/secrets-manager/
  * Microsoft Azure's Key Vault: https://azure.microsoft.com/es-es/services/key-vault/

## Why is IaC Important for DevOps?

As you may know, one of the most important parts of the DevOps Culture is the implementation of Continuous Integration (CI) and Continuous Delivery (CD).  Cloud plays a major role on these processes. Mainly on CD, you have to deploy your applications somewhere, as we discussed on the previous chapter you
will deploy applications on a Cloud platform instance, these instances have to be already created before you deploy an application to them, thanks to
IaC, you don't need to wait for these instances to be created in order to start deploying your applications, you can trigger their creation on the 
same deployment, and erase them once they're not required. Also, in order to reduce the occurrence of bugs, you have to ensure that all environments are
the same, including production. You'll need to execute the same implementation process on each environment in order to do this, the best way to achieve
uniformity on all environments is using IaC.

## Challenges

Let's get to work! in this challenge you'll do the same things we did on the previous chapter, but using IaC:

1. **Choose an IaC tool**: we saw some tools for doing IaC on this chapter. Read about them, see their pros and cons and choose the one that you like the most!
We recommend using Terraform if you can't decide on any tool.
2. **Implement all your Infrastructure as code**: create your scripts that will set up all your infrastructure just as you did manually on the previous
chapter! you should be able to create and destroy your infrastructure using a single (or a couple of) command(s), don't forget to apply the best
practices seen here!
3. **Use a VCS for storing your IaC**: just as you'll do with any other code, upload your scripts to a VCS in order to keep track of your code versions.
4. **Test your Infrastructure's High Availability**: remember, we want to set up a High Availability infrastructure, make sure that everything is working ok!