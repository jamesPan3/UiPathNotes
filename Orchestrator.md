# Orchestrator
## What is Orchestrator?
Orchestrator is the component of UiPath Suite through which the automation workflows developed in Studio are published, assigned to robots and executed. It comes in the form of a web application that enables the management of robots, activity packages, data to be processed, execution schedules, as well as other assets.

Orchestrator is ideal for large deployments of robots covering complex processes, but it can also be deployed in scenarios dealing with short and repetitive processes and fewer robots.

## What are Orchestrator's capabilities?
- **Provisioning** - creates and maintains the connection with the robots.
- **Deployment** - ensures the delivery of the workflows for execution, either immediately or using schedules.
- **Configuration** - enables the creation, configuration and maintenance of groups of robots and the execution of tasks.
- **Queues** - the data that needs to be processed is broken down to indivisible operations called transactions. Queues can store any number of transactions and they facilitate their distribution, execution and monitoring.
- **Monitoring** - keeps track of robot identification data and maintains user permissions.
- **Logging** - stores and indexes the logs to an SQL database and/or ElasticSearch.
- **Inter-connectivity** - acts as the centralized point of communication for 3rd party solutions or applications, and can be used for storing activity packages, libraries and other assets (such as credentials).

## What are the benefits of Orchestrator?
As you know, workflows can be executed on a local machine to perform simple tasks. In business contexts though, all the capabilities listed in the previous section are needed for effectively managing a large number of robots that have to execute numerous tasks. All these capabilities translate into tangible benefits, such as:
- **Accessibility and version control** - Workflows can be published as packages and stored in Orchestrator, at version level and with the developer's release notes. Different versions can be distributed to robots for execution. Libraries can also be published and stored in Orchestrator. From there, they can be accessed at any time, used in development and distributed to robots. 
- **Transactional processing** - Queues allow efficient allocation of the workload between robots, continuous execution and monitoring at transaction level.  If a certain transaction in the queue cannot be executed for certain reasons, it won't stop or delay the overall execution.
- **Efficient planning and execution** - Orchestrator allows execution of tasks according to schedules that can accommodate various scenarios (like non-working days), to choose execution targets from the available robots and even to create continuous execution loops even outside business hours.
- **Securely storing assets** - As a good practice, configuration assets, credentials and data that change frequently must not be stored in the workflows. Orchestrator provides a secure way of storing assets and distributing them to robots according to different scenarios.
- **Monitoring** - Robots, processes and task execution can be monitored via Orchestrator, which can enable quick reaction in case of any error, and also provides the means for accurate reporting and auditing of the robot work.

# Orchestrator Key Concepts
- **Robot** - The Robot is UiPath’s execution agent that enables you to run workflows built in Studio. It can be of several types.
- **Environment** - An environment is a group of robots configured in Orchestrator. Processes can be allocated to individual robots, but it's more effective to allocate them to environments. A robot can be part of more than one environment, provided they are in the same service.
- **Organization Unit** - In general, it is an entity in Orchestrator that corresponds to a business unit. The same Orchestrator instance can have multiple organization units configured, each of them having separate robots, environments, queues, assets and so on. The Community Edition plan won't allow the creation of other organization units than the default one created.
- **Package** - A project developed in UiPath Studio that is published to Orchestrator. Multiple versions of the same project can be stored and used.
- **Process** - It is a package that has been allocated to a certain environment.
- **Job** - A job is a process that has been sent for execution to some or all of the robots in the environment.
- **Schedule** - A process that is configured for an execution that is not immediate, but according to a schedule. Multiple configurations are possible when it comes to schedules.
- **Asset** - An asset is a piece of data stored in Orchestrator for the use of robots. There are four types of assets:
    - **Text** - stores only strings (it is not required to add quotation marks);
    - **Bool** - supports true or false values;
    - **Integer** - stores only whole numbers;
    - **Credential** - contains usernames and passwords that the Robot requires to execute particular processes, such as login details for ERP systems.
- **Queue** - A queue is a sequence of transactions that is built in Orchestrator, and then used to dispatch to robots for processing.

# Robots and Environments in Orchestrator
## What is a robot?
The robot is UiPath’s execution agent that enables you to run workflows built in Studio. The installation of the Studio comes with a robot that is triggered when the 'Run' button is clicked when a project is open.

Provisioning robots in Orchestrator allows better package distribution capabilities, better scheduling, and enables the use of assets and queues. All these will take an implementation much closer to a business context. 

## Types of robots
Before covering robot provisioning, let's spend some time to talk about the types of robots that UiPath offers.

