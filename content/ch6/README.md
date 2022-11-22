# Configuration Management
Managing IT system configurations involves defining a system's desired state—like server configuration—then building and maintaining those systems. Closely related to configuration assessments and drift analyses, configuration management uses both to identify systems to update, reconfigure, or patch.

Using Configuration Management is imperative in DevOps infrastructures. Remember, DevOps is about facilitating speed, accuracy, and efficiency. Configuration Management helps to automate mundane maintenance tasks, which frees up dev time for actual programming. This increases agility, both on the part of individual devs and the organization as a whole. At this point, it would be correct to state that Configuration Management is fundamentally necessary for setting up a DevOps-driven framework.
## What is Configuration Management?
Configuration management is a process for maintaining computer systems, servers, and software in a desired, consistent state. It’s a way to make sure that a system performs as it’s expected to as changes are made over time. 

An important function of configuration management is defining the state of each system. By orchestrating these processes with a platform, organizations can ensure consistency across integrated systems and increase efficiency. The result is that businesses can scale more readily without hiring additional IT management staff. Companies that otherwise wouldn’t have the resources can grow by deploying a DevOps approach.

Configuration management is closely associated with change management, and as a result, the two terms are sometimes confused. Configuration management is most readily described as the automation, management, and maintenance of configurations at each state, while change management is the process by which configurations are redefined and changed to meet the conditions of new needs and dynamic circumstances.

## Why is important to use a Configuration Management strategy in a project
Misconfigurations can lead to poor performance, inconsistencies, or noncompliance and negatively impact business operations and security. When undocumented changes are made across many systems and applications, it adds to instability and downtime.

In a traditional sysadmin world, usually, the configuration of servers (everything the server needs to work) are managed either manually or by a bunch of scripts that automate some processes. Imagine if one of those servers fails, our instinct would tell us to log in to that server, enter some commands, maybe change some configurations files, press some buttons or change one of those bash scripts we wrote. Great! the server is running again and now you can go home. Now imagine if you keep doing the same over and over; in the end, you will end up with a bunch of servers that everyone fears to touch because no one really knows how it works or how it’s configured. Also, you’ll find yourself making backups of those servers very often. That’s what we call Snowflake servers and we should do whatever it takes to prevent that to happen.

Fortunately, exists some tools that will help you to manage the configuration of your servers in an easier and more efficient way. Most of those tools will let you express the desired state of the system instead of a series of instructions or to achieve that state. The tool will do the necessary steps to convert the system from its current state to the state you specified.
### Proper configuration management tools:

* Classify and manage systems by groups and subgroups. 
* Centrally modify base configurations.
* Roll out new settings to all applicable systems. 
* Automate system identification, patches, and updates
* Identify outdated, poor performing, and noncompliant configurations. 
* Prioritize actions. 
* Access and apply prescriptive remediation.
## Benefits
Think of it like this. If you keep up with the small things, you can avoid more complicated, expensive repairs in the future. Configuration management is about preventing issues so you don’t have to deal with as many problems later. 

For example, you can make sure that your test and production environments match. That way, you’ll have fewer problems with applications once they’ve been deployed than you would if these environments weren’t exactly the same.

With configuration management, you can accurately replicate an environment with the correct configurations and software because you know what exists in the original environment.

* Reduces risk of unpredictable system failures and data breaches because it offers perfect visibility and tracks every change made to test environments.
* By offering detailed knowledge of all configurational elements, it reduces costs by lowering the possibility of duplicating technological assets.
* Offers greater agility and better resolution of issues by making it easy for personnel to view changes (unforeseen or otherwise) that may have led to said problems.
* Implement faster restoration of services. This is because the configuration, including all changes, is automated and documented. Not only is it easier to detect the problem, but it is easier to revert the failing environment to its last functional stage.
* Offers greater control over relevant workflows by establishing and enforcing formalized policies and procedures for status monitoring, asset detection, audition, change implementation, etc.
## Configuration Management Tools
Through automation, a configuration management tool can provision a new server within minutes with less room for error. You can also use automation to maintain a server in the desired state, such as your standard operating environment (SOE), without the provisioning scripts needed previously.

Most configuration management tools use a controller/master and node/agent model. Essentially, the controller directs the configuration of the nodes, based on a series of instructions or tasks defined in your provisioning scripts.

Every configuration management tool will have a machine where the configuration data is stored and some machines (nodes) whose configuration needs to be maintained. How the nodes get configuration from the main server depends on the type of configuration management tool used. There are two type **Pull Based** and **Push Based**.

### Pull Based
In this type of configuration management tool, the nodes pull the configuration information from the server (hence, the name).

A small software (called agent or client) is installed on every node. 
This agent/client will:

* at regular intervals, get the configuration from the server
*compare the configuration received from the server with the current configuration of the node
* if there is any mis-match, take the steps required to match the configuration of the node with the configuration received from the server.

This means that, its always the agent/client that initiates communication, not the main server.

Chef & Puppet are good examples of such configuration management tools.
### Push Based
In this type of configuration management tool, the main server (where the configuration data is stored) pushes the configuration to the node (hence, the name). So, it is the main server that initiates communication, not the nodes. Which means that an agent/client may or may not be installed on each node.

Ansible is an example of a push based configuration management tool that doesn’t need an agent to be installed on the nodes. 

### Chef
chef is basically an automation platform that provides a way to configure and manage infrastructure. Infrastructure as code implies executing by coding rather than doing manual execution. The chef works on Ruby and DSL for writing the configurations.
Chef follows the Push model and allows cloud adoption.
Chef uses "recipes" written in Ruby to keep your infrastructure running up-to-date and compliant. The recipes describe a series of resources that should be in a particular state. Chef can run in client/server mode or in a standalone configuration named chef-solo. It has good integration with the major cloud providers to automatically provision and configure new machines.

Chef has a solid user base and provides a full toolset to allow people with different technical backgrounds and skills to interact around the recipes. But, at its base, it is more technically oriented tool.
### Ansible
Ansible is a push-based configuration tool. It helps to automate the entire IT infrastructure by providing large productivity gains. Ansible generally connects through SSH, remote PowerShell or via other remote APIs. It is agentless what it means no need for agent installation and management.
Because agents are not required, there is less overhead on servers. An SSH connection is necessary when running in push mode (which is the default), but pull mode is available if needed. Playbooks can be written with a minimal set of commands or they can be scaled for more elaborate automation tasks that could include roles, variables, and modules written by other people.

You can combine Ansible with other tools to create a central console to control processes. Those tools include Ansible Works (AWX), Jenkins, RunDeck, and ARA, which offers traceability when running playbooks.
### Puppet
Puppet is an open-source software configuration management tool. It is used for deploying, configuring and managing servers. It uses a master-slave architecture so configurations are pulled from the master by the nodes. Puppet provides Intuitional web UI to handle multiple tasks, which includes reporting and real-time node management.
Puppet uses a declarative language or Ruby to describe the system configuration. It is organized in modules, and manifest files contain the desired-state goals to keep everything as required. Puppet uses the push model by default, and the pull model can be configured.

We really suggest you to check this video for more information and this website with information about different tools
* https://www.youtube.com/watch?v=_TVNCTK808I&t=715s&ab_channel=Simplilearn
* https://www.softwaretestinghelp.com/top-5-software-configuration-management-tools/ 

## Best Practices
### Automate Deployments
Many problems can arise with manual deployments, resulting in lengthy, expensive fixes to poor-quality software. Introducing automation can reduce the risk of human error, increase communication in the workplace, and introduce security checks into the build. All in all, automation helps organizations get high-quality software to production, faster.

Automating deployment practices can be a daunting task, especially for organizations working with legacy applications. However, automation can and should be added into the software delivery lifecycle.  
### Create standards
For optimal network consistency, it is recommended that the following standards be created: software version control and management, IP addressing standards and management, configuration upgrade procedures, and solution templates.
### Maintain documentation 
Documenting network changes that have occurred in real-time is important in order to make troubleshooting, inventory, validation, and audits more efficient.
### Configuration integrity checks 
By routinely checking the integrity of configurations, any potential problems (such as duplicate IP addresses or protocol mismatches) can be identified and manually reviewed.
### Configuration upgrade procedures
Upgrade procedures help ensure that hardware and software upgrades occur smoothly and with minimal downtime. Upgrade procedures include vendor installation references, testing requirements, and configuration guidelines.
### Configuration version control system
Keeping a configuration version control system is helpful for comparing current running configuration to previously working versions to identify where problems occur.
## Challenges
*  Choose a SCM Tool to use in the project: Each tool has its advantages and disadvantages so, explain why you made that decision.
* Just like the Scripting challenge, create the code to provision your instance with everything the app needs to work but, in this case, using the tool you chose.
* Remember that your instances are now in the cloud and they should be disposable, meaning you should be able to destroy and recreate them anytime you want. Your implementation needs to able to detect if a new instance was created and configure it accordingly.
* Try to provision the servers from your local machine.
## References
* https://www.redhat.com/en/topics/automation/what-is-configuration-management
* https://www.digitalocean.com/community/tutorials/an-introduction-to-configuration-management
* https://www.bmc.com/blogs/devops-configuration-management/
* https://opensource.com/article/18/12/configuration-management-tools
* https://www.softwaretestinghelp.com/top-5-software-configuration-management-tools/
* https://blog.inedo.com/configuration-management-best-practices