Based on how they can be used, there are 4 types of robots: 
- **Attended Robot** - This type of Robot is triggered by user events, and operates alongside a human, on the same workstation. Attended Robots are used with Orchestrator for a centralized process deployment and logging medium.
- **Unattended Robot** - Robots run unattended in virtual environments and execute any number of processes. On top of the Attended Robot capabilities, Orchestrator covers execution, monitoring, scheduling and providing support for work queues.
- **Development Robot** - Has the features of an Unattended Robot, but it should be used only to connect Studio to Orchestrator, for development purposes.
- **Non-Production Robot** - Similar to Unattended Robots, but they should be used only for development and testing purposes.

### According to the Robot/Machine interaction, there are two kinds of robots:
- **Standard Robot** - Works on a single Standard Machine only. It is a good choice when the machine on which the robot runs is known and will never change.
- **Floating Robot** - Works on any machine defined in Orchestrator. It is a good choice when human users work in shifts on the same machine or on different machines, and when virtual machines are being regenerated often.

## Provisioning robots in Orchestrator
In order for robots to perform jobs, they have to be provisioned in Orchestrator, together with the machines that they will be using. It is important to remember that the machine name is mandatory for standard robots, and login credentials may be needed for unattended robots. Only the Orchestrator admins have rights to provision robots and machines.

Robots can be connected:
- Directly from the Orchestrator Settings window
- From the Command Line
- Or automatically enrolled

Usually, it is recommended to first try and connect the robot from the Orchestrator window. If issues are encountered when doing so, the next step would be to perform the connection from the Command Line.

## Environments
An environment is a grouping of Robots, that is used to deploy processes. The dedicated tab in the Robots menu can be used to create, modify and delete environments. 

A robot can be added in more than one environment, provided that they are under the same service.

In a real scenario, the Finance service could create environments at business unit level (Accounts Payable, Accounts Receivable), at application level (SAP, electronic banking, settlement application) or sub-process. It is very important to remember that services have the robots, environments, queues, processes and so on totally separated.

# Process Execution in Orchestrator
## Packages
Packages consist of one or more automation workflows published from Studio. They can be published on the local machine or directly to the Orchestrator. Similarly, in Orchestrator, packages can be manually uploaded.

In Orchestrator, versions of the same package are stored automatically. The version and release notes can be accessed anytime by selecting Processes from the menu on the left in Orchestrator, and navigating to the Packages tab.

Package versions can be active or inactive:
- active: deployed to at least an environment;
- inactive: not deployed (this type can be deleted).

Packages can easily be updated following the same steps as for publishing. It will be automatically detected that it's a new version of an existing package.

## Processes
A process represents the association between a package and an environment. Processes can be accessed from the menu on the left. In order to create a new Process, simply click on the '+', select a package available in Orchestrator, select the environment and give it a description.

If the Main.xaml of the process has In, Out, or In/Out arguments, they are displayed on the Parameters tab of the View Processes window. In Orchestrator, they become input and output parameters and they can be configured from the Parameters tab.

# Jobs and Schedules
Once a process is created, its execution can be triggered. There are 3 ways to do it:

## Using Jobs (immediately)
To start a job, simply navigate to Jobs from the menu on the left, choose a process and either select the robots you want to execute the job from the environment, or allocate the job dynamically. A job allocated directly to certain robots will have priority over jobs allocated dynamically, but jobs allocated dynamically are executed immediately when any robot in the environment becomes available.

When starting a job, you have the option to set input parameters or display the output parameters if they exist as arguments in the Main.xaml of the package.

There are 2 options to stop a job:
- using Stop Job, that will stop it when a Should Stop activity in the workflow is encountered
- using Kill Job, that will stop it immediately.

## Using Schedules (planned)
Schedule offer multiple configuration options, such as:
- choosing a regular interval to execute the process
- setting up parameters (arguments in the Main.xaml in Studio)
- selecting the robots to execute (similarly to Jobs) - all robots, selected robots or dynamically
- setting up non-working days and other parameters.

To schedule a process execution, navigate to the Schedules page, create a new Schedule and configure its parameters. Once you are done, click 'Create'.

## From the Robot Tray
Running processes from the Robot Tray can be very useful for testing purposes or simple automations created for parts of your job or personal matters.

To run a process directly from the Robot Tray:
- make sure the package is assigned to the environment in which your attended robot is part of;
- open the robot;
- if the package has an update available, you will see an up arrow from which you can update it in your robot;
- once this is done, you can run the process by clicking the 'Play icon'.

# Assets
## What are Assets?
Assets are shared variables or credentials that are stored in the Orchestrator and used by the robots in different automation projects. They can be considered a data repository that the robots can access when running processes, based on clear instructions.

There are four types of assets:
- **Text** - the equivalent of String (it is not required to add quotation marks)
- **Bool** - supports true or false values
- **Integer** - stores only whole numbers
- **Credential** - contains usernames and passwords that the Robot requires to execute particular processes, such as login details for SAP or SalesForce.

## What are some business scenarios in which I will use Assets?
- When data doesn't change from one execution of a process to another, so it doesn't make sense to assign it every time from the Parameters tab. At the same time, data that may change shouldn't be stored in the workflow;
- Whenever robots need credentials to access applications in an automation scenario. The Credentials stored as Assets are encrypted with the AES 256 algorithm.

## How are Assets created and used?
In **Orchestrator**:
- Assets can be created from the dedicated area;
- The name and the data type have to be provided. By using the tabs, assets can be configured as follows:
    - Single Value - can be accessed and used by all Robots;
    - Value Per Robot - each value provided can be accessed only by the indicated Robot.
- Assets can be modified or deleted from the same menu.

In **Studio**:
- For credentials, the 'Get Credential' activity has to be used;
- For all the other types of assets, the 'Get Asset' activity is used.

# Queues
## What are Queues?
Queues are containers that can hold an unlimited number of items. Queues in Orchestrator will store items and allow their distribution individually to robots for processing, and monitoring the status of the items based on the process outcomes.

Working with Queues brings a series of advantages, especially for large automations with multiple types of elements underlined by a complex logic:
- centralized depository of work items;
- reporting capabilities at individual item level, as well as queue level;
- effectiveness of item distribution process - anytime a robot becomes available, the queue item in line is dispatched;
- unitary logic of item distribution - such as First In, First Out.

## What are some business scenarios in which I will use Queues?
Items in the Orchestrator Queues are known as transactions. They are meant to be indivisible units of work - a customer contract, an invoice, a complaint, and so on.

Working with Queues is very useful for large automations mainly, where the number of items is high and the distribution process may become problematic. Consider the following examples:
- New customer enrollment forms for a retail company - these may come from different sources (online, partners, own shops, call center) and having a smooth process of adding them to the processing line is crucial. Working with Queues will ensure that these are processed within the SLA time constraints;
- The complaint process of a worldwide retailer, having contact centers in many locations across the world - working with Queues will ensure that the items are centralized in a single depository and distributed to the available resources as they become available.

## Working with Queues
Queues are easily created in Orchestrator. When they are created, queues are empty, but there are specific activities in the UiPath Studio to make the robots populate Queues. Bulk upload is also supported directly in Orchestrator, from .csv files. 

When creating a queue, you set the **maximum number of retries** (the number of times you want a queue item to be retried) and the **Unique Reference** field (select Yes if you want the transaction references to be unique). Once a queue was created, these settings can not be modified 

Queues are very important for the Dispatcher & Performer model, in which the two main stages of a process involving queues is separated:
- the stage in which data is taken and fed into a queue in Orchestrator, from where it can be taken and processed by the robots. This is called Dispatcher;
- the stage in which the data is processed, called Performer.

Below are the main activities used to program the robots to work with queues:
- **Add Queue Item** - When encountering this activity in a workflow, the robot will send an item to the designated Queue and will configure the time frame and the other parameters.
- **Add Transaction Item** - The robot adds an item in the queue and starts the transaction with the status 'In progress'. The queue item cannot be sent for processing until the robot finalizes this activity and updates the status.
- **Get Transaction Item** - Gets an item from the queue to process it, setting the status to 'In progress'.
- **Postpone Transaction Item** - Adds time parameters between which a transaction must be processed.
- **Set Transaction Progress** - Enables the creation of custom progress statuses for In Progress transactions. This can be useful for transactions that have a longer processing duration, and breaking down the workload will give valuable information.
- **Set Transaction Status** - Changes the status of the transaction item to Failed (with an Application or Business Exception) or Successful. As a general approach, a transaction failed due to Application Exceptions will be retried, and a transactions failed due to Business Exceptions will not be retried. A Queue item can have one of the following statuses:
    - New - just added to the queue with Add Queue Item (or the item was postponed or a deadline was added to it).
    - In Progress - the item was processed with the Get Transaction Item or the Add Transaction Item activity;
    - Failed - the item did not meet a business or application requirement within the project;
    - Successful - the item was processed;
    - Abandoned - the item remained in the In Progress status for a long period of time (approx. 24 hours) without being processed;
    - Retried - the item failed with an application exception and was retried (at the end of the process retried, the status will be updated to a final one - Sucessful or Failed)
    - Deleted - the item has been manually deleted from the Transactions page