# Zurich API Reference

**Last updated: 11/11/2025**

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries.

Some examples and graphics depicted herein are provided for illustration only. No real association or connection to ServiceNow products or services is intended or should be inferred.

ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. Other company and product names may be trademarks of the respective companies with which they are associated.

Please read the ServiceNow Website Terms of Use at http://www.servicenow.com/terms-of-use.html

Company Headquarters 2225 Lawson Lane Santa Clara, CA 95054 United States (408) 501-8550

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries.

### Table of Contents

API implementation and reference........................................................................................................ 4

API implementation............................................................................................................................................. 4

Scripting........................................................................................................................................................... 5

Web services............................................................................................................................................. 318

API reference.................................................................................................................................................... 602

Server API reference............................................................................................................................. 604

Client API reference............................................................................................................................ 3963

Client Next Experience API reference.......................................................................................... 4243

UIB API reference................................................................................................................................ 4344

Client mobile API reference............................................................................................................. 4380

Mobile SDK API reference.................................................................................................................. 4411

REST API reference............................................................................................................................... 4717

ServiceNow Fluent............................................................................................................................... 9698

Browse APIs by product..................................................................................................................... 9702

Developer guides........................................................................................................................................... 9722

Alarm Management Open API Developer Guide...................................................................... 9723

AP Invoice API Developer Guide.................................................................................................... 9726

Event Notification Management Open API Developer Guide............................................... 9729

GlideGeoPoint Developer Guide..................................................................................................... 9733

Mobile SDK Developer Guide Android....................................................................................... 9737

Mobile SDK Developer Guide iOS................................................................................................ 9777

Producer Event Notification Framework developer guide...................................................... 9815

Product Order Open API Developer Guide................................................................................ 9825

Resource Inventory Open API Developer Guide...................................................................... 9829

ScopedCacheManager API Developer Guide........................................................................... 9829

Service Order Open API Developer Guide.................................................................................. 9831

Trouble Ticket Open API Developer Guide................................................................................ 9834

Client GlideList API in the Workspace Experience UI Developer Guide.......................... 9838

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. iii

## API implementation and reference

Get started using ServiceNow APIs with guides, resources, and reference documentation.

API implementation

Set up Web Services to access ServiceNow APIs.

API reference

Find reference documentation for Client, Server, and REST APIs.

Developer guides

Explore program resources for learning, building, and developing.

##### API implementation

Use web services to connect ServiceNow applications to other software applications.

This section includes information on the following:

**-** Useful server-side scripts for implementing functionality that is not available in the core system.

**-** Details on how to debug scripts

**-** Client scripting techniques and use cases, such as messages.

**-** Use web services to connect ServiceNow applications to other software applications.

##### API reference

Explore ServiceNow APIs that you can use to change functionalities and add features on the ServiceNow AI Platform.

This section includes references for the following:

**-** Client JavaScript APIs to control how the ServiceNow AI Platform functions and is displayed within the web browser.

**-** Server-side JavaScript APIs to modify and develop applications.

**-** REST APIs to access and update data on the ServiceNow AI Platform.

##### Developer guides

Set up or extend API configuration on the ServiceNow AI Platform for a ServiceNow product or API.

### API implementation

You can use JavaScript APIs to extend application server and client functionality. Use web services to connect ServiceNow applications to other software applications.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 4

Scripts

Extend application server and client functionality.

Web services

Communicate between ServiceNow and third-party applications.

##### Scripts

Use Server JavaScript APIs in scripts to change application functionality or create applications. Use client-side JavaScript APIs to control aspects of how an instance is displayed and functions within the web browser.

Common use cases:

**-** Calculate durations to give users a way to specify when a task or process is due.

**-** Display prompts with alerts, confirmations, or other messages.

**-** Implement event logging at different output levels, such as debug, info, warning, and error.

**-** Query, update, create, and delete records.

**-** Validate the input of all date and time fields.

##### Web services

Use inbound (provider) and outbound (consumer) web services enable diverse applications to exchange information.

Common use cases:

**-** Use REST API request information from ServiceNow instances in third-party applications.

**-** Create scripted REST APIs for custom requests that aren’t available in the provided ServiceNow REST APIs.

**-** Create a custom GraphQL API to query record data from a component or a third-party system.

**-** Use the open database connectivity (ODBC) driver for read-only access to the database associated with your instance.

**-** Use domain separation to separate data, processes, and administrative tasks into logical groups.

#### Scripting

Use scripts to extend your instance beyond standard configurations. With scripts, you may automate processes, add functionality, integrate your instance with an outside application and more.

APIs (Application Programming Interfaces) provide classes and methods that you can use in scripts to define functionality. ServiceNow provides APIs as JavaScript classes, web services, and other points of connection for integrations. Note that you cannot access commonly used JavaScript objects (such as DOM or Window). Jelly scripts are also used in some modules. Jelly is used to turn XML into HTML and may include both client-side and server-side scripts.

Scripts may be server-side (run on the server or database), client-side (run in the user's browser), or run on the MID server.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 5

##### Note: When you are writing scripts, you cannot use reserved words.

Understand JavaScript before you begin customizing your instance, and with Jelly if you intend to deploy Jelly scripts.

##### Server-side scripts

Perform database operations. For example, use a server-side script to update a record. Create a script in a scoped application or in the global scope. Each execution context includes a set of available APIs.

Scoped environment

###### Use scoped APIs when scripting in a scoped application. Scoped Glide APIs do

###### not include all the methods included in the global Glide APIs, and you cannot call

###### a global Glide API in a scoped application.

Global environment

The global scope is a special application scope that identifies applications developed prior to application scoping, or applications intended to be accessible to all other global applications. Use global APIs when scripting in the global scope.

To learn more about server-side scripting, see Server-side scripting. To learn more about application scope, see Application scope.

##### Client-side scripts

Make changes to the appearance of forms, display different fields based on values that are entered, or change other custom display options.

**-** onLoad client scripts run when the form or page is loaded

**-** onChange client scripts run when something specific gets changed AND also when the form or page loads

**-** onSubmit client scripts run when the form is submitted

Client Scripts can also be called by other scripts or modules, including UI policies. To learn more about client-side scripting, see Client-side scripting.

##### Available script types

Scripts can be used in many places. The most important detail is whether the script runs on the client or the server.

Script types and where they run

Script Description Runs on

Access Control Determines whether access will be granted for a specified operation to a specific entity.

**-** type of entity being secured

**-** operation being secured

**-** unique identifier describing the object

server script and any condition run on the server

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 6

Script types and where they run (continued)

Script Description Runs on

Can be defined by roles, conditional expressions or scripts.

Ajax Scripts

Enables the client to get data from the server to dynamically incorporate into a page without reloading the whole page.

**-** Ajax Client Scripts request that information be returned, or that action be taken, or sometimes both

**-** Ajax Server Scripts fulfill Ajax Client Script requests

**-** client - Ajax Client Scripts run on the client

**-** server - Ajax Server Scripts run on the server

Business Rules

Customizes system behavior

**-** runs when a database action occurs (query, insert, update or delete)

**-** the script may run

◦ before or after the database action is performed (runs as part of the database operation)

◦ asynchronously (at some point after the database operation)

◦ on display (when displaying the data in a form)

server script and any condition run on the server

Service Catalog UI policies

Defines the display of a variable set or a

catalog item (from the service catalog). (^) **•** client scripts in the "execute if true" field or "execute if false" field run on the client

**-** server - all conditions run on the server

Client Scripts Used for making changes to the appearance of forms, displaying different fields based on values that are entered or other custom display options.

**-** onLoad means the Client Script runs when the form or page is loaded

**-** onChange means the Client Script runs when something specific gets changed AND also when the form or page loads

**-** onSubmit means the Client Script runs when the form is submitted

Client Scripts can also be called by other scripts or modules, including UI policies.

client

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 7

Script types and where they run (continued)

Script Description Runs on

Script actions Contains scripts which run when an event occurs, for example

**-** approval is cancelled

**-** change is approved

**-** problem is assigned

Can have a condition which must be true for the script to run. Commonly used to call a Script Include.

server script and any condition run on the server

Script Includes Contains scripts which can be functions or classes. These scripts run only when called by other scripts (often Business Rules).

Any server script which is complicated or reusable should be a Script Include (especially complicated Business Rules).

server

Transform maps Used for importing data.

**-** defines mapping relationships between tables

**-** can use Business Rules, other scripts and/ or other options to import that data

Do not always include scripts.

server

UI actions Creates the ability to choose a specific action such as clicking a button or a link.

UI Actions put these items on forms and lists:

**-** buttons

**-** links

**-** context menu items

**-** list choices

**-** client - when the "Client" box is checked, the script in the script field runs on the client

**-** server - when the "Client" box is unchecked, the script in the script field runs on the server

**-** client - when the "Client" box is checked, the onClick script is available, which can contain any JavaScript but normally calls a function which is specified in the script field

**-** server - all conditions run on the server

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 8

Script types and where they run (continued)

Script Description Runs on

UI Context Menus

Defines which "right-click menu" will pop-up in which area, and the menu choices that will be available

##### Note: If you use a left-handed mouse

configuration, right-click means "click the other button."

**-** client - onShow scripts run on the client

**-** client - action scripts run on the client

**-** server - dynamic action scripts run on the server

**-** server - all conditions run on the server

UI macros Contains modular, reusable components that can contain Jelly and are called by UI pages. They also contain different types of scripts and may be called multiple times on the same page.

##### Note: Jelly turns XML into HTML.

**-** server - the UI Macro itself executes on the Server

**-** server - may contain content that runs on the server (Jelly expressions or JavaScript inside Jelly constructs)

**-** client - may generate output that runs on the client (embedded JavaScript within <script> tags)

UI Pages Used to create and display pages, forms, dialogs, lists and other UI components. Can be displayed on a standalone basis, or called as a usable component, as part of a larger page.

Can contain

**-** server - Jelly XML runs on the server to produce HTML

**-** client - HTML may contain embedded JavaScript that runs on the client

**-** client - client scripts run on the client

**-** server - processing scripts run on the server

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 9

Script types and where they run (continued)

Script Description Runs on

**-** Client Scripts,

**-** processing scripts (which are server scripts),

**-** HTML,

**-** Jelly,

**-** UI Macros,

**-** and also can call other scripts.

##### Note: Jelly turns XML into HTML.

UI Policies Defines the behavior and visibility of fields on a form.

**-** mandatory

**-** visible

**-** read only

Use UI Policies rather than client scripts whenever possible.

**-** UI Policies are always attached to one table

**-** UI Policies often have a condition which must be true in order for them to run

**-** client - scripts in the "execute if true" field or "execute if false" field run on the client

**-** server - all conditions run on the server

UI Properties

Designates what the instance will look like.

**-** server - properties set on the server

**-** client - the results get rendered on the client

no scripts

UI Scripts Contains client scripts stored for re-use. Only used when called from other scripts.

Not recommended for use.

client

Validation Scripts Validates that values are in a specified format.

For example, a validation script can verify that the only value allowed in a specific field is an integer.

client

Workflow editor Used to create or change a workflow. Scripts can be run at any point in a workflow, or different scripts can be run at different points.

server script and any conditions run on the server

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 10

Script types and where they run (continued)

Script Description Runs on

Scripts also can be found inside every workflow activity and can be modified (although do so with extreme caution).

##### Glide class overview

The ServiceNow Glide classes expose JavaScript APIs that enable you to conveniently work with tables using scripts.

Using the Glide APIs, you can perform database operations without writing SQL queries, display UI pages, and define UI actions. The following tables provide brief descriptions of the Glide classes and links to detailed information.

Server-side Glide classes

Class Description

GlideRecord Use this class for database operations instead of writing SQL queries. GlideRecord is a special Java class that can be used in JavaScript exactly as if it were a native JavaScript class. A GlideRecord is an object that contains records from a single table. See GlideRecord.

GlideElement Use this class to operate on the fields of the current GlideRecord. See GlideElement.

GlideSystem Use this class to get information about the system. See GlideSystem.

GlideAggregate Use this class to perform database aggregation queries, such COUNT, SUM, MIN, MAX, and AVG, for creating customized reports or calculations in calculated fields. See GlideAggregate.

GlideDateTime Use this class to perform date-time operations, such as date-time calculations, formatting a date-time, or converting between date-time formats. See GlideDateTime.

Client-side Glide Classes

Class Description

GlideAjax Use this class to execute server-side code from the client. See GlideAjax.

GlideDialogWindow Use this class to display a dialog window. See GlideDialogWindow.

GlideForm Use this class to customize forms. See GlideForm.

GlideList2 Use this class to customize (v2) lists, including normal lists and related lists. See GlideList2.

GlideMenu Use this class to customize UI Context Menu items. See GlideMenu.

GlideUser Use this class to get session information about the current user and current user roles. See GlideUser.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 11

Glide stack

Glide is an extensible Web 2.0 development platform written in Java that facilitates rapid development of forms-based workflow applications (work orders, trouble ticketing, and project management, for example).

User interface stack technology map

Java packages Technologies used

User Interface (Browser)

**-** AngularJS

**-** HTML

**-** CSS

**-** JavaScript

com.glide.ui

com.glide.jelly

GlideServlet Apache Jelly

com.glide.script Business Rules Mozilla Rhino

com.glide.db Persistence JDBC

User interface stack technology map descriptions

Name Description Attributes

GlideServlet The primary driver of Glide, and the only servlet in the system, is found in GlideServlet.java. The GlideServlet:

**-** Handles inbound action requests

**-** Renders pages

**-** Merges data with forms

**-** Presents to user

**-** Interfaces with script layer

Business

Rules (^) **•** ECMA / JavaScript implementation based on Mozilla Rhino

**-** Interfaces with persistence layer using JDBC recordset interface

**-** Merges persistence layer meta-data with data for easy correlation

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 12

User interface stack technology map descriptions (continued)

Name Description Attributes

Persistence

**-** Persistence means any store

◦ RDBMS

◦ LDAP

◦ File system

**-** Uniform access regardless of store type

**-** Provides QUID and meta- data capabilities

**-** Interfaces presented to callers

◦ RecordSet

◦ TableDescriptor

◦ ElementDescriptor

Glide servlet

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 13

##### Execution order of scripts and engines

Scripts, assignment rules, business rules, workflows, escalations, and engines all take effect in relation to a database operation, such as insert or update. In many cases, the order of these events is important.

##### Note: Client-based code that executes in the browser, using Ajax or running as JavaScript,

will always execute before the form submission to the server.

The order of execution is as follows:

**1.** Before business rules: Scripts configured to execute before the database operation with an order less than 1000.

**2.** Before engines. The following are not executed in any specific order:

◦ Approval engine (for task and sys_approval_approver tables)

◦ Assignment rules engine (for task tables)

◦ Escalation engine

◦ Data policy engine

◦ Field normalization engine

◦ Role engine keeps role changes in sync with sys_user_has_role table (for sys_user, sys_user_group, sys_user_grmember, and sys_user_role tables)

◦ Execution plan engine (for task tables)

◦ Update version engine creates version entry when sys_update_xml entry is written (for sys_update_xml table)

◦ Data lookup engine inserts or updates

◦ Workflow engine (for default workflows)

**3.** Before business rules: Scripts configured to execute before the database operation with an order greater than or equal to 1000.

**4.** The data base operation (insert, update, delete).

**5.** After business rules: Scripts configured to execute after the database operation with an order less than 1000.

**6.** After engines. The following are not executed in any specific order:

◦ Label engine

◦ Listener engine

◦ Table notifications engine

◦ Role engine keeps role changes in sync with sys_user_has_role table (for sys_user, sys_user_group, sys_user_grmember and sys_user_role tables)

◦ Text indexing engine

◦ Update sync engine

◦ Workflow engine (for deferred workflows)

◦ Trigger engine (for all Workflow Studio flows)

**7.** Email notifications. The following are executed based on the weight of the notification record:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 14

◦ Notifications sent on an insert, update, or delete

◦ Event-based notifications

**8.** After business rules (Only active records). Scripts configured to execute after the database operation with an order greater than or equal to 1000.

##### Note: Like After business rules, Async business rules execute their logic after a

database operation occurs. Unlike After business rules, Async business rules execute asynchronously, running in the background simultaneously with other processes. Async business rules run after the user submits the form and after the scheduler runs the scheduled job created from the business rule. The system creates a scheduled job from the business rule after the user submits the form but before any action is taken on the record in the database.

##### Script evaluation of fields by data type

Script fields evaluate data based on the field type of the input.

Evaluation of fields by data types

Type

Evaluates to in script

Example

String The string "dog" > "dog"

Decimal A number with up to two decimal points

12.34 > 12.34

Integer A number with zero decimal points

12 > 12

True / False

true or false > true

> false

Date A date formatted as yyyy-mm-dd

2008-11-04

Date-time A day and time formatted as yyyy-mm-dd hh:mm:ss

2008-11-04 06:46:20

Duration A date that is equal to January 1st 1970 00:00:00 + the amount of time of the duration being stored

> "1970-01-01 00:00:00"

> "1970-01-02 02:03:04"

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 15

Evaluation of fields by data types (continued)

Type

Evaluates to in script

Example

##### Note:

This date corresponds to the system time zone. If a different user time zone has been specified, the date and time value may appear different for that user.

Choice Returns the contents of the value field for the sys_choice record associated with that choice. See: Choice List for more information on returning the value associated with a particular item in a choice list.

> "2" (Note that this value is is a string)

Journal Returns a string of all entries made to that journal field. See Journal Fields for scripting of journal type fields

The web server is down > The web server is down

Reference Returns the sys_id of the record that is referenced

> "287ee6fea9fe198100ada7950d0b1b73"

Image Returns the path to the image

> images/icons/image_name.gif

URL Returns a string > "http://www.service-now.com"

Glide Lists

Returns a string of commaseparated Sys IDs

> 5137153cc611227c000bbd1bd8cd2007,46d14f04a9fe19810142e40c6b071512

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 16

##### Scripting alert, info, and error messages

You can send messages to customers as alerts, informational messages, or error messages.

Business rule and other general use scripts

Script Result

current.field_name.setError("Hello World");

Adds Hello World below the specified field in a red error message.

gs.addInfoMessage("Hello World"); Adds Hello World at the top of the browser window in a blue info message.

gs.addErrorMessage("Hello World"); Adds Hello World at the top of the browser window in a red error message.

gs.print("Hello World"); Writes Hello World to the text log on the file system but not to the sys_log table in the database.

gs.log("Hello World"); Writes Hello World to the database and the log file.

##### Note: gs.log can adversely affect

performance if used too frequently.

Client side scripts

Script Result

alert("Hello World"); Displays a window with Hello World and an OK button.

##### Note: Rather than use JavaScript

###### alert(), for a cleaner look, you

can display an error on the form itself

###### with thee showFieldMsg() and

###### hideFieldMsg() methods. For

more information, see Display field messages.

confirm("Hello World"); Displays a window with Hello World? and OK and Cancel buttons.

g_form.showFieldMsg("field_name", "Hello World", "error");

Adds Hello World below the specified field in a red error message.

g_form.hideFieldMsg("field_name"); Hides the most recent message for the specified field.

##### Important: The methods in this table are only for use in client scripts.

It is also possible to add other custom messages to your forms if necessary using client scripting.

The text size of info and error messages at the top of the screen is customizable. Two properties control this. If you configured your forms, you may need to add these properties.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 17

##### Note: The client script alert option is not available for use with Automated Test Framework

(ATF).

Error and alert text size properties

Property Description

css.outputmsg.info.text.fontsize

Sets the size for info messages. Default is 11pt.

css.outputmsg.error.text.fontsize

Sets the size for error messages. Default is 11pt.

##### Now Assist for Code

ServiceNow ® Now Assist for Code is a generative AI-powered tool that assists you by providing code suggestions. It accelerates the coding tasks and boosts productivity when scripting on the ServiceNow AI Platform.

##### Get started

##### Important: Some Now Assist products/features are currently unavailable for customers

in the FedRAMP, NSC DOD IL5, or Australia IRAP-Protected data centers, self-hosted customers, or in other restricted environments. For more information, see the KB0743854 article in the Now Support Knowledge Base. Please check for availability updates in future releases.

##### Important: Some Now Assist products/features are currently available only for

customers in some regions. Be sure to check for availability updates in future releases.

##### Troubleshoot and get help

**-** ServiceNow Community

**-** Search the Known Error Portal for known error articles

**-** Contact Customer Service and Support

AI limitations

This application uses artificial intelligence (AI) and machine learning, which are rapidly evolving fields of study that generate predictions based on patterns in data. As a result, this application may not always produce accurate, complete, or appropriate information. Furthermore, there is no guarantee that this application has been fully trained or tested for your use case. To mitigate these issues, it is your responsibility to test and evaluate your use of this application for accuracy, harm, and appropriateness for your use case, employ human oversight of output, and refrain from relying solely on AI-generated outputs for decisionmaking purposes. This is especially important if you choose to deploy this application in areas with consequential impacts such as healthcare, finance, legal, employment, security, or infrastructure. You agree to abide by ServiceNow’s AI Acceptable Use Policy , which may be updated by ServiceNow.

Data processing

This application requires data to be transferred from ServiceNow customers' individual instances to a centralized ServiceNow environment, which may be located in a different data center region from the one where your instance is, and potentially to a third-party cloud provider, such as Microsoft Azure. This data is handled per ServiceNow's internal policies and procedures, including our policies available through our CORE Compliance Portal.

Data collection

ServiceNow collects and uses the inputs, outputs, and edits to outputs of this application to develop and improve ServiceNow technologies including ServiceNow models and AI products. In addition, this application will collect information about scripts (and associated script records) in which Now Assist for code generation is called. Customers can opt out of future data collection at any time, as described in the Now Assist Opt-Out page.

For more information, see the Now Assist documentation.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 18

Exploring Now Assist for Code

ServiceNow ® Now Assist for Code is a generative AI-powered tool designed to help developers create, edit, and summarize code.

Now Assist for Code is designed to empower developers with code suggestions. By using natural language prompts in the script editor on the ServiceNow AI Platform ® , you will receive contextaware code suggestions that enhance your coding experience.

Now Assist for Code supports Now LLM Service, Azure OpenAI, Google Gemini and AWS Anthropic model providers. This capability is a part of Creator Pro Plus offering and includes the following skills:

**-** Code generation

**-** Code autocomplete

**-** Code editing

**-** Code explain and summarize

##### Code generation overview

The Code generation skill creates new code at the cursor location based on user input, without altering the surrounding code. It considers the context provided by the code preceding and following it.

When code generation is enabled on an instance, a Now Assist icon ( ) appears at the bottom of the script editor.

After you describe the code you want to generate, you will receive code suggestions in the JavaScript editor on forms in the ServiceNow AI Platform

® and in Script steps within Workflow Studio. Developers, regardless of their scripting experience on the ServiceNow AI Platform ® , can benefit from code generation, allowing them to start writing custom code or refine existing code more efficiently.

##### Note: Developers must be assigned the now.assist.creator role to use code generation.

For more information on using this skill, see Generate code with AI-powered code generation.

##### Code autocomplete overview

The Code autocomplete skill provides contextually relevant suggestions as users type in the script editor. These suggestions appear in grey text and will only be added to the script once the user accepts them.

For more information, see Generate code with autocomplete.

With the Zurich release, Code autocomplete is available in the ServiceNow integrated development environment (IDE) application.

##### Difference between Code generation and Code autocomplete skills

The Code generation skill requires a specific prompt from the user to create code that aligns precisely with the given requirements or instructions. The Code autocomplete skill works automatically. It generates code completions or snippets based on the context around it.

This means the first skill relies on direct user input, while the second skill anticipates what the user might need, offering suggestions and completions without needing detailed prompts.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 19

##### Code edit overview

The Code Edit skill modifies the selected code while reviewing the surrounding code. It functions only when the code to be edited is highlighted.

For more information, see Edit code with Now Assist.

##### Code explain and summarize overview

The Code explain and summarize skill provides a summary of the code and a comprehensive explanation of its functionality.

For more information, see Explain and summarize code.

##### Now Assist for Code benefits

Benefit Feature Users

Generate code based on your prompts to improve quality and reduce repetitive tasks.

Generate code with AI-powered code generation

Developers

Quickly edit and refactor large code segments. Edit code with Now Assist

Developers

Add comments to code segments. Add comments to code

Developers

Understand code. Explain and summarize code

Developers

Identify code generated by AI. Tracking AI-generated code

Developers, administrators

General guidelines for code generation

Use these general guidelines for code generation to get better code suggestions and create useful and accurate scripts.

##### Writing prompts

Write clear and specific but concise prompts

Specify the expected outcome and context clearly. Include important details like task requirements, specific APIs if you know them, and any limitations.

Experiment with different prompts

**-** Consider adjusting your task instructions and incorporating examples. Observe how the code suggestions change with different prompt styles and levels of detail.

**-** Keep track of your prompts, along with any modifications and instructions for generating prompts that meet your specifications.

Character limit of the prompts

Short and concise prompts generate better outcomes.

On reaching 200 characters, a message appears to inform you that short, focused, task-oriented directions yield the best results.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 20

Input beyond 300 characters isn’t allowed.

Example prompts for code generation

Weak prompt Strong prompt Notes

Get incidents with tasks Get incidents with related tasks Includes sufficient detail.

Count P1 incidents between 3-3 and 4-13

Use Glide aggregate to count number of P1 incidents closed between March 3 to April 13 assigned to admin

Includes the API name and more specific language.

Don’t allow changing P1 change requests

If open change request is P1, don’t allow reducing the severity unless it's the creator

Includes more specific instructions on what shouldn't change.

Latest change Glide record of the most recent change Includes the API name and more specific language.

##### Reviewing code

Review code

Implement strict and detailed reviews of the AI-generated code to determine its accuracy, efficiency, and how well it adheres to your coding standards.

Test code

Validate the code by running it against test cases in controlled environments to verify that it functions according to your requirements.

Configuring Now Assist for Code

Install and configure Now Assist for Code on an instance.

Install Now Assist for Code

Install the ServiceNow ® Now Assist for Creator application from the ServiceNow ® Store to get Now Assist for code generation.

###### Before you begin

**-** Review the Now Assist for Creator application listing in the ServiceNow Store for information on dependencies, licensing or subscription requirements, and release compatibility. Now Assist for Creator installs the Now Assist for code generation application (sn_now_assist_code).

Role required: admin

###### Procedure

**1.** From the Now Assist for Creator application page on the ServiceNow Store, select **Buy**.

**2.** After approval has been granted, on your instance, navigate to **All** > **System Applications** > **All** **Available Applications** > **All**.

**3.** Using the search bar, search for the Now Assist for Creator application (sn_now_creator).

**4.** Select **Install**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 21

**5.** Verify that Now Assist for Creator is installed:

###### a. Navigate to All > Now Assist Admin > Now Assist Skills.

b. In the workflow list, select Creator.

c. Verify that the Now Assist for Code skills are active.

###### What to do next

Grant the now.assist.creator role to each user you want to use code generation. For more information, see Configure user access.

Related topics

Install Now Assist for Creator

Configure user access

Assign the now.assist.creator role to users who have permission to edit scripts.

###### Before you begin

Role required: admin

###### About this task

To use the Now Assist for Code skills, users must have the now.assist.creator role.

###### Procedure

**1.** Navigate to **All** > **User Administration** > **Users**.

###### 2. Open a user record from the list to assign the now.assist.creator role.

**3.** Under **Related Links** go to the **Roles** tab, and select **Edit**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 22

###### 4. From the Collection list, select now.assist.creator, and then select Add.

###### Assign the now.assist.creator role to users who have permission to edit scripts.

To learn more about user roles that have permission to edit scripts, see Special administrative roles

**5.** Select **Save**.

###### Result

###### The now.assist.creator role is added to the user and is listed in the Roles tab.

Select a model provider for Now Assist skills

Select a large language model (LLM) as the AI service provider for Now Assist for Code skills.

###### Before you begin

Role required: admin

###### About this task

You can use Now LLM Service, Azure OpenAI, Google Gemini or Anthropic Claude on AWS as the AI model provider for all Now Assist skills and AI agents. Use the Configuration Controls in AI Control Tower to define which options are available, then set the skill-level preferences in the Now Assist Admin console. For more information, see Large language models on the

ServiceNow AI Platform

® .

###### Procedure

**1.** Navigate to **All** > **Now Assist Admin** > **Settings**.

**2.** Go to the **Manage model providers** tab and select **Model Providers**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 23

**3.** Change the model provider by selecting **Edit LLM Provider**.

**4.** Select a model provider for either all skill groups or just a specific skill group.

Choice Description

Select a model provider for all the skill groups and skills in the instance.

a. In the Edit model provider Window, set the edit scope to Instance.

b. From the Default model provider list, select a model provider.

c. Select Save and activate.

Select a model provider for a specific skill group.

a. In the Edit model provider Window, set the edit scope to Customize.

b. To change the model provider for a skill group, do the following:

i. From the Skill group name list, select the skill group.

ii. From the Default LLM provider list, select a model provider.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 24

Choice Description

iii. Select Save and activate

Select a model provider for a specific skill.

a. In the Edit model provider Window, set the edit scope to Customize.

b. To change the model provider for specific skills, do the following:

i. From the Select skills list, select the skill.

ii. From the Default LLM provider list, select a model provider.

iii. Select Save and activate.

##### Note: You can select a different mod

el provider for each skill.

###### Result

The skills and the skill groups are updated with the selected model providers.

Enable or disable Now Assist skills

Learn to enable and disable Now Assist for Code skills.

###### Before you begin

Role required: admin

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 25

###### About this task

You can enable or disable Now Assist for Code skills.

###### Procedure

**1.** Navigate to **Admin** > **Now Assist Admin**.

**2.** Go to the **Now Assist Skills** tab and select **Creator**.

A list of all Now Assist Skills for Creator is displayed.

**3.** To enable or disable a skill:

◦ Select Turn on to enable a skill.

The skill is enabled for all users.

◦ Select Deactivate skill to disable a skill.

A prompt appears asking you to confirm skill deactivation. Select Deactivate to disable the skill.

The skill is disabled for all users.

Using Now Assist for Code

Learn to use ServiceNow ® Now Assist for Code to generate, edit, explain and summarize code.

**-** Generate code with AI-powered code generation

Use the Code generation skill to generate new code based on your prompts.

**-** Generate code with autocomplete

Use the Code autocomplete skill to get contextually relevant code suggestions or completions as you type in the script editor.

**-** Edit code with Now Assist

Use the Code edit skill to quickly edit and refactor large code segments.

**-** Add comments to code

Use this skill to add comments to code segments.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 26

**-** Explain and summarize code

Use the Code explain and summarize skill to understand code.

**-** Tracking AI-generated code

Control when to track and indicate that code is AI-generated.

Generate code with AI-powered code generation

Generate code from text with AI-powered Now Assist for Code.

###### Before you begin

Learn how to write prompts to generate better code suggestions. For more information, see General guidelines for code generation.

Role required: now.assist.creator

###### Procedure

**1.** Navigate to a form with a script field.

Example For example, to open a script include form:

◦ Navigate to All > System Definition > Script Includes and select New or enter sys_script_include.do in the navigation filter.

◦ Navigate to All > System Definition > Script Includes and select a script include.

**2.** In the script editor, place your cursor where you want to add code.

**3.** Right-click and select **Open Code with Now Assist** or use one of the following keyboard shortcuts:

◦ Windows: Ctrl-Enter

◦ Mac: Cmd-Enter

##### Tip: Select the Help icon ( ) to access the list of relevant keyboard shortcuts.

**4.** In the **Code with Now Assist** dialog box, enter text that describes the desired goal of the code to generate.

The text you enter must be fewer than 1,000 characters.

**5.** Press Enter to generate a code suggestion. The code suggestion appears highlighted in the script editor.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 27

**6.** Review the code suggestion and complete one of the following steps:

◦ To include it in your script and make any edits, select Accept.

◦ To regenerate a suggestion, revise the text in the dialog box and select the arrow icon ( ).

◦ To remove it from the script, select Reject. When you accept a code suggestion, a line next to the line numbers indicates which code was created by AI and hasn't been edited. If you edit AI-generated code, the line indicator doesn’t appear for those lines of code.

Trouble? If the code suggestion doesn’t meet your requirements, try rephrasing your prompt according to the prompt guidance and generating another code suggestion.

**7.** Select **Submit** or **Update** to save your changes.

##### Note: Depending on your workflow needs, you can use the prompt modal in either inline

or floating mode. In the inline mode, the prompt modal is embedded within the script editor. In the floating mode you can move the prompt modal around the script editor. Toggling between these two modes is simple. When in inline mode, select the Pop Out toggle to switch to floating mode. Conversely, when in floating mode, select the Pop In toggle to return to inline mode. The transition between inline and floating modes preserve all text within the modal.

Generate code with autocomplete

The autocomplete feature of Now Assist for Code provides you with contextually relevant code suggestions.

###### Before you begin

Role required: now.assist.creator

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 28

###### Procedure

**1.** Navigate to any script editor enabled with Now Assist for Code.

Example For example, to open a script include form, navigate to All > System Definition > Script Includes and select a script include.

**2.** Start coding in the script editor. When you stop typing, a code suggestion is displayed in grey within a few seconds.

##### Note:

Retrieval-Augmented Generation (RAG) enhances auto-complete suggestions and minimizes inaccuracies or hallucinations.

It may take a few seconds for the code suggestions to appear.

**3.** Review the code suggestions generated by the AI and decide whether to accept or reject them:

◦ Press the tab key to accept the code suggestion.

If you accept the code suggestion, it's added to the script.

◦ Press the esc key to reject the code suggestion or continue typing.

If you reject the code suggestion, it isn't added to the script.

**4.** After accepting the code suggestions, select **Update** to save the script. The code suggestion is saved within the script.

##### Note: To disable autocomplete for your session, in the script editor select Code with

Now Assist from the status bar at the bottom of the editor, and then clear Autocomplete.

Edit code with Now Assist

Quickly enhance your scripts by instructing Now Assist on how to improve the code.

###### Before you begin

Role required: now.assist.creator

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 29

###### About this task

When code generation is enabled on an instance, a Now Assist icon ( ) appears in the script editor.

###### Procedure

**1.** Navigate to a script.

Example For example, to open a script include form, navigate to All > System Definition > Script Includes and select a script include.

**2.** In the script editor, use one of the following options to edit code:

◦ Select the code that you want to edit. Right-click and select Open Code with Now Assist.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 30

◦ Select the code and then select the Quick Actions

button.

◦ Select the code and use one of the following keyboard shortcuts:

▪ Windows: Ctrl-Enter

▪ Mac: Cmd-Enter

##### Tip: Select the Help icon ( ) to access the list of relevant keyboard shortcuts.

**3.** In the **Edit code with Now Assist** dialog box, enter text that describes how you want to refactor the code.

The text you enter must be fewer than 1,000 characters.

**4.** Press Enter to generate an edited code suggestion.

A view comparing the original code and the edited code suggestion appears in the script editor.

**5.** Review the edited code suggestion and complete one of the following steps:

◦ To overwrite the original code with the edited code suggestion, select Accept.

◦ To regenerate a suggestion, revise the text in the dialog box and select the arrow icon ( ).

◦ To remove the edited code from the script and keep only the original code, select Reject. When you accept a code suggestion, a line next to the line numbers indicates which code was created by AI and hasn't been edited. If you edit AI-generated code, the line indicator doesn’t appear for those lines of code.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 31

Trouble? If the code suggestion doesn’t meet your requirements, try rephrasing your prompt according to the prompt guidance and generating another code suggestion.

**6.** Select **Submit** or **Update** to save your changes.

Add comments to code

Add comments in the Now Assist for Code enabled script editor using quick actions.

###### Before you begin

Role required: now.assist.creator

###### Procedure

**1.** Navigate to any script editor enabled with Now Assist for Code and select a script.

Example For example, to open a script include form, navigate to All > System Definition > Script Includes and select a script include.

**2.** In the script editor, select a code and then select the **Quick Actions** button.

**3.** Select **Add comments in code**.

The comments appear highlighted in the script editor.

**4.** Review the AI-generated comments and then either accept or reject the comments.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 32

If you accept the comments, they’re added to the script.

**5.** After accepting the comments, select **Update** to save your changes.

Explain and summarize code

Get a summary of the code or a comprehensive explanation of its functionality.

###### Before you begin

Role required: now.assist.creator

###### Procedure

**1.** Navigate to any script editor enabled with Now Assist for Code.

Example For example, to open a script include form, navigate to All > System Definition > Script Includes and select a script include.

**2.** In the script editor, select a code and then select the **Quick Actions** button.

**3.** To understand the purpose of the code, select **Summarize code**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 33

**4.** To get a comprehensive explanation of the code’s functionality, select **Explain code in detail**.

Tracking AI-generated code

Control when to track and indicate that code is AI-generated.

When you accept a code suggestion, the lines of code that are AI-generated are tracked and indicated by a line next to the line numbers in script editors. If you edit AI-generated code, the line indicator doesn’t appear for those lines of code.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 34

You can turn on and off tracking of AI-generated code and configure how long to record and indicate AI-generated code in script editors. By default, AI-generated code is recorded and indicated for six months.

Configure how long to indicate AI-generated code

Show that the code was generated by AI in script editors for a specified duration after accepting code suggestions.

###### Before you begin

Role required: admin

###### Procedure

**1.** In the navigation filter, enter sys_auto_flush.list, and press the Enter key.

**2.** Filter the Auto Flushes [sys_auto_flush] list by entering

###### sn_now_assist_code_ai_generated_lines in the Tablename column filter.

###### 3. Select sn_now_assist_code_ai_generated_lines to open the record.

**4.** In the **Age in seconds** field, enter the duration to record and indicate AI-generated code after its creation in seconds.

**5.** Select **Update**.

###### Result

AI-generated code is tracked and indicated. However, AI-generated code created before the configured duration isn’t recorded or indicated in script editors.

Turn off tracking AI-generated code

Turn off tracking and indicating which code is AI-generated.

###### Before you begin

Role required: admin

###### About this task

Tracking and indicating which code is AI-generated involves changes that are included in update sets. If you don't want to include changes related to this in update sets, you can turn off tracking and indicating AI-generated code.

###### Procedure

**1.** In the navigation filter, enter sys_properties.list and press the Enter key.

**2.** Filter the System Properties [sys_properties] list by entering

###### sn_now_assist_code.show_ai_code_line_marker in the Name column filter.

###### 3. Select sn_now_assist_code.show_ai_code_line_marker to open the property

record.

**4.** In the **Value** field, enter false.

**5.** Select **Update**.

###### Result

AI-generated code isn’t recorded or indicated in script editors.

Now Assist for Code reference

Reference topics provide additional information about configuration properties, roles, and more.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 35

Now Assist for Code properties

You can adjust how code generation functions on an instance using several advanced properties.

##### Note: To open the System Properties [sys_properties] table, enter

sys_properties.list in the navigation filter.

Properties for Now Assist for Code

Property Description

sn_now_assist_code.enable_code_assist Enables using code generation in supported script editors.

**-** Type: true | false

**-** Default value: true

**-** Location: System Property [sys_properties] table

**-** Learn more: You can also enable code generation from Now Assist Admin. For more information, see Activate a Now Assist skill.

sn_now_assist_code.enable_promptless_experience Enables using code completion in the script editor.

**-** Type: true | false

**-** Default value: false

**-** Location: System Property [sys_properties] table

sn_now_assist_code.enable_prompt_modal Enables using the Code with Now Assist dialog box to provide text prompts.

**-** Type: true | false

**-** Default value: true

**-** Location: System Property [sys_properties] table

**-** Learn more: Generate code with AI- powered code generation

sn_now_assist_code.show_ai_code_line_marker Enables tracking which lines of code are AI-generated. In a script editor, the AI-generated code are indicated by a line next to the line numbers. However, if you edit any AI-generated code, the

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 36

Properties for Now Assist for Code (continued)

Property Description

indicator will no longer appear for those modified lines.

**-** Type: true | false

**-** Default value: true

**-** Location: System Property [sys_properties] table

**-** Learn more: Tracking AI-generated code

sn_now_assist_code.collect_schema_for_code_assist Specifies whether to collect the data schema of the table, a business rule, or client script runs when using code generation. If you set this property to false, you can receive code suggestions faster but may get fewer contextual suggestions.

**-** Type: true | false

**-** Default value: true

**-** Location: System Property [sys_properties] table

Now Assist for Code roles

Understand the roles needed to use Now Assist for Code. These roles are created when Now Assist for Creator is installed.

To learn more about managing subscriptions for individual users, see Managing per-user subscriptions in Subscription Management and contact your account representative for assistance.

##### Now Assist Creator [now.assist.creator]

Write scripts using AI-powered code generation.

Groups

This role is not assigned to any groups by default.

Contains Roles

This role contains no roles.

Elevated

This role is not an elevated role.

Special considerations

None

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 37

Keyboard shortcuts

Learn about the keyboard shortcuts that you can use in the script editor on the ServiceNow AI Platform ® .

Keyboard shortcuts

Action Windows Mac

View full screen Control+Alt+Enter Command+Option+Enter

Format Control+Alt+L Command+Option+L

Toggle comment Control+Option+/ Command+Option+/

Start search Control+F Command+F

Find next Control+G Command+G

Find previous Control+Shift+G Command+Shift+G

Replace Control+Alt+K Command+Alt+K

Replace all Control+Alt+R Command+Alt+R

Open Generate code with Now Assist dialog box

Control+Enter Command+Enter

##### JavaScript syntax editor

The syntax editor provides support for editing JavaScript scripts.

The syntax editor has these features.

**-** JavaScript syntax coloring, indentation, line numbers, and automatic creation of closing braces and quotes

**-** JavaScript support

**-** Linting using the ESLint utility

##### Note: Modify or view default linting configurations by accessing the

###### glide.ui.syntax_editor.linter.eslint_config property in the System

Property [sys_properties] table. See Available system properties for more information.

**-** Context menu for script includes, API, and tables

**-** Script macros for common code shortcuts

This feature requires the Syntax Editor (com.glide.syntax_editor) plugin.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 38

JavaScript editor

Syntax editor plugin

Enable the syntax editor plugin to use the syntax editor.

The syntax editor enables the following features for all script fields:

**-** JavaScript syntax coloring, indentation, line numbers, and automatic creation of closing braces and quotes

**-** Code editing functions

**-** Code syntax checking

**-** Script macros for common code shortcuts

JavaScript syntax editor

The syntax editor can be disabled or enabled by modifying the

###### glide.ui.javascript_editor property in the sys_properties.list. In

addition, administrators can configure the syntax editor to show error and warning indicators next to a line of code that contains an error by modifying the

###### glide.ui.syntax_editor.show_warnings_errors property. For information on the

sys_properties.list, refer to Available system properties.

##### Note: Administrators can disable or enable the syntax editor for all users, regardless of

user preference.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 39

Syntax editor JavaScript support

The syntax editor provides editing functions to support editing JavaScript scripts.

##### JavaScript editing functions

Icon

Keyboard Shortcut

Name Description

N/A Toggle Syntax Editor

Disables the syntax editor. Click the button again to enable the syntax editor.

Access Key + R

Format Code

Applies the proper indentation to the script.

Access Key + C

Comment Selected Code

Comments out the selected code.

Access Key + U

Uncomment Selected Code

Removes comment codes from the selected code.

N/A Check Syntax

Checks the code for syntax errors. By default, the system automatically checks for syntax errors as you type in a script field. If an error or warning is found, the syntax editor displays a bullet beside the script line containing the error or warning. This check occurs on all script fields.

Access Key + \

Start Searching

Highlights all occurrences of a search term in the script field and locates the first occurrence. Click the icon, then enter the search term and press Enter. You can use regular expressions enclosed in slashes to define the search term. For example, the term /a{3}/ locates aaa.

Access Key + [

Find Next Locates the next occurrence of the current search term in the script field. Use Start Searching to change the current search term.

Access Key + ]

Find Previous

Locates the previous occurrence of the current search term in the script field. Use Start Searching to change the current search term.

Access Key + W

Replace Replaces the next occurrence of a text string in the script field.

**1.** Click the icon, then enter the string to replace and press **Enter**. You can use regular expressions enclosed in slashes to define the string to replace. For example, the term _/a{3}/_ locates _aaa_.

**2.** Enter the replacement string and press **Enter**.

Access Key + ;

Replace All Replaces all occurrences of a text string in the script field.

**1.** Click the icon, then enter the string to replace and press **Enter**. You can use regular expressions enclosed in slashes to define the string to replace. For example, the term _/a{3}/_ locates _aaa_.

**2.** Enter the replacement string and press **Enter**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 40

Icon

Keyboard Shortcut

Name Description

N/A Save Saves changes without leaving the current view. Use this button in full screen mode to save without returning to standard form view.

Access Key + L

Toggle Full Screen Mode

Expands the script field to use the full form view for easier editing. Click the button again to return to standard form view. This feature is not available for Internet Explorer.

Access Key + P

Help Displays the keyboard shortcuts help screen.

##### JavaScript editing tips

**-** To fold a code block, click the minus sign beside the first line of the block. The minus sign only appears beside blocks that can be folded. To unfold the code block, click the plus sign.

**-** To insert a fixed space anywhere in your code, press Tab.

**-** To indent a single line of code, click in the leading white space of the line and then press Tab.

**-** To indent one or more lines of code, select the code and then press Tab. To decrease the indentation, press Shift + Tab.

**-** To remove one tab from the start of a line of code, click in the line and press Shift + Tab.

##### JavaScript resources

Scripts use ECMA 262 standard JavaScript. Helpful resources include:

**-** Mozilla: [http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Reference](http://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Reference)

**-** ECMA Standard in PDF format: [http://www.ecma-international.org/publications/files/ECMA-](http://www.ecma-international.org/publications/files/ECMA-) ST/Ecma-262.pdf

**-** History and overview: [http://javascript.crockford.com/survey.html](http://javascript.crockford.com/survey.html)

**-** JavaScript number reference: [http://www.hunlock.com/blogs/](http://www.hunlock.com/blogs/) The_Complete_Javascript_Number_Reference

Syntax editor keyboard shortcuts and actions

The syntax editor offers keyboard shortcuts and actions to assist in writing code.

Syntax editor keyboard shortcuts and actions for writing code

Keyboard shortcut or action

Description Example

Write code

Scripting assistance

Control +Spacebar

Displays a list of valid elements at the insertion point such as:

**-** Class names

**-** Function names

**-** Object names

**-** Variable names

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 41

Syntax editor keyboard shortcuts and actions for writing code (continued)

Keyboard shortcut or action

Description Example

Double-click an entry to add it to the script.

##### Note: The elements

are based on server or client type of script. However, these elements are available based on the UI type you select. For example, spUtil is available for Service Portal client scripts and g_navigation is available for Desktop scripts.

Enter a period character after a valid class name.

Displays a list methods for the class.

Double-click an entry to add it to the script.

Enter an open parenthesis character after a valid class, function, or method name.

Displays the expected parameters for the class or method.

Enter the expected parameters as needed.

Toggle full screen mode

Control+M

Switches between displaying the form with the full screen and displaying it normally.

Format code

**-** Windows: Control +Shift+B

**-** Mac: Command +Shift+B

Formats the selected lines to improve readability.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 42

Syntax editor keyboard shortcuts and actions for writing code (continued)

Keyboard shortcut or action

Description Example

Toggle comment

**-** Windows: Control+/

**-** Mac: Command +/

Adds or removes the comment characters // from the selected lines.

Insert macro text

**1.** In the **Script** field, type the macro keyword text. For example help.

**2.** Press Tab.

Inserts macro text at the current position.

Search

Start search

**-** Windows: Control+F

**-** Mac: Command +F

Highlights all occurrences of a search term in the script field and locates the first occurrence.

You can create regular expressions by enclosing the search terms between slash characters. For example, the search term /a{3}/ locates the string aaa.

Find next

**-** Windows: Control+G

**-** Mac: Command +G

Locates the next occurrence of the current search term in the script field. Use Start Searching to change the current search term.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 43

Syntax editor keyboard shortcuts and actions for writing code (continued)

Keyboard shortcut or action

Description Example

Find previous

**-** Windows: Control +Shift+G

**-** Mac: Command +Shift+G

Locates the previous occurrence of the current search term in the script field. Use Start Searching to change the current search term.

Replace

**-** Windows: Control+E

**-** Mac: Command +E

Replaces the next occurrence of a text string in the script field.

Replace all

**-** Windows: Control+;

**-** Mac: Command +;

Replaces all occurrences of a text string in the script field.

Help

Help

**-** Windows: Control+H

**-** Mac: Command +H

Displays the list of syntax editor keyboard shortcuts.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 44

Syntax editor keyboard shortcuts and actions for writing code (continued)

Keyboard shortcut or action

Description Example

Show description

**-** Windows: Control+J

**-** Mac: Command +J

Displays API documentation for the scripting element at the cursor's current location.

Show macros

**1.** In the **Script** field, type help.

**2.** Press Tab.

Displays the list of available syntax editor macros as text within the script field.

Syntax editor macros

Script macros provide shortcuts for typing commonly used code. To insert macro text into a script field, enter the macro keyword followed by the Tab.

Syntax editor macros are defined in the Editor Macros [syntax_editor_macro] table. To create or modify a script macro, see Create or modify a script macro.

vargr

**-** Inserts a standard GlideRecord query for a single value.

**-** Output:

var gr = new GlideRecord("$0"); gr.addQuery("name", "value"); gr.query(); if (gr.next()) {

}

vargror

**-** Inserts a GlideRecord query for two values with an OR condition.

**-** Output:

var gr = new GlideRecord('$0');

var qc = gr.addQuery('field', 'value1');

qc.addOrCondition('field', 'value2'); gr.query();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 45

while (gr.next()) {

}

for

**-** Inserts a standard recursive loop with an array.

**-** Output:

for (var i=0; i< myArray.length; i++) { //myArray[i];

}

info

**-** Inserts a GlideSystem information message.

**-** Output:

gs.addInfoMessage("");

method

**-** Inserts a blank JavaScript function template.

**-** Output:

/_************************\_\_\_\_************************ ******\_****** _ Description: _ Parameters: _ Returns:

**************************\_************************** ****\_\_\_****\*/ : function() {

},

doc

**-** Inserts a comment block for describing a function or parameters.

**-** Output:

/\*\*

- Description:

- Parameters:

- Returns: \*/

Create or modify a script macro

Administrators can define new script macros or modify existing script macros.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 46

###### Before you begin

Role required: admin

###### About this task

Script macros provide shortcuts for typing commonly used code. Several script macros are available by default. Administrators can define new or modify existing script macros.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Syntax Editor Macros**.

**2.** Click **New** or select the macro to edit.

**3.** Define the macro details with the fields listed in the table below.

Editor macro fields

Field Description

Name Macro keyword text users type to insert macro text.

Comments Description of the macro. This text appears when the user types help.

Text Full macro text that replaces the name in the editor.

Context menu in the syntax editor

View the context menu for script includes, Glide APIs, and tables in the JavaScript syntax editor.

With the context menu options, your users can navigate to:

**-** Script include definitions

**-** Glide API documentation

**-** System and custom table definitions and data

In the syntax editor, bold font is used for tokens that have a context menu. Right-click the token to view context menu options. If you use a Mac, you can use the Command-click shortcut.

Context menu options

Token type Context menu option Description

Open Definition Definition of the script include in a new window.

Script include

Find References List of files referencing the script include.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 47

Context menu options (continued)

Token type Context menu option Description

##### Note:

**-** To view the preview of the file, click the

preview script icon.

To open the file in a new window, click Open File.

**-** To view all files that reference the script include, click **Show All** **Files**.

Glide API Show Documentation Documentation page of the Glide API.

Show Definition Definition of the system or custom table in a new window.

Table

Show Data Records in the table that are based on the role of the current user.

Enable or disable the context menu in the script editor using the

###### glide.ui.syntax_editor.context_menu property in the System Property

[sys_properties] table. See Available system properties for more information.

##### Note: Context menu options can be accessed only if the browser supports SharedWorker.

For example, Google Chrome and Mozilla Firefox.

Script syntax error checking

All script fields provide controls for checking the syntax for errors and for locating the error easily when one occurs. The script editor places the cursor at the site of a syntax error and lets you search for errors in scripts by line number.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 48

Script syntax check

The script editor notifies you of syntax errors in your scripts in the following situations.

**-** Save a new record or update an existing record. A banner appears at the bottom of the editor showing the location of the first error (line number and column number), and the cursor appears at the site of the error. Warnings presented at **Save** or **Update** show only one error at a time.

Script syntax error (short)

**-** Click the syntax checking icon before saving or updating a record. A banner appears at the bottom of the editor showing the location of all errors in the script, and the cursor appears at the site of the first error.

Script syntax error

Searching for errors by line

To locate the exact position of the error in a large script, click the Go to line icon.

This feature is particularly useful when you are encounter a syntax error in a log file rather than in the ServiceNow record itself. In this case, you can navigate to the record and search for errors by line number. In the dialog box that appears, enter the line number of an error, and then click OK. Your view moves to the site of the error, and the cursor marks the correct line and column.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 49

##### Note: For this feature to function, you must disable the Syntax Editor.

Go to script error

Navigate to a line number

When the syntax editor is disabled, users can navigate to a specific line in the code using the Go to line icon ( ).

###### Before you begin

Disable the Syntax Editor.

Role required: admin

###### Procedure

**1.** Click the Go to line icon ( ).

##### Note: This icon is not available when the editor is enabled.

**2.** Enter a number in the field and then press **Enter**.

##### HTML syntax editor

The HTML syntax editor provides support for editing HTML and Jelly scripts and defines what's rendered when the page is displayed. The HTML syntax editor can contain either static XHTML or dynamically generated content defined as Jelly, and can call script includes and UI Macros.

The syntax editor has these features.

**-** HTML and Jelly script support

**-** HTML and Jelly syntax coloring, indentation, line numbers, and automatic creation of closing braces and quotes

**-** Auto-suggestions for HTML and Jelly tags

**-** Script macros for common code shortcuts

HTML syntax editor

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 50

HTML and Jelly editing functions

Icon

Keyboard shortcut

Name Description

N/A Toggle syntax editor

Disables the syntax editor. Click the Toggle syntax editor icon ( ) again to enable the syntax editor.

Cmd+/ Toggle comment

Comments the selected code.

Cmd+E Replace Replaces the next occurrence of a text string in the script field.

**1.** Click the Replace icon ( ), then enter the string to replace, and press⌘Enter. You can use regular expressions enclosed in slashes to define the string to replace. For example, the term/a{3}/ locatesaaa.

**2.** Enter the replacement string and press⌘Enter.

Cmd Replace All

Replaces all occurrences of a text string in the script field.

**1.** Click the Replace all icon ( ), then enter the string to replace and press⌘Enter. You can use regular expressions enclosed in slashes to define the string to replace. For example, the term/a{3}/ locatesaaa.

**2.** Enter the replacement string and press⌘Enter.

Cmd+F Start Searching

Highlights all occurrences of a search term in the script field and

locates the first occurrence. Click the Start searching icon ( ), then enter the search term and press Enter.

Cmd+G Find Next Locates the next occurrence of the current search term in the script

field. Click the Start searching icon ( ) to change the current search term.

Cmd +Shift +G

Find Previous

Locates the previous occurrence of the current search term in

the script field. Click the Start searching icon ( ) to change the current search term.

Ctrl+M Toggle Full Screen

Expands the script field to use the full form view for easier editing.

Click the Toggle full screen icon ( ) again to return to standard form view. This feature is not available for Internet Explorer.

Cmd+H Help Displays the keyboard shortcuts help screen.

N/A Save Saves changes without leaving the current view. Click the Save icon

( ) in full screen mode to save without returning to standard form view.

##### Editing tips

**-** To insert a fixed space anywhere in your code, press Tab.

**-** To indent a single line of code, click in the leading white space of the line and then press Tab.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 51

**-** To indent one or more lines of code, select the code and then press Tab. To decrease the indentation, press Shift+Tab.

**-** To remove one tab from the start of a line of code, click in the line and press Shift+Tab.

##### Code editor

The code editor provides support to use programming language services in a text editor and is used in scripts.

The code editor has these features for the supported language services and Inline scripts.

**-** Syntax coloring, indentation, line numbers, and automatic creation of closing braces and quotes

**-** Auto-suggestions and auto-completions

Code editor

##### Editing tips

**-** To insert a fixed space anywhere in your code, press Tab.

**-** To indent a single line of code, click in the leading white space of the line and then press Tab.

**-** To indent one or more lines of code, select the code and then press Tab. To decrease the indentation, press Shift+Tab.

**-** To remove one tab from the start of a line of code, click in the line and press Shift+Tab.

**-** To declare variables, use the var keyword so that they remain within the proper JavaScript scope.

##### Server-side scripting

Server scripts run on the server or database. They can change the appearance or behavior of ServiceNow or run as business rules when records and tables are accessed or modified.

Server-side Glide APIs (Application Programming Interfaces) provide classes and methods that you can use in scripts to perform server-side tasks.

##### Immediately invoked function expressions

The system uses immediately invoked function expressions when a script runs in a single context, such as in a Create a transform map. Functions that run from multiple contexts use Script includes instead.

By enclosing a script in an immediately invoked function expression, you can:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 52

**-** Ensure that the script does not impact other areas of the product, such as by overwriting global variables.

**-** Pass useful variables or objects as parameters.

**-** Identify function names in stack traces.

**-** Eliminate having to make separate function calls.

An immediately invoked function expression follows this format:

(function functionName(parameter){

//The script you want to run

})('value');//Note the parenthesis indicating this function should run.

You can declare functions within the immediately invoked function expression. These inner functions are accessible only from within the immediately invoked function expression.

(function functionName(parameter){

function helperFunction(parameter){//return some value}

var value = helperFunction(parameter);//Valid function call.

//perform any other script actions

})('value');

var value2 = helperFunction(parameter);//Invalid. This function is not accessible from outside the self-executing function.

Glide Server APIs

ServiceNow provides APIs for the Glide Server.

GlideAggregate

###### The GlideAggregate class is an extension of GlideRecord and allows database

aggregation (COUNT, SUM, MIN, MAX, AVG) queries to be done. This can be helpful in creating customized reports or in calculations for calculated fields.

##### Note: This functionality requires a knowledge of JavaScript.

For additional information, refer to GlideAggregate API.

GlideAggregate examples

###### GlideAggregate is an extension of GlideRecord and its use is probably best shown

through a series of examples.

##### Note: This functionality requires a knowledge of JavaScript.

Here is an example that simply gets a count of the number of records in a table:

var count = new GlideAggregate('incident'); count.addAggregate('COUNT'); count.query(); var incidents = 0;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 53

if(count.next()) incidents = count.getAggregate('COUNT');

There is no query associated with the preceding example. If you want to get a count of the

###### incidents that were open, simply add a query as is done with GlideRecord. Here is an

example to get a count of the number of active incidents.

var count = new GlideAggregate('incident'); count.addQuery('active','true'); count.addAggregate('COUNT'); count.query(); var incidents = 0; if(count.next()) incidents = count.getAggregate('COUNT');

To get a count of all the open incidents by category the code is:

var count = new GlideAggregate('incident'); count.addQuery('active','true'); count.addAggregate('COUNT','category'); count.query(); while(count.next()){ var category = count.category; var categoryCount = count.getAggregate('COUNT','category'); gs.log("The are currently "+ categoryCount +" incidents with a category of "+ category);}

The output is:

**_ Script: The are currently 1.0 incidents with a category of Data _** Script: The are currently 11.0 incidents with a category of Enhancement **_ Script: The are currently 1.0 incidents with a category of Implementation _** Script: The are currently 197.0 incidents with a category of inquiry **_ Script: The are currently 13.0 incidents with a category of Issue _** Script: The are currently 1.0 incidents with a category of \*\*\* Script: The are currently 47.0 incidents with a category of request

The following is an example that uses multiple aggregations to see how many times records have

###### been modified using the MIN, MAX, and AVG values.

var count = new GlideAggregate('incident'); count.addAggregate('MIN','sys_mod_count'); count.addAggregate('MAX','sys_mod_count'); count.addAggregate('AVG','sys_mod_count'); count.groupBy('category'); count.query(); while(count.next()){ var min = count.getAggregate('MIN','sys_mod_count'); var max = count.getAggregate('MAX','sys_mod_count'); var avg = count.getAggregate('AVG','sys_mod_count');

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 54

var category = count.category.getDisplayValue(); gs.log(category +" Update counts: MIN = "+ min +" MAX = "+ max +" AVG = "+ avg);}

The output is:

**_ Script: Data Import Update counts: MIN = 4.0 MAX = 21.0 AVG = 9.3333 _** Script: Enhancement Update counts: MIN = 1.0 MAX = 44.0 AVG = 9.6711 **_ Script: Implementation Update counts: MIN = 4.0 MAX = 8.0 AVG = 6.0 _** Script: inquiry Update counts: MIN = 0.0 MAX = 60.0 AVG = 5.9715 **_ Script: Inquiry / Help Update counts: MIN = 1.0 MAX = 3.0 AVG = 2.0 _** Script: Issue Update counts: MIN = 0.0 MAX = 63.0 AVG = 14.9459 **_ Script: Monitor Update counts: MIN = 0.0 MAX = 63.0 AVG = 3.6561 _** Script: request Update counts: MIN = 0.0 MAX = 53.0 AVG = 5.0987

The following is a more complex example that shows how to compare activity from one month to the next.

var agg = new GlideAggregate('incident'); agg.addAggregate('count','category'); agg.orderByAggregate('count','category'); agg.orderBy('category'); agg.addQuery('opened_at','>=','javascript:gs.monthsAgoStart(2) '); agg.addQuery('opened_at','<=','javascript:gs.monthsAgoEnd(2)'); agg.query(); while(agg.next()){ var category = agg.category; var count = agg.getAggregate('count','category'); var query = agg.getQuery(); var agg2 = new GlideAggregate('incident'); agg2.addAggregate('count','category'); agg2.orderByAggregate('count','category'); agg2.orderBy('category');

agg2.addQuery('opened_at','>=','javascript:gs.monthsAgoStart(3) ');

agg2.addQuery('opened_at','<=','javascript:gs.monthsAgoEnd(3) '); agg2.addEncodedQuery(query); agg2.query(); var last =""; while(agg2.next()){ last = agg2.getAggregate('count','category');} gs.log(category +": Last month:"+ count +" Previous Month:"+ last);

}

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 55

The output is:

**_ Script: Monitor: Last month:6866.0 Previous Month:4468.0 _** Script: inquiry: Last month:142.0 Previous Month:177.0 **_ Script: request: Last month:105.0 Previous Month:26.0 _** Script: Issue: Last month:8.0 Previous Month:7.0 **_ Script: Enhancement: Last month:5.0 Previous Month:5.0 _** Script: Implementation: Last month:1.0 Previous Month:0

The following is an example to obtain distinct count of a field on a group query.

var agg = new GlideAggregate('incident'); agg.addAggregate('count'); agg.addAggregate('count(distinct','category'); agg.addQuery('opened_at', '>=', 'javascript:gs.monthsAgoStart(2)'); agg.addQuery('opened_at', '<=', 'javascript:gs.monthsAgoEnd(2)'); // agg.groupBy('priority'); agg.query(); while (agg.next()) { // Expected count of incidents and count of categories within each priority value (group) gs.info('Incidents in priority ' + agg.priority + ' = ' + agg.getAggregate('count') + ' (' + agg.getAggregate('count(distinct','category') + ' categories)'); }

The output is:

**_ Script: Incidents in priority 1 = 13 (3 categories) _** Script: Incidents in priority 2 = 10 (5 categories) **_ Script: Incidents in priority 3 = 5 (3 categories) _** Script: Incidents in priority 4 = 22 (6 categories)

###### You can implement the SUM aggregate with or without the use of the groupBy() method. If

###### you do not use the groupBy() method, the result of the SUM is the cumulative value for each

different value of the field for which you request the SUM. For example, if you SUM the total_cost field in the Fixed Asset table, and the Fixed Asset table contains 12 total records:

**-** Three records with a total_cost of $12

**-** Four records with a total_cost of $10

**-** Five records with a total_cost of $5

###### When you SUM the record set, the getAggregate() method returns three different sums:

$36, $40, and $25.

###### The following code illustrates implementing the SUM aggregate without using the groupBy()

method:

var totalCostSum = new GlideAggregate('fixed_asset'); totalCostSum.addAggregate('SUM', 'total_cost'); totalCostSum.query();

while (totalCostSum.next()) { © 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 56

var allTotalCost = 0; allTotalCost = totalCostSum.getAggregate('SUM', 'total_cost'); aTotalCost = totalCostSum.getValue('total_cost'); gs.print('Unique field value: ' + aTotalCost + ', SUM = ' + allTotalCost + ', ' + allTotalCost/aTotalCost + ' records'); }

The output for this example is:

**_ Script: Unique field value: 12, SUM = 36, 3 records _** Script: Unique field value: 10, SUM = 40, 4 records \*\*\* Script: Unique field value: 5, SUM = 25, 5 records

###### Using the same data points as the prior example, if you use the groupBy() method, the SUM

aggregate returns the sum of all values for the specified field.

###### The following example illustrates implementing the SUM aggregate using the groupBy()

method:

var totalCostSum = new GlideAggregate('fixed_asset'); totalCostSum.addAggregate('SUM', 'total_cost'); totalCostSum.groupBy('total_cost'); totalCostSum.query(); if(totalCostSum.next()){ // in case there is no result var allTotalCost = 0; allTotalCost = totalCostSum.getAggregate('SUM', 'total_cost'); gs.print('SUM of total_cost: = ' + allTotalCost); }

The output for this example is:

\*\*\* Script: SUM of total_cost: 101

GlideRecord

###### GlideRecord is a special Java class ( GlideRecord.java) that can be used in JavaScript

exactly as if it was a native JavaScript class.

###### GlideRecord:

**-** is used for database operations instead of writing SQL queries.

**-** is an object that contains zero or more records from one table. Another way to say this is that a GlideRecord is an ordered list.

A GlideRecord contains both records (rows) and fields (columns). The field names are the same as the underlying database column names. For additional information, refer to GlideRecord Scoped.

##### Note: Use of gs.sql()) scripting syntax was discontinued in Geneva. Use standard

###### GlideRecord syntax in its place.

Using GlideRecordSecure

###### GlideRecordSecure is a class inherited from GlideRecord that performs the same

###### functions as GlideRecord, and also enforces ACLs.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 57

##### Non-writable fields

###### Be aware that, when using GlideRecordSecure, non-writable fields are set to NULL when

###### trying to write to the database. By default, canCreate() on the column is replaced with

###### canWrite() on the column. If that returns false, the column value is set to NULL.

##### Checking for NULL values

If an element cannot be read because an ACL restricts access, a NULL value is created in memory for that record. With GlideRecord, you must explicitly check for any ACLs that might restrict read access to the record. To do so, an if statement such as the following is required to check if the record can be read:

if ( !grs.canRead() ) continue;

###### With GlideRecordSecure, you do not need to explicitly check for read access using

###### canRead(). Instead, you can use next() by itself to move to the next record. The following

###### example provides a comparison between GlideRecord and GlideRecordSecure.

var count = 0; var now_GR = new GlideRecord('mytable'); now_GR. query(); while (now_GR. next()) { if (!now_GR. canRead()) continue; if (!now_GR. canWrite()) continue; if (!now_GR. val. canRead() || !now_GR. val. canWrite()) now_GR. val = null; else now_GR. val = "val-" + now_GR. id; if (now_GR. update()) count ++; }

var count = 0; var grs = new GlideRecordSecure('mytable'); grs. query(); while (grs. next()) { grs. val = "val-" + grs. id; if (grs. update()) count ++; }

##### Examples

###### These are two simple examples using GlideRecordSecure.

var att = new GlideRecordSecure ('sys_attachment'); att. get('$[sys_attachment.sys_id]'); var sm = GlideSecurityManager.get(); var checkMe = 'record/sys_attachment/delete'; var canDelete = sm.hasRightsTo(checkMe,att); gs. log('canDelete: ' + canDelete); canDelete;

var grs = new GlideRecordSecure('task_ci'); grs.addQuery(); grs.query();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 58

var count = grs. getRowCount(); if (count > 0 ) { var allocation = parseInt(10000/count) / 100; while (grs.next()) { grs.u_allocation = allocation; grs.update(); } }

GlideSystem

###### The GlideSystem API provides methods for retrieving information.

###### The GlideSystem (referred to by the variable name ' gs' in business rules) provides a number

of convenient methods to get information about the system, the current logged in user, etc. For

###### example, the method addInfoMessage() permits communication with the user.

gs.addInfoMessage('Email address added for notification');

###### Many of the GlideSystem methods facilitate the easy inclusion of dates in query ranges and

are most often used in filters and reporting.

For additional information, see GlideSystem.

GlideDateTime

###### The GlideDateTime class provides methods for performing operations on GlideDateTime

###### objects, such as instantiating GlideDateTime objects or working with glide_date_time

fields.

In addition to the instantiation methods described below, a GlideDateTime object can be

###### instantiated from a glide_date_time field using the getGlideObject() method (for

example, var gdt = gr.my_datetime_field.getGlideObject();).

Some methods use the Java Virtual Machine time zone when retrieving or modifying a date and time value. Using these methods may result in unexpected behavior. Use equivalent local time and UTC methods whenever possible.

GlideDate and GlideDateTime examples

###### The GlideDate and GlideDateTime APIs are used to manipulate date and time values.

##### Note: This functionality requires a knowledge of JavaScript.

For additional information, refer to GlideDate API and GlideDateTime API.

###### You can create a GlideDateTime object from a GlideDate object by passing in the

###### GlideDate object as a parameter to the GlideDateTime constructor. By default, the

###### GlideDateTime object is expressed in the internal format, yyyy-MM-dd HH:mm:ss and the

system time zone UTC.

var gDate = new GlideDate(); gDate.setValue('2015-01-01'); gs.info(gDate);

var gDT = new GlideDateTime(gDate); gs.info(gDT);

Output:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 59

2015-01-01 2015-01-01 00:00:00

See also Modify a GlideDateTime field value.

Set a duration field value in script

Examples of JavaScript that can be used to set the value of a duration field.

##### Note: Negative duration values are not supported.

##### Using the GlideDateTime.subtract() method

###### The subtract(GlideDateTime start, GlideDateTime end) method in

GlideDateTime enables you to set the duration value using a given start date/time and end date/ time. An example on how to set the duration for the time a task was opened is:

var duration = GlideDateTime.subtract(start, end);

If you want to work with the value returned as a number to use in date or duration arithmetic, convert the return to milliseconds:

var time = GlideDateTime.subtract(start,end).getNumericValue();

If you want to set a duration to the amount of time between some event and the current date/ time:

<duration_field> = GlideDateTime.subtract(new GlideDateTime(<start_time>.getValue()),gs.nowDateTime());

###### The time values presented to GlideDateTime.subtract are expected to be in the user's

time zone and in the user's format.

##### Setting a default value of a duration field

Setting the default value for a duration field is similar to the method used in the previous topic.

##### Setting the duration field value in a client script

###### This script sets a duration_field value in a client script. Replace duration_field with

the field name from your instance.

g_form.setValue('<duration_field>','11 01:02:03');

##### Calculating and setting a duration using a client script

Here is an example of how to return a value and populate it using a client script.

Create an onChange client script that includes the following code. You can modify this script if you need the calculation to happen in an onLoad script or some other way.

function onChange(control, oldValue, newValue, isLoading){ var strt = g_form.getValue('<start_field>'); var end = g_form.getValue('<end_field>'); var ajax = new GlideAjax('AjaxDurCalc'); ajax.addParam('sysparm_name','durCalc'); ajax.addParam('sysparm_strt',strt); ajax.addParam('sysparm_end',end); ajax.getXMLWait();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 60

var answer = ajax.getAnswer(); g_form.setValue('<duration_field>', answer);}

###### Create a system script include file called AjaxDurCalc that handles the request. It may be

reused for other functions as well.

var AjaxDurCalc = Class.create(); AjaxDurCalc.prototype = Object.extendsObject(AbstractAjaxProcessor,{ durCalc:function(){return GlideDuration.subtract(this.getParameter('sysparm_strt'),this.g etParameter('sysparm_end'));}});

##### Changing the duration field value

If you manipulate a duration value with addition/subtraction of some amount of time, use the functions that allow you to get and set the numeric value of the duration. A unit of measure for a duration numeric value is milliseconds. The following is an example that adds 11 seconds to the

###### duration field in the current record.

var timems = current.duration.dateNumericValue(); timems = timems + 11\*1000; current.duration.setDateNumericValue(timems);

##### Formatting the Resolve Time

To format the Resolve Time or the Business Resolve Time fields as durations, which displays them as a duration instead of a large integer, add the following attribute to those fields:

format=glide_duration

Modify the dictionary entry for the field and add the attribute. If there is an existing attribute, separate multiple attributes with commas.

##### Setting the maximum unit of measurement

###### The max_unit dictionary attribute defines the maximum unit of time used in a duration. For

example, if max_unit=minutes, a duration of 3 hours 5 minutes 15 seconds appears as 185 minutes 15 seconds. To set the maximum unit of duration measurement, add the following

###### dictionary attribute to the duration field:

max_unit=<unit>

Date and time format guidelines

You can specify a date format with a sequence of specific date and time pattern strings. A pattern string consists of one or more uppercase and lowercase letters from A to Z. Any text within quotation marks is ignored and is instead copied into the date output.

String Description Output Format Example

G Era designator Text AD

y Year Year 2019; 19

Y Week in year Year 2019; 19

M Month in year (within date) Month July; Jul; 07

L Month in year (standalone value) Month July; Jul; 07

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 61

String Description Output Format Example

w Week in year Number 52

W Week in month Number 1

D Day in year Number 365

d Day in month Number 2

F Day of week in month Number 3

E Day name in week Text Wednesday; Wed

u Day number of week Number 3

a a.m. or p.m. Text p.m.

H Hour in day from 0 through 23 Number 0

k Hour in day from 1 through 24 Number 24

K Hour in a.m. or p.m. from 0 through 11

Number 0

h Hour in a.m. or p.m. from 1 through 12

Number 12

m Minute in hour Number 59

s Second in minute Number 1

S Millisecond Number 500

z Time zone in default format Time zone in default format

Pacific Standard Time; PST

Z Time zone in RFC 822 format Time zone in RFC 822 format

-0800

X Time zone in ISO 8601 format Time zone in ISO 8601 format

-08; -0800; -08:00

Classic Business rules

A business rule is a server-side script that runs when a record is displayed, inserted, updated, or deleted, or when a table is queried.

Business rules are scripts that run when certain server-side conditions are met. Business rule conditions include when to run a business rule in relation to a database operation, and what record operations the business rule applies to. There are other scripting options available on the platform for client-side conditions, such as client scripts and UI actions.

##### Note: Business rules are a classic automation solution that rely on scripting. Use Workflow

Studio for any new process automation to create automations that are easier to extend, reuse, understand, and upgrade. As many organizations have business rules in production, use this documentation to learn how to work with existing business rules.

How business rules work

To configure business rules, you first need to determine when the business rule should run and what action it should take.

##### When business rules run

Business rules run based on two sets of criteria.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 62

**-** When to run the business rule in relation to a database operation.

**-** What record operation the business rule applies to.

The following options are provided to determine when the business rule should run.

When the business rule should run

Option When the rule runs

Before After the user submits the form but before any action is taken on the record in the database.

After After the user submits the form and after any action is taken on the record in the database.

Async After the user submits the form and after the scheduler runs the scheduled job created from the business rule. The system creates a scheduled job from the business rule after the user submits the form but before any action is taken on the record in the database.

##### Note: Newly created business rules will run during upgrades.

If a record has an asynchronous business rule that makes decisions based on the data in the record, multiple updates to the record in quick succession can cause the business rule to execute out of order or incorrectly.

If multiple async business rules update the same record, the updates performed by one script could be overwritten by another script or made in an unexpected sequence because the order of execution isn't guaranteed. You can use the After option for business rules or System Events as an alternative in these situations.

Display Before the form is presented to the user, just after the data is read from the database.

##### Note:

**-** Asynchronous business rules do not have access to the previous version of a record.

###### Therefore, the changes(), changesTo(), and changesFrom() GlideElement

methods do not work with async rule script. However, the condition builder and

###### condition field (advanced view) both support the changes(), changesTo(), and

###### changesFrom() methods.

**-** Business rules do not honor ACLs until you want them to be honored. For more information, see Relationship between Business Rules and Access Control Rules (ACLs)

The following options are provided to determine what record operations the business rule applies to.

What record operation the business rule applies to

Option When the rule runs

Insert When the user creates a new record and the system inserts it into the database.

Update When the user modifies an existing record.

Query When the user sends a query for a record or list of records to the database. Typically you should use query operation for before business rules.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 63

What record operation the business rule applies to (continued)

Option When the rule runs

Delete When the user deletes a record.

##### Note: Business rules only run record operations when called from the GlideRecord

API. Some applications intentionally bypass business rule processing to perform record operations directly. In addition, business rules ignore API calls run with the setWorkflow() method set to false.

This image shows when different types of business rules run:

Business rule processing flow

##### Note: Business rules apply consistently to records regardless of whether they are

accessed through forms, lists, or web services. This is one major difference between business rules and client scripts, which apply only when the form is edited.

##### Business rule actions

Business rules can perform a variety of actions. Common types of actions are:

**-** Changing field values on a form that the user is updating. Field values can be set to specific values available for that field, values copied from other fields, and relative values determined by the user's role.

**-** Displaying information messages to the user.

**-** Changing values of child tasks based on changes to parent tasks.

**-** Preventing users from accessing or modifying certain fields on a form.

**-** Aborting the current database transaction. For example, if certain conditions are met, prevent the user from saving the record in the database.

Administrators can set field values, create information messages, and abort transactions without writing a script.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 64

##### Prevent recursive business rules

###### Avoid using current.update() in a business rule script. The update() method triggers

business rules to run on the same table for insert and update operations, leading to a business rule calling itself over and over. Changes made in before business rules are automatically saved when all before business rules are complete, and after business rules are best used for updating related, not current, objects. When a recursive business rule is detected, the system stops it and

###### logs the error in the system log. However, current.update() causes system performance

issues and is never necessary.

###### You can prevent recursive business rules by using the setWorkflow() method with the

###### false parameter. The combination of the update() and setWorkflow() methods is

only recommended in special circumstances where the normal before and after guidelines mentioned above don't meet your requirements.

Business rules in scoped applications

Every business rule is assigned to either a private application scope or to the global scope.

The types of business rules you can create and how you can access those rules varies depending on the scope of the business rule and the scope of the table it runs on.

##### Note: The term global can refer to two different aspects of a business rule: the table it runs

on and the scope it runs in. Business rules can either run on specific tables or be global. In addition, they can be in the global scope or in a private application scope.

##### Business rules on specific tables

Most business rules run on a specific table, which is defined in the Table field. You can create business rules on tables in the same scope and on tables that allow configuration records from another application scope.

For tables that are in a different scope than the business rule record, the types of rules are limited.

**-** You can create a rule where **When is async** with any of the following options:

◦ Insert , Update , and Delete database operations. You cannot select Query.

◦ Set field values actions and scripts (the Script field).

**-** You can create a rule where When is before with any of the following options:

◦ Insert , Update , and Delete database operations. You cannot select Query.

◦ Set field values actions only. You cannot write scripts and you cannot abort the database transaction.

**-** You cannot create any other types of business rules on tables in a different scope.

Business rules on specific tables cannot be accessed by other business rules or scripts.

##### Global business rules

##### Warning: Consider using script includes instead of global business rules. Script includes

load only on request while global business rules load on every page in the system.

Global business rules are business rules where the Table field is set to Global. Global business rules may be accessible on multiple tables and from other scripts, depending on their scope protection. For a global business rule, define the scope protection by setting the Accessible from field:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 65

**- This application scope only** : prevents applications in a different scope than the business rule from calling this business rule.

**- All application scopes** : allows any application to call this business rule.

##### Note: Global business rules do not support domain separation.

##### Scripts in scoped business rules

When you write a script in a business rule, you can access:

**-** Any script includes and global business rules in the same scope as the business rule.

**-** Script includes and global business rules that allow applications in a different scope to call them. To call functions from another scope, you must specify the scope of the function.

**-** For business rules in a unique scope, you can access the scoped system APIs only.

Create a business rule

You can create any type of business rule to run when a record is displayed, inserted, updated, or deleted, or when a table is queried.

###### About this task

##### Note: These instructions and examples provide general guidance for how to implement

this functionality. For help with unique use cases, refer to the Developer Community Forum , where you can ask questions, interact with other developers, and search for existing solutions.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Business Rules**.

**2.** Click **New**.

**3.** Fill in the fields, as appropriate.

##### Note: You might need to configure the form to see all fields.

Business Rule fields

Field Description

Name Enter a name for the business rule.

Table Select the table that the business rule runs on.

##### Note: The list shows only tables and database views that meet the scope

protections for business rules. Business rules defined for a database view can run only on Query. A business rule for a database view cannot run on insert, update, or delete.

Application Application that contains this business rule.

Accessible from

Scope protection for a global business rule.

##### Note: This field is visible only when the Table field is set to Global. It

does not apply to rules that run on specific tables.

Active Select this check box to enable the business rule.

Advanced Select this check box to see the advanced version of the form.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 66

Field Description

When to run

When [Advanced] Select when this business rule should execute: display , before , async , or after the database operation is complete.

##### Note: Consider setting the Order for async business rules as the system

uses this value when creating the associated scheduled job.

Newly created async business rules run automatically on upgrade.

Existing async business rules can be migrated to use the new async behavior.

Order [Advanced] Enter a number indicating the sequence in which this business rule should run. If there are multiple rules on a particular activity, the rules run in the order specified here, from lowest to highest.

Insert Select this check box to execute the business rule when a record is inserted into the database.

Update Select this check box to execute the business rule when a record is update.

Delete [Advanced] Select this check box to execute the business rule when a record is deleted from the database.

Query [Advanced] Select this check box to execute the business rule when a table is queried.

Filter Conditions

Use the condition builder to determine when the business rule should run based on the field values in the selected Table. You can also use the Condition field to build a condition with a script.

##### Note: Filters based on string compares are case-sensitive.

Role Conditions

Select the roles that users who are modifying records in the table must have for this business rule to run.

Actions

Set field values

Set values for fields in the selected Table using the choice lists:

◦ The field

◦ The assignment operator:

▪ To: An exact value

▪ Same as: The value of another field

▪ To (dynamic): A value relative to the user configuring the business rule or a user with a specific role

◦ The value

Add message

Select this check box and enter a message that appears when this business rule is run

Abort action Select this check box to abort the current database transaction. For example, on a before insert business rule, if the conditions are met, do not insert the record into the database.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 67

Field Description

If you select this option, you cannot perform additional actions on the record, such as setting field values and running scripts. You can still display a message to users by selecting the Add message check box and composing the message.

Advanced

Condition Create a JavaScript conditional statement to specify when the business rule should run. By adding the condition statement to this field, you tell the system to evaluate the condition separately and run the business rule only if the condition is true. If you decide to include the condition statement in the Script field or if you use the condition builder, leave this field blank. To have the instance reevaluate the condition statement a second time before running an async business rule, add the system property

###### glide.businessrule.async_condition_check and set the value to

true.

Script [Advanced] Create a script that runs when the defined condition is true.

◦ onAfter

◦ onAsync

◦ onBefore

◦ onDisplay

For more information and examples, see Example business rule scripts.

Related list: Versions

Versions Shows all versions of the business rule. Use this list to compare versions or to revert to a previous version.

**4.** Click **Submit**.

Trouble? If you run into issues with your business rule, see the Business Rule FAQ [KB0965707] article in the Now Support Knowledge Base.

Global variables in business rules

Predefined global variables are available for use in business rules.

Use the following predefined global variables to reference the system in a business rule script.

Global variable Description

###### current Current state of the record being referenced. See "Prevent null pointer

exceptions" below to check for nulls before using this variable.

###### previous State of the referenced record prior to any updates made during the

execution context, where the execution context begins with the first update or delete operation and ends after the script and any referenced business rules are executed. If multiple updates are made to the record within one

###### execution context, previous will continue to hold the state of the record

before the first update or delete operation. Available on update and delete

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 68

Global variable Description

operations only. Not available on async operations. See "Prevent null pointer exceptions" below to check for nulls before using this variable.

###### g_scratchpad Scratchpad object is available on display rules, and is used to pass

information to the client to be accessed from client scripts.

###### gs References to GlideSystem functions.

###### The variables current, previous, and g_scratchpad are global across all business rules

that run for a transaction.

##### Prevent null pointer exceptions

###### In some cases, there may not be a current or previous state for the record when a business

rule runs, which means that the variables will be null. To check for null before using a variable, add the following code to your business rule:

if (current == null) // to prevent null pointer exceptions. return;

##### Define variables

User-defined variables are globally scoped by default. If a new variable is declared in an order 100 business rule, the business rule that runs next at order 200 also has access to the variable. This may introduce unexpected behavior.

To prevent such unexpected behavior, always wrap your code in a function. This protects your variables from conflicting with system variables or global variables in other business rules that

###### are not wrapped in a function. Additionally, variables such as current must be available when

a function is invoked in order to be used.

###### The following script is vulnerable to conflicts with other code. If the variable now_GR is used in

other rules, the value of the variable may unexpectedly change.

var now_GR = new GlideRecord('incident'); now_GR.query(); while(now_GR.next()) {

//do something

}

When this script is wrapped in a function, the variable is available only within the function and

###### does not conflict with other functions using a variable named now_GR.

myFunction();

function myFunction() { var now_GR = new GlideRecord('incident'); now_GR.query(); while(now_GR.next()) { //do something } }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 69

Use business rules and client scripts to control field values

Implement both business rules and client scripts for a field to enable users to set record values properly using both forms and lists, and to see immediate changes to the values in forms as edits are made.

The problem with using only a client script or a business rule to control updates to a field is that fields can be changed on either a form or a list. Client scripts and UI policies run on forms only (client-side) and do not apply to list editing. Allowing list editing with client scripts running on fields in a form can result in incorrect data being saved to the record. For systems in which client scripts or UI policies apply to forms, either disable list editing or create appropriate business rules or access control to control the setting of values in the list editor. A side effect of this is that security measures implemented in client scripts are easy to circumvent. The user only needs to edit the field in a list.

Business rules on a form are not dynamic, the user must update the record for the change to be seen. This makes using client scripts the preferred method for controlling field values on forms.

When using both a business rule and client script to control field values, the update behavior is the same across the system. This means that updated values are not different depending on whether a list of form is used to make the change. This means that the same functionality must be implemented twice, once in a client script and once in a business rule or access control.

##### Example: Use a business rule to create email addresses during user record

##### import

An organization has a client script that sets the email address for a user to first.last@company.com. Administrators do this so they can see the email address immediately when they enter the user's information. The administrator then performs a bulk import of users from a spreadsheet containing the users' first and last names. The expectation is that each user's email address will be set automatically, as they are when they edit the form. Since the client script runs only on the form (the interface to the record), it has no effect on data imported into the record from outside that interface, and no email addresses are created. To solve this problem, the administrator implements a business rule that runs when the import occurs and creates the email addresses.

##### Example: Prevent list edit for a field that is not editable in the form

An organization wants to hide the Priority field on an incident form if the assignment group is Development. They create a UI policy on the incident form to do this, but their users can still see and edit the Priority field using the list editor. To rectify this, apply an access control to prevent read access to the Priority field when the assignment group is Development.

Using NULL as a field value

The string NULL has a particular role in scripts and is a reserved word.

The reserved word is NULL in all capital letters. A field with the value Null or null , for example, is acceptable. Only use NULL to clear out a particular field.

Any NULL field values obtained from an import set data source are inserted into the staging table as empty field values. You should not use the term NULL as a field value in import set transform maps or anywhere in the First name or Last name fields. Also, do not use NULL in reference fields as the system interprets the value as a string containing the word NULL, not as a reserved word.

Display business-rules

Display rules are processed when a user requests a record form.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 70

The data is read from the database, display rules are executed, and the form is presented to the user. The current object is available and represents the record retrieved from the database. Any field changes are temporary since they are not yet submitted to the database. To the client, the form values appear to be the values from the database; there is no indication that the values were modified from a display rule. This is a similar concept to calculated fields.

###### The primary objective of display rules is to use a shared scratchpad object, g_scratchpad,

which is also sent to the client as part of the form. This can be useful when you need to build client scripts that require server data that is not typically part of the record being displayed. In most cases, this would require a client script making a call back to the server. If the data can be determined prior to the form being displayed, it is more efficient to provide the data to the client on the initial load. The form scratchpad object is an empty object by default, and used only to store name:value pairs of data.

To populate the form scratchpad with data from a display rule:

// From display business rule g_scratchpad.someName = "someValue"; g_scratchpad.anotherName = "anotherValue";

// If you want the client to have access to record fields not being displayed on the form g_scratchpad.created_by = current.sys_created_by;

// These are simple examples, in most cases you will probably perform some other // queries to test or get data

To access the form scratchpad data from a client script:

// From client script if(g_scratchpad.someName == "someValue") { //do something special }

Task Active State Management business rule

This business rule determines whether the active field value needs to change based on changes to the State field.

The Task Active State Management business rule is executed when the State is changed for a task record. Its execution order is 50, and it runs before most other task business rules.

###### If the current task table has the close_states attribute defined on its table, or if it is inherited

from a higher-level table, then the rule determines whether the active field needs to change. This is done by comparing the previous and current state values.

**-** If the state changes from an active state to an inactive state, the **Active** field is set to false.

**-** If the state changes from an inactive state to an active state, the **Active** field is set to true, effectively re-activating or re-opening the task.

###### It is recommended that you leverage the (current.active.changesTo([true/

###### false]) action in your business rule, as opposed to creating rules on each task table that mark

tasks as inactive or active.

Example business rule scripts

Find an example business rule script that helps you with a requirement of your organization.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 71

##### Note: These instructions and examples provide general guidance for how to implement

this functionality. For help with unique use cases, refer to the Developer Community Forum , where you can ask questions, interact with other developers, and search for existing solutions.

Compare date fields in a business rule

It is possible to compare two date fields or two date and time fields in a business rule, and abort a record insert or update if they are not correct.

For example, you may want a start date to be before an end date. The following is an example script:

if ((!current.u_date1.nil()) && (!current.u_date2.nil())) { var start = current.u_date1.getGlideObject().getNumericValue(); var end = current.u_date2.getGlideObject().getNumericValue(); if (start > end) { gs.addInfoMessage('start must be before end'); current.u_date1.setError('start must be before end') ; current.setAbortAction(true); } }

This example has been tested in global scripts, and may need changes to work in scoped scripts. In addition to possibly needing API changes, security is more strict in scoped scripts.

As a good practice, make the business rule a before rule for insert and update actions. In the example script:

**-** u_date1 and u_date2 are the names of the two date fields. Replace these names with your own field names.

**-** The first line checks that both fields actually have a value.

**-** The next two lines create variables that have the dates' numerical values.

**-** The next two lines create different alert messages for the end user: one at the top of the form

###### and one by the u_date1 field in the form.

**-** The last line aborts the insert or update if the date fields are not correct.

Here is a more complex example of the above comparison. If you have more than one pair of start and end dates, you can use arrays as shown. Additionally, this script requires the input dates to be within a certain range, in this case, no fewer than 30 days in the past and no more than 365 days in the future.

// Enter all start and end date fields you wish to check, as well as the previous values // Make sure that you keep the placement in the sequence the same for all pairs var startDate = new Array(current.start_date,current.work_start); var prevStartDate = new Array(previous.start_date,previous.work_start); var endDate = new Array(current.end_date,current.work_end); var prevEndDate = new Array(previous.end_date,previous.work_end);

// The text string below is added to the front of ' start must be before end' var userAlert = new Array('Planned','Work');

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 72

// Set the number of Previous Days you want to check var pd = 30; // Set the number of Future Days you want to check var fd = 365;

// You shouldn't have to modify anything below this line

var nowdt = new GlideDateTime(); nowdt.setDisplayValue(gs.nowDateTime()); var nowMs = nowdt.getNumericValue(); var pdms = nowMs;

// Subtract the product of previous days to get value in milliseconds pdms -= pd _ 24 _ 60 _ 60 _ 1000; var fdms = nowMs;

// Add the product of future days to get value in miliseconds fdms += fd _ 24 _ 60 _ 60 _ 1000; var badDate = false;

// Iterate through all start and end date / time fields for (x = 0; x < startDate.length; x ++) { if ((!startDate[x].nil()) && (!endDate[x].nil())) { var start = startDate[x].getGlideObject().getNumericValue(); var end = endDate[x].getGlideObject().getNumericValue(); if (start > end) { gs.addInfoMessage(userAlert[x] + ' start must be before end'); startDate[x].setError(userAlert[x] + ' start must be before end'); badDate = true; } else if ((prevStartDate[x]) != (startDate[x])) { if (start < pdms) { gs.addInfoMessage(userAlert[x] + ' start must be fewer than ' + pd + ' days ago'); startDate[x].setError(userAlert[x] + ' start must be fewer than ' + pd + ' days ago'); badDate = true; } } else if ((prevEndDate[x]) != (endDate[x])) { if (end > fdms) { gs.addInfoMessage(userAlert[x] + ' end must be fewer than ' + fd + ' days ahead'); endDate[x].setError(userAlert[x] + ' end must be fewer than ' + fd + ' days ahead'); badDate = true ; } } } } if (badDate == true ) { current. setAbortAction ( true ) ; }

Parse XML payloads

###### Fields in XML format can be parsed with the system's getXMLText function.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 73

Fields that get inserted into the database in XML format, such as the payload of an ecc_event

###### row, can be parsed with the system's getXMLText function. The getXMLText function takes

a string and an XPATH expression. For example:

var name = gs.getXMLText("<name>joe</name>", "//name");

returns the string 'joe'.

Assuming that the field "payload" contains XML, the function call might look like:

var name = gs.getXMLText(current.payload, "//name");

For information on XPATH, visit w3schools.

Abort a database action in a before business-rule

In a before business rule script, you can cancel or abort the current database action using the

###### setAbortAction() method.

For example, if the before business rule is executed during an insert action, and you have a condition in the script that calls current.setAbortAction(true), the new record stored in current is not created in the database. The business rule continues to run after calling

###### setAbortAction() and all subsequent business rules will execute normally. Calling this

method only prevents the database action on current object from occurring.

###### You can use the isActionAborted() method to determine if the current database action

###### (insert, update, delete) is going to be aborted. isActionAborted() is initialized for new

###### threads and the next() method explicitly sets its value to false.

##### Note: setAbortAction() can only be executed from the same scope as the record

whose action is being aborted. current.setAbortAction is not honored if executed in a business rule that is defined in a different scope.

Determine the operation that triggered the business rule

You can write a script for a business rule that is triggered on more than one database action.

If you want the business rule script to dynamically branch depending on the action that triggered

###### the event, you can use the operation() function. For example:

if(current.operation() == "update") { current.updates ++; } if(current.operation() == "insert") { current.updates = 0; }

Use an OR condition in a business rule

An OR condition can be added to any query part within a business rule.

An OR condition can be added to any query part within a business rule with the

###### addOrCondition() method. The example below shows a query for finding all the incidents

###### that have either a 1 or a 2 priority. The first addQuery() condition is defined as a variable and is

used in the OR condition.

var inc = new GlideRecord('incident'); var qc = inc.addQuery('priority','1'); qc.addOrCondition('priority','2'); inc.query(); while(inc.next()) { // processing for the incident goes here }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 74

The following script is a more complex example, using two query condition variables doing the equivalent of (priority = 1 OR priority = 2) AND (impact = 2 OR impact

###### = 3). The results of the OR condition are run with two variables, qc1 and qc2. This allows you

to manipulate the query condition object later in the script, such as inside an IF condition or WHILE loop.

var inc = new GlideRecord('incident'); var qc1 = inc.addQuery('priority','1'); qc1.addOrCondition('priority','2'); var qc2 = inc.addQuery('impact','2'); qc2.addOrCondition('impact','3'); inc.query(); while(inc.next()) { // processing for the incident goes here }

Reference a Glide list from a business rule

A field defined as a glide list is an array of values stored in a single field.

Here are some examples of how to process a glide_list field when writing business rules. Generally a glide_list field contains a list of reference values to other tables.

##### Examples

For example, the Watch list field within tasks is a glide_list containing references to user records.

The code below shows how to reference the field.

// list will contain a series of reference (sys_id) values separated by a comma // array will be a javascript array of reference values var list = current.watch_list.toString(); var array = list.split(","); for (var i=0; i < array.length; i++) { gs.print("Reference value is: " + array[i]); }

Output:

**_ Script: Reference value is: 62826bf03710200044e0bfc8bcbe5df1 _** Script: Reference value is: c2826bf03710200044e0bfc8bcbe5d45 **_ Script: Reference value is: 5f74e421c0a8010e01ec0d74a7ee2cc6 _** Script: Reference value is: 06826bf03710200044e0bfc8bcbe5d57

You can also get the display values associated with the reference values by using the

###### getDisplayValue() method as shown below.

// list will contain a series of display values separated by a comma // array will be a javascript array of display values var list = current.watch_list.getDisplayValue(); var array = list.split(","); for (var i=0; i < array.length; i++) { gs.print("Display value is: " + array[i]); }

Output:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 75

**_ Script: Display value is: Abel Tuter _** Script: Display value is: Ashley Leonesio **_ Script: Display value is: Charles Beckley _** Script: Display value is: Cherie Fuhri

Use indexOf("searchString") to find a string in a Glide list

###### Use indexOf(" searchString") to return the location of the string passed into the method if

the glide list field, such as a Watch list, has at least one value in it.

If the field is empty, it returns undefined. To avoid returning an undefined value, do any of the following:

**-** Force the field to a string, such as:

###### watch_list.toString().indexOf(" searchString")

**-** Check for an empty Glide list field with a condition before using indexOf(), such as: if

###### (watch_list.nil() || watch_list.indexOf(" searchString") == -1)

Lock user accounts

You can lock user accounts if the user is not active.

The following business rule script locks user accounts if the user is not active in the LDAP directory or the user does not have self-service, itil, or admin access to the instance.

// Lock accounts if bcNetIDStatus != active in LDAP and user does not // have self-service, itil or admin role var rls = current.accumulated_roles.toString(); if(current.u_bcnetidstatus == 'active' && (rls.indexOf(',itil,') > 0 || rls.indexOf(',admin,') > 0 || rls.indexOf(',ess,') > 0 )) { current.locked_out = false; } else { current.locked_out = true; }

var now_GR = new GlideRecord("sys_user"); now_GR.query(); while(now_GR.next()) { now_GR.update(); gs.info("updating " + gr.getDisplayValue()); }

Default before-query business rule

You can use a query business rule that executes before a database query is made.

Use this query business rule to prevent users from accessing certain records. Consider the following example from a default business rule that limits access to incident records.

**-** Name: incident query

**-** Table: Incident

**-** When: before, query

**-** Script:

if(!gs.hasRole("itil") && gs.isInteractive()) { var u = gs.getUserID();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 76

var qc = current.addQuery("caller_id",u).addOrCondition("opened_by",u).a ddOrCondition("watch_list","CONTAINS",u); gs.print("query restricted to user: " + u); }

This example prevents users from accessing incident records unless they have the itil role, or are listed in the Caller or Opened by field. So, for example, when self-service users open a list of incidents, they can only see the incidents they submitted.

##### Note: You can also use access controls to restrict the records that users can see.

Script includes

Script includes are used to store JavaScript that runs on the server.

Create script includes to store JavaScript functions and classes for use by server scripts. Each script include defines either an object class or a function.

Consider using script includes instead of global business rules because script includes are only loaded on request. See Privacy settings on Glide AJAX enabled script includes and Discovery script includes for more information.

For additional examples of scripts, see Useful scripts.

Script include form

Script includes have a name, description, and, script. They also specify whether they are active or not, and whether they can be called from a client script. View existing or create a new script include using the Script Include form.

To access script includes, navigate to All > System Definitions > Script Includes.

Script include form

Field Description

Name The name of the script include. If you are defining a class, this must match the name of the class, prototype, and type. If you are using a classless (on-demand) script include, the name must match the function name.

API Name The internal name of the Script Include. Used to call the Script Include from out-ofscope applications.

Glide AJAX enabled (or Client callable)

The script include is available to client scripts, list/report filters, reference qualifiers, or if specified as part of the URL. Glide AJAX enabled script includes are invoked from GlideAjax and require that users satisfy an ACL associated with the script include. When selected, the Access Controls Related Link is available. See Privacy settings on Glide AJAX enabled script includes for more information.

Mobile callable

The script include is available to client scripts called from mobile devices.

Sandbox enabled

The script include is available to scripts invoked from the script sandbox, such as a query condition.

##### Important: Script includes should only be made available to the script

sandbox if necessary.

For information about the script sandbox, see Script sandbox.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 77

Script include form (continued)

Field Description

Application The application where this script include resides.

Accessible from Sets which applications can access this script include: All application scopes

Can be accessed from any application scope.

This application scope only

Can be accessed only from the current application scope.

Active Enables the script include when selected. Deselect the active field to disable the script include.

Description Provides descriptive content regarding the script include.

Script Defines the server side script to run when called from other scripts.

The script must define a single JavaScript class or a global function. The class or function name must match the Name field.

Package The package that contains this script include.

Created by The user who created this script include.

Updated by

The user who most recently updated this script include.

Protection policy Sets the level of protection for the script include: None

Allows anyone to read and edit this downloaded or installed script include.

Read-only

Allows anyone to read values from this downloaded or installed script include. No one can change script values on the instance on which they download or install the script include.

Protected

Provides intellectual property protection for application developers. Customers who download the script include cannot see the contents of the script field. The script is encrypted in memory to prevent unauthorized users from seeing it in plain text.

Related lists on the form view:

Versions Shows all versions of the script include. Use this list to compare versions or to revert to a previous version. See Versions.

Access Controls

Becomes available when the Glide AJAX enabled is selected and is hidden from standard script includes. Use to protect a script include against unauthorized use when public access is not granted.

Use script includes

Script includes are found under System Definition or System UI. You can call existing script includes from a script or create a new script include.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 78

To create an entirely new script include, you can follow the format of any of the existing script

###### includes. In this example, the name of your script include is NewInclude and there is a single

function called myFunction. It is important that the name of the script include match the name of the class, prototype, and type. When you create a new script include and give it a name, the system provides a code snippet with the class and prototype properly set up.

var NewInclude =Class.create();

NewInclude. prototype ={ initialize : function (){},

myFunction : function (){<Put function code here>},

type :'NewInclude'};

You could then use the myFunction line like this:

var foo = new NewInclude(); foo.myFunction();

Glide AJAX enabled script includes

Glide AJAX enabled Script Includes make the script include available to client scripts, list/report filters, reference qualifiers, or if specified as part of the URL.

###### Before you begin

Role required: admin

###### Procedure

**1.** Navigate to **System Definition** > **Script Includes**.

**2.** Select **New** or select an existing script include for viewing or editing. See Use script includes for additional information on writing script includes.

**3.** Complete the form and select the **Glide AJAX enabled** option.

A role selector pops up to select a user role and automatically create an Access Control entry. Select a user role and click

OK.

##### Note: To disable the role selector window, set the

###### glide.script.ccsi.enable_acl_create_ux to false.

A script include record with a role-based Access Control is created. The Access Control Related Link becomes available with the selection of the Glide AJAX enabled check box.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 79

Privacy settings on Glide AJAX enabled script includes

Privacy settings for Glide AJAX enabled script includes determine who can access a Glide AJAX enabled script include.

##### Private privacy-setting

The private privacy-setting means that guests who access public pages cannot access the Glide AJAX enabled script-include. A private script cannot be executed by a non-logged-in user.

##### Public privacy-setting

A public privacy-setting means that the client script can be executed by non-logged-in users that create an appropriate HTTP request. This can create a security problem if the client script provides confidential information.

The following script includes remain public by default because Make UI pages public or private need to access them:

**-** GlideSystemAjax

**-** SysMessageAjax

**-** KnowledgeMessagingAjax

**-** KnowledgeAjax

**-** PasswordResetAjax

##### Set privacy on all Glide AJAX enabled script includes

Change the privacy setting on all Glide AJAX enabled script includes.

To provide further control over all Glide AJAX enabled script includes, administrators can add

###### the glide.script.ccsi.ispublic property. This property changes the visibility of Glide

AJAX enabled script includes by making them all public or private. Configure the property as follows:

Configure property

Title Property

Name glide.script.ccsi.ispublic

Type true|false

Value false

##### Note: To learn more about this property, see Require authentication by default for client

callable script includes [Updated in Security Center 1.3] in Instance Security Hardening Settings.

Change privacy on a single Glide AJAX enabled script include

Change the privacy setting for a single Glide AJAX enabled script include by adding the

###### isPublic() function.

###### The isPublic() setting takes precedence over the glide.script.ccsi.ispublic

property. For example, if the property is set to false , making all Glide AJAX enabled script

###### includes private, and a script sets isPublic() to true , the script is public.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 80

To change the privacy for a single Glide AJAX enabled script include, add the following method to the script include:

isPublic: function (){ return [true/false];},

Make the NewInclude client script private.

var NewInclude =Class.create();

NewInclude. prototype ={ initialize: function (){},

myFunction: function (){//Put function code here}, isPublic: function (){ return false;},

type:'NewInclude'};

Security on Glide AJAX enabled script includes

Protect your Glide AJAX enabled script includes against unauthorized use. For all records which are created a customer application, recommendations display that may help reduce security risk.

When creating a Glide AJAX enabled script include, the system displays the following security recommendations if they have not yet been configured:

**-** Add or define an Access Control, unless the script include has public access.

**-** Use GlideRecordSecure instead of GlideRecord API for better security, if the script queries the database.

##### Note: To disable the security recommendation messages, set the property

###### glide.script.ccsi.customer_scoped.security_msgs_enabled to false

in the sys_properties table. The default value is set to true.

See Instance Security Hardening Settings for additional information on security compliance.

Discovery script includes

Discovery script includes define JavaScript classes that you can use to accomplish Discovery tasks.

##### Note: Users with discovery_admin role can write script includes. Follow best practices

for server-side and client-side scripting to prevent security issues. See knowledge article KB0550828 for more information.

##### Using GlideRecordUtil to Work with GlideRecords

###### GlideRecordUtil is a utility class that provides methods that are useful for working with

GlideRecords during Discovery. Refer to GlideRecordUtil for descriptions of available methods.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 81

##### Getting a GlideRecord Instance

###### To get a GlideRecord instance for a given configuration item, and of the correct class

###### and table, use the getCIGR(sys_id) method. For example, the following code gets the

GlideRecord of a CI with the sys_id of 2dfd7c8437201000deeabfc8bcbe5d56:

var now_GR = new GlideRecordUtil().getCIGR("2dfd7c8437201000deeabfc8bcbe5d56");

###### To retrieve any hierarchical table without knowing its class type, use the getGR(base_table,

###### sys_id) method. For instance, to get a GlideRecord for a computer class CI, you might have

to distinguish whether it is a computer class, Windows server, or Linux server class. Using this method guarantees a GlideRecord with the correct class. Different classes have different attributes. In this use case, a Windows server has attributes different from a Linux server. The following example shows how to get a GlideRecord in the correct class with its attributes.

var now_GR = new GlideRecordUtil().getGR( "cmdb_ci_computer", "2dfd7c8437201000deeabfc8b cbe5d56");

##### Getting All the Fields In a GlideRecord

###### The getFields(now_GR) method returns a JavaScript object, such as a hashmap, of all the

fields or attributes that exist in a given GlideRecord.

var now_GR = new GlideRecordUtil().getGR("cmdb_ci_computer", "2dfd7c8437201000deeabfc8bc be5d56"); var fields = new GlideRecordUtil().getFields(now_GR); gs.log(fields.join(" ")); // List all the fields that are in a computer CI

##### Populating GlideRecord Object Fields

###### The populateFromGR(hashmap, gr, ignore) method enables you to take a

GlideRecord object and populate its fields and values into a JavaScript object. The third

###### argument ( ignore) is an optional JavaScript object that enables you to exclude certain fields.

###### For example, you may not care about sys_created_by or sys_updated_by fields in a

GlideRecord.

var objectToPopulate = { }; var now_GR = new GlideRecordUtil().getGR("cmdb_ci_computer", "2dfd7c8437201000deeabfc8bc be5d56"); var ignore = {"sys_created_on": true, "sys_updated_by": true}; new GlideRecordUtil().populateFromGR(objectToPopulate, now_GR, ignore); // Now the objectToPopulate contains field/value pairs from the computer GlideRecord

###### The mergeToGR(hashmap, gr, ignore) method enables you to populate a GlideRecord

with a field/value-paired object. The ignore argument stops specified fields from being updated.

###### The following code example updates a computer record's name and os fields, but does not

###### update the sys_created_by field:

var now_GR = new GlideRecordUtil().getGR("cmdb_ci_computer", "2dfd7c8437201000deeabfc8bc be5d56"); var obj = {"name": "xyz", "os": "windows 2000", "sys_created_by", "aleck.lin"}; var ignore = {"sys_created_by": true};

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 82

new GlideRecordUtil().mergeToGR(obj, gr, ignore); gr.update();

##### Getting Table Hierarchies

###### The getTables(table) method returns a list of table hierarchies, as shown in the following

example:

var tables = new GlideRecordUtil().getTables("cmdb_ci_linux_server"); gs.log(tables.join(",")); // The result would be "cmdb_ci, cmdb_ci_computer, cmdb_ci_server, cmdb_ci_linux_server".

Using DiscoveryException and AutomationException

When writing Discovery sensors and sensor-related scripts, you may want to use DiscoveryException or AutomationException to indicate that an exception has come from Discovery.

###### The DiscoveryException script include extends AutomationException,

###### which extends the GenericException class. The following example uses

###### DiscoveryException to throw an exception:

function foo() { if (//condition matches) throw new DiscoveryException("The message", "The cause"); }

The first argument takes the message of the exception and the second argument (optional) takes the cause of the exception. You may also want to catch the exception and log it as shown in the example below:

try { foo(); } catch (e) { if (e instanceof DiscoveryException) gs.log("A DiscoveryException occurred. It is " + e. getMessage() + " caused by " + e.getCause()); }

###### The above example also applies for AutomationException. DiscoveryException

is typically used to provide exception processing specifically for Discovery, while

###### AutomationException is used for exception processing that applies to both Orchestration

and Discovery.

Processors

Processors provide a customizable URL endpoint that can execute arbitrary server-side JavaScript code and produce output such as TEXT or JSON. Creating custom processors is deprecated.

##### Note: This feature is deprecated. While legacy, existing custom processors continue to

be supported, creating new custom processors has been deprecated. Instead, use the Scripted REST APIs.

##### Warning: When creating a processor, ensure that you use parameter names that

are specific to your processor. For example, if your processor exports a list of legal records, and a necessary parameter is the recipient's email address, don't use “email” as the parameter name. Create a more processor specific parameter name, such as legal_export_recipient_email. Failure to do so, and using instance parameter names, such as id, table, sys_id, service, catalog_id, or view (and others), can cause unexpected results.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 83

##### When to create processors

Do not create custom processors. This feature is deprecated. Please use the REST APIs instead of creating custom processors. The remaining information is left for existing processors only.

##### Processor form

Field Description

Name Unique name of the processor.

Type Programming language of the processor script.

Options include:

**-** java: do not select this option

**-** script

Application Application containing this record.

Active Flag to enable or disable the record.

CSRF protect

Option to protect the processor from running unless the instance uses a CSRF token.

Description Description of the processor's function or purpose.

Parameters List of available input parameters.

###### Specify parameter values in the URL as <parameter name>=<parameter

###### value>.

##### Note: Parameter names must be processor-specific. Do not choose

common parameter names that another processor might use. If you use a common parameter name, such as id, sys_id or table in a processor, it can break other functionality, since the processor wins when that parameter exists in a URL. For example, a processor with an id parameter, regardless of the Path value in the same record, breaks the Service Portal, which depends on that parameter for page identification.

Path URI path used to call this processor.

Call a processor from the URL as:

https://<instance name>.service-now.com/<Path>.do

Script Immediately Invoked Function Expression to run when the system calls this processor.

The function automatically provides input parameters for the following API objects.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 84

Field Description

**-** g_request

**-** g_response

**-** g_processor

Protection policy Policy to use to protect this record's script.

Options include:

**-** None

**-** Read-only

**-** Protected

Processor API components

Processors have access to dedicated API classes, objects, and methods.

Processor API components

Class, object, or method Description

g_response An object of type HttpServletResponse. See GlideServletResponse.

setContentType(‘text/ html;charset=UTF-8’)

A GlideServletResponse method to set the content type of the response being sent to the client.

g_request An object of type HttpServletRequest. See HttpServletRequest.

getParameter() A glide method to get the value of a URL parameter.

canRead() A GlideRecord method to determine if the user can read data from a table. See GlideRecord.

g_processor A simplified servlet for processors. See GlideScriptedProcessor.

writeOutput() A GlideScriptedProcessor method to display information on the client.

g_target An object containing the target table name of a processor URL. For example, a processor containing the URI incident.do applies to the Incident table.

Secure and protect a processor

You can protect your processor against unauthorized use by using role restrictions, and protect it by requiring a CSRF token.

###### About this task

##### Note: This feature is deprecated. While legacy, existing custom processors continue to

be supported, creating new custom processors has been deprecated. Instead, use the Scripted REST APIs.

You can re-use a table's user role restrictions to protect it from access by your processor. This protection method assumes the processor will access table data.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 85

###### Procedure

**1.** Create or select a user role that has access to the table the processor script calls.

**2.** Navigate to **System Definition** > **Processors**.

**3.** In **Script** , add the following code block.

var now_GR = new GlideRecord('your_table_name'); // canRead() compares the table’s ACL to the user making this request, and returns true if the logged-in user has read access to this table if(gr.canRead()) { // Perform table query here g_processor.writeOutput('Success!'); } else { g_processor.writeOutput('You do not have permission to read table your_table_name'); }

**4.** Update the code block to use other access restrictions as needed.

Available access functions include:

###### ◦ canCreate()

###### ◦ canRead()

###### ◦ canWrite()

###### ◦ canDelete()

**5.** Click **Update**.

Protect a processor with a CSRF token

You can protect a processor by requiring a CSRF token.

###### About this task

Script type processors can require a CSRF token check before the processor runs.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Processors**.

**2.** Open a processor record.

**3.** Select the **CSRF protect** option.

**4.** Click **Update**.

Create a simple processor

Create a simple processor to execute a script from a URL query. This feature is deprecated.

###### Before you begin

You must have your own demonstration instance.

Role required: admin

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 86

###### About this task

##### Note: This feature is deprecated. While legacy, existing custom processors continue to

be supported, creating new custom processors has been deprecated. Instead, use the Scripted REST APIs.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Processors**.

**2.** Select **New**.

**3.** Enter the following information.

Field Value

Name Hello

Type Script

Path Hello

Script

var name= g_request.getParameter("name "); g_processor.writeOutput("te xt/plain","Hello "+name);

**4.** Select **Submit**.

**5.** Enter a URL query to the instance with the following format: https:// instance.service-now.com/processor_name.do?parameter=value For example: https://<instancename>.service-now.com/Hello.do? name=world.

Create a multi-table processor

Create a multi-table processor that reports the number of rows in any table on your instance. This feature is deprecated.

###### Before you begin

Role required: admin

###### About this task

##### Note: This feature is deprecated. While legacy, existing custom processors continue to

be supported, creating new custom processors has been deprecated. Instead, use the Scripted REST APIs

The multi-table processor protects itself from performance and security violations by confirming that the user is authorized to read the table. It does not report on certain tables that are too large to query safely.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Processors**. The list of processors appears.

**2.** Select **New**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 87

**3.** Enter the following information.

Name TableSize

Type Choose Javascript

Description Return number of records in a table

Parameters SIZE

Path <leave empty>

Script:

g_response.setContentType('text/html;charset=UTF-8'); if(g_target === 'sys_email' || g_target === 'sys_log' ) { g_processor.writeOutput(g_target + ' table is too large to quickly count'); } else { var count = new GlideAggregate(g_target); if( count.canRead() ) { count.addAggregate('COUNT'); count.query(); var records = 0; if (count.next()) { records = count.getAggregate('COUNT'); } g_processor.writeOutput('table ' + g_target + ' has ' + records + ' records'); } else { g_processor.writeOutput('You do not have access to table ' + g_target); } }

**4.** Select **Save**.

**5.** Test the new processor by entering the following URLs: https://<instancename>.service-now.com/incident.do?SIZE and https://<instancename>.service-now.com/sys_user.do?SIZE Your instance reports the number of records in the table. For example, table incident has 82 records.

Create a custom processor

Create a custom processor to execute a script from a URL query. This feature is deprecated.

###### Before you begin

Role required: admin

###### About this task

##### Note: This feature is deprecated. While legacy, existing custom processors continue to

be supported, creating new custom processors has been deprecated. Instead, use the Scripted REST APIs.

When complete, you can do the following tasks:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 88

**-** Create a new processor

**-** Run a script from a URL query

The following example steps assume you have your own demonstration instance.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Processors**.

**2.** Select **New**.

**3.** In the **Name** field, enter Hello.

**4.** In the **Type** field, select _script_.

**5.** In the **Path** field, enter Hello.

**6.** In the **Script** field, enter the following code.

var name = g_request.getParameter("name"); g_processor.writeOutput("text/plain", "Hello " + name);

**7.** Select **Submit**.

**8.** Log out of the instance and open a new browser window.

**9.** Enter a URL query to the instance with the following format: https:// instance.service-now.com/processor_name.do?parameter=value. For example: https://<instance name>.service-now.com/Hello.do? name=world.

**10.** When prompted, enter the credentials for a valid user.

Scripts Background module

Administrators can use the Scripts Background module to run arbitrary JavaScript code from the server.

The Scripts Background module consists of the following components.

**-** Text box to enter JavaScript.

**-** Selector to specify the application scope.

**- Run script** button.

**-** List of available scopes.

**- Record for rollback?** check box. Selected by default. Creates a rollback context for the script execution. After the script is run, click the **Script execution and recovery available here** link to go to the **Script Execution History** form where you can rollback the script.

**- Execute in sandbox?** check box. Allows script to run with sandbox like restrictions. If checked, data cannot be inserted, updated, or deleted.

**- Execute as scriptlet?** check box. Allows the script to execute as a scriplet, which gives the script access to the global scope and any server-side functionality or objects. If the check box is not selected, the script executes in global scope, but does not have access to any server- side functionality or objects.

**- Cancel after 4 hours** check box. Selected by default. Cancels the script execution if it continues running after four hours.

When a script is run, the instance displays results, information, and error messages at the top of the screen.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 89

##### Important: Running free-form JavaScript can cause system disruption or data loss. Do

not run free-form scripts from a production instance.

To stop a transaction, see View and kill active transaction.

For examples of scripts you could run, see Useful scripts.

Script sandbox

The script sandbox is an environment with restricted rights in which client-generated scripts run when they’re made available to the script sandbox.

The script sandbox helps prevent unauthorized or unauthenticated users from executing privileged script on your instance. There are two cases that enable the client to send scripts to the server for evaluation (client-generated scripts).

**-** Filters or queries: It’s legal to send a filter to the server such as: assigned_to=javascript:getMyGroups().

**-** System API: The API call AJAXEvaluate enables the client to run arbitrary scripts on the server and receive a response.

The script being evaluated via either of these two entry points runs within a reduced-rights sandbox with the following characteristics:

**-** Only those business rules marked **Client callable** are available within the sandbox.

**-** Only script includes marked **Sandbox enabled** are available within the sandbox.

**-** Certain API calls (largely but not entirely limited to ones dealing with direct database access) aren’t allowed.

**-** Data can’t be inserted, updated, or deleted from within the sandbox. Any calls to

###### current.update(), for example, are ignored.

##### Note: Beginning with the Xanadu release, script includes marked as Glide AJAX enabled

(previously named Client callable ) aren’t accessible within the sandbox. Only those marked Sandbox enabled are available within the sandbox. When upgrading to the Zurich release from the Washington DC release or earlier, any script includes marked as Client callable are also marked as Sandbox enabled.

##### Restricted methods with the script sandbox

These methods aren’t supported in client-generated scripts in the script sandbox.

##### Note: The GlideSystem (gs) methods log(), logError(), and

###### logWarning() can be enabled with script sandboxing by setting the

###### glide.security.sandbox_no_logging system property to false.

Restricted methods

Class Method

GlideRecord

**-** deleteMultiple()

**-** deleteRecord()

**-** getRowCount()

**-** insert()

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 90

Restricted methods (continued)

Class Method

**-** update()

**-** updateMultiple()

GlideSystem (gs)

**-** addErrorMessage()

**-** addInfoMessage()

**-** addMessage()

**-** eventQueue()

**-** flushMessages()

**-** getEscapedProperty()

**-** getProperty()

**-** log()

**-** logError()

**-** logWarning()

**-** setProperty()

**-** setRedirect()

**-** setReturn()

**-** workflowFlush()

ScopedGlideRecord

**-** deleteMultiple()

**-** deleteRecord()

**-** insert()

**-** update()

**-** updateMultiple()

ScopedGlideSystem (gs)

**-** addErrorMessage()

**-** addInfoMessage()

**-** debug()

**-** eventQueue()

**-** executeNow()

**-** getProperty()

**-** getSessionToken()

**-** info()

**-** setRedirect()

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 91

Restricted methods (continued)

Class Method

GlideDateTime

**-** add()

**-** addDays()

**-** addDaysLocalTime()

**-** addDaysUTC()

**-** addMonths()

**-** addMonthsLocalTime()

**-** addSeconds()

**-** addWeeks()

**-** addYears()

**-** compareTo()

**-** getDate()

**-** getDayOfWeek()

**-** getDayOfWeekUTC

**-** getDayOfWeekLocalTime()

**-** getDayOfMonth()

**-** getDayOfMonthLocalTime()

**-** getDayOfMonthNoTZ()

**-** getDayOfWeek()

**-** getDayOfWeekLocalTime()

**-** getDayOfWeekUTC()

**-** getHourOfDayLocalTime()

**-** getHourOfDayUTC()

**-** getDaysInMonth()

**-** getDaysInMonthUTC()

**-** getDaysInMonthLocalTime()

**-** getDisplayValueInternal()

**-** getDisplayValue()

**-** getLocalDate()

**-** getMonthLocalTime()

**-** getMonthNoTZ()

**-** getMonthUTC()

**-** getNumericValue()

**-** getTime()

**-** getTZOffset()

**-** getYear()

**-** getUserTimeZone()

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 92

Restricted methods (continued)

Class Method

**-** getWeekOfYearLocalTime()

**-** getWeekOfYearUTC()

**-** getYearUTC()

**-** getYearLocalTime()

**-** isDST()

**-** onOrAfter()

**-** onOrBefore()

**-** setDayOfMonthUTC()

**-** setDisplayValue()

**-** setMonth()

**-** setNumericValue()

**-** setTZ()

**-** setValue()

**-** setValueUTC()

**-** subtract()

**-** toString()

GlideDate GlideDate supports the same methods as GlideDateTime, as well as:

**-** getByFormat()

**-** getDayOfMonthNoTZ()

**-** getMonthNoTZint()

**-** parseDate()

GlideTime GlideTime supports the same methods as GlideDateTime, as well as:

**-** getByFormat()

**-** getHourLocalTime()

**-** getHourOfDayLocalTime()

**-** getHourOfDayUTC()

**-** getMinutesLocalTime()

**-** getMinutesUTC()

**-** getSeconds()

GlideSchedule

**-** add()

**-** isInSchedule()

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 93

Restricted methods (continued)

Class Method

**-** Load()

**-** whenNext()

Installation settings

Installation settings are global business rules with calculated names. Installation settings are calculated just before a record is displayed and facilitate dynamic determination of access and roles. Installation Settings permit the programmatic determination of a setting.

Installation settings controlling access to fields and records are:

**-** CanRead()

**-** CanWrite()

**-** CanCreate()

**-** CanDelete()

Functions can return true if access is permitted, false if not. No return value uses the permission calculated using roles. The function has access to the current record through the variable current code.

The name of the function checking the permission on a record is formed by prefixing the setting name with the record name:

record_nameCanRead()

Similarly, the permission on a field in a record is formed by prefixing the function name with the record name, underscore, and field name:

record_name_field_nameCanRead()

Naming examples:

function incidentCanWrite() {} // can user write to this record? function incident_numberCanWrite() {} // can user write to the number field?

This sample business rule restricts the writing of the name field in the sys_dictionary file when the entry exists:

// the element name cannot be written unless this is a new record (not yet in database) function sys_dictionary_nameCanWrite() { if (current.isNewRecord()) return;

return false; }

Using DurationCalculator to calculate a due date

Using the DurationCalculator script include, you can calculate a due date, using either a simple duration or a relative duration base on schedules.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 94

The following script demonstrates how to use the global API DurationCalculator to calculate a due date. The first part of the script illustrates how to set a start datetime using the setStartDateTime() method and then use the calcDuration() method to determine a due date that is "x" amount of continuous time (seconds) from the specified start datetime. The second half of

###### the script illustrates how to use DurationCalculator to calculate a due date based on a

schedule. Schedules enable you to apply a "filter" on future time, such as only including the days in a work week within the calculation. For example, if you apply a schedule "weekdays" (which only includes Monday through Friday) to your duration calculation, and the start datetime is Friday at 5:00 pm, when you add a duration of two days, your due date would be Tuesday at 5:00 pm. If you did not use a schedule, your due date would be Sunday at 5:00 pm. For additional information on schedules, see Creating and using schedules.

This script can be cut and pasted into the Scripts Background page and run as is. It can also serve as an example for authoring business rules, UI actions, or used any other place that serverside script can be authored.

/\*\* _ Demonstrate the use of DurationCalculator to compute a due date. _ _ You must have a start date and a duration. Then you can compute a _ due date using the constraints of a schedule. \*/

gs.include('DurationCalculator'); executeSample();

/\*\* _ Function to house the sample script. _/ function executeSample(){

// First we need a DurationCalculator object. var dc = new DurationCalculator();

// --------------No schedule examples -----------------

// Simple computation of a due date without using a schedule. Seconds // are added to the start date continuously to get to a due date. var gdt = new GlideDateTime("2012-05-01 00:00:00"); dc.setStartDateTime(gdt); if(!dc.calcDuration(2*24*3600)){ // 2 days gs.log("\*\*\* Error calculating duration"); return; } gs.log("calcDuration no schedule: " + dc.getEndDateTime()); // "2012-05-03 00:00:00" two days later

// Start in the middle of the night (2:00 am) and compute a due date 1 hour in the future // Without a schedule this yields 3:00 am. var gdt = new GlideDateTime("2012-05-03 02:00:00"); dc.setStartDateTime(gdt); if(!dc.calcDuration(3600)){

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 95

gs.log("\*\*\* Error calculating duration"); return; } gs.log("Middle of night + 1 hour (no schedule): "+ dc.getEndDateTime()); // No scheduled start date, just add 1 hour

// -------------Add a schedule to the date calculator --------------------addSchedule(dc);

// Start in the middle of the night and compute a due date 1 hour in the future. // Since we start at 2:00 am the computation adds the 1 hour from the start // of the day, 8:00am to get to 9:00am var gdt = new GlideDateTime("2012-05-03 02:00:00"); dc.setStartDateTime(gdt); if(!dc.calcDuration(3600)){ gs.log("\*\*\* Error calculating duration"); return; } gs.log("Middle of night + 1 hour (with 8-5 schedule): " + dc.getEndDateTime()); // 9:00 am

// Start in the afternoon and add hours beyond quiting time. Our schedule says the work day // ends at 5:00pm, if the duration extends beyond that, we roll over to the next work day. // In this example we are adding 4 hours to 3:00pm which gives us 10:00 am the next day. var gdt = new GlideDateTime("2012-05-03 15:00:00"); dc.setStartDateTime(gdt);

if(!dc.calcDuration(4\*3600)){ gs.log("\*\*\* Error calculating duration"); return;} gs.log("Afternoon + 4 hour (with 8-5 schedule): " + dc.getEndDateTime()); // 10:00 am.

// This is a demo of adding 2 hours repeatedly and examine the result. This // is a good way to visualize the result of a due date calculation. var gdt = new GlideDateTime("2012-05-03 15:00:00"); dc.setStartDateTime(gdt); for(var i=2; i<24; i+=1){ if(!dc.calcDuration(i\*3600)){ gs.log("\*\*\* Error calculating duration"); return; } gs.log("add "+ i +" hours gives due date: " + dc.getEndDateTime()); }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 96

// Setting the timezone causes the schedule to be interpreted in the specified timezone. // Run the same code as above with different timezone. Note that the 8 to 5 workday is // offset by the two hours as specified in our timezone. dc.setTimeZone("GMT-2"); var gdt = new GlideDateTime("2012-05-03 15:00:00"); dc.setStartDateTime(gdt); for(var i=2; i<24; i+=1){ if(!dc.calcDuration(i\*3600)){ gs.log("\*\*\* Error calculating duration"); return; } gs.log("add "+ i +" hours gives due date (GMT-2): " + dc.getEndDateTime()); } }

/** _ Add a specific schedule to the DurationCalculator object. _ _ @param durationCalculator An instance of DurationCalculator _/ function addSchedule(durationCalculator){ // Load the "8-5 weekdays excluding holidays" schedule into our duration calculator. var scheduleName = "8-5 weekdays excluding holidays"; var grSched = new GlideRecord('cmn_schedule'); grSched.addQuery('name', scheduleName); grSched.query(); if(!grSched.next()){ gs.log('\*** Could not find schedule "'+ scheduleName +'"'); return; }

durationCalculator.setSchedule(grSched.getUniqueValue(),"GMT"); }

Using DurationCalculator to compute a simple duration

A simple duration is the number of seconds between two date times.

If no schedule is used then this is a simple time date subtraction. If a schedule is used, then the schedule is consulted to remove non-work hours from the computation. Suppose schedule "8-5 weekdays excluding holidays" is used. In this case, the number of work hours from noon Monday to noon Tuesday is nine hours. To compute a simple duration, initialize the global API

###### DurationCalculator and call the calcScheduleDuration() method.

###### This script demonstrates how to use DurationCalculator to compute a simple duration.

/\*\* _ Sample script demonstrating use of DurationCalculator to compute simple durations _ \*/

gs.include('DurationCalculator');

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 97

executeSample();

/\*\* _ Function to house the sample script. _/ function executeSample(){

// First we need a DurationCalculator object. var dc = new DurationCalculator();

// Compute a simple duration without any schedule. The arguments // can also be of type GlideDateTime, such as fields from a GlideRecord. var dur = dc.calcScheduleDuration("2012-05-01", "2012-05-02"); gs.log("calcScheduleDuration no schedule: " + dur); // 86400 seconds (24 hours)

// The above sample is useful in limited cases. We almost always want to // use some schedule in a duration computation, let's load a schedule. addSchedule(dc);

// Compute a duration using the schedule. The schedule // specifies a nine hour work day. The output of this is 32400 seconds, or // a nine hour span. dur = dc.calcScheduleDuration("2012-05-23 12:00:00","2012-05-24 12:00:00"); gs.log("calcScheduleDuration with schedule: " + dur); // 32400 seconds (9 hours)

// Compute a duration that spans a weekend and holiday. Even though this // spans three days, it only spans 9 work hours based on the schedule. dur = dc.calcScheduleDuration("2012-05-25 12:00:00", "2012-05-29 12:00:00"); gs.log("calcScheduleDuration with schedule spaning holiday: " + dur); // 32400 seconds (9 hours)

// Use the current date time in a calculation. The output of this is // dependent on when you run it. var now = new Date(); dur = dc.calcScheduleDuration("2012-05-15", new GlideDateTime()); gs.log("calcScheduleDuration with schedule to now: " + dur); // Different on every run. }

/\*\* _ Add a specific schedule to the DurationCalculator object. _ \* @param durationCalculator An instance of DurationCalculator

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 98

\*/ function addSchedule(durationCalculator){ // Load the "8-5 weekdays excluding holidays" schedule into our duration calculator. var scheduleName = "8-5 weekdays excluding holidays"; var grSched = new GlideRecord('cmn_schedule'); grSched.addQuery('name', scheduleName); grSched.query(); if(!grSched.next()){ gs.log('\*\*\* Could not find schedule "'+ scheduleName +'"'); return; } durationCalculator.setSchedule(grSched.getUniqueValue()); }

Using relative duration

Relative duration is very similar to simple duration except a piece of script is used to determine what parts of a day to remove from the difference calculation.

This script is stored in table cmn_relative_duration and can be examined by navigating to System Scheduler > Schedules > Relative Durations. There are some example relative duration scripts in the out-of-the-box instance.

###### A relative duration sys_id is passed to the method calcRelativeDuration() of

the global API DurationCalculator class after initialization. When this method is called, the DurationCalculator object is passed to the relative duration script (stored in table

###### cmn_relative_duration) as the variable calculator. So, the relative duration script you write

and store in cmn_relative_duration has access to the executing DurationCalculator through the

###### variable calculator.

###### The following script demonstrates how to use DurationCalculator to calculate a relative

duration.

/\*\* _ Sample use of relative duration calculation. _ \*/

gs.include('DurationCalculator'); executeSample();

/\*\* _ Function to house the sample script. _/ function executeSample(){

// First we need a DurationCalculator object. We will also use // the out-of-box relative duration "2 bus days by 4pm" var dc = new DurationCalculator(); var relDur = "3bf802c20a0a0b52008e2859cd8abcf2"; // 2 bus days by 4pm if before 10am addSchedule(dc);

// Since our start date is before 10:00am our result is two days from// now at 4:00pm.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 99

var gdt = new GlideDateTime("2012-05-01 09:00:00"); dc.setStartDateTime(gdt); if(!dc.calcRelativeDuration(relDur)){ gs.log("\*\*\* calcRelativeDuration failed"); return; } gs.log("Two days later 4:00pm: "+ dc.getEndDateTime());

// Since our start date is after 10:00am our result is three days from // now at 4:00pm. var gdt = new GlideDateTime("2012-05-01 11:00:00"); dc.setStartDateTime(gdt); if(!dc.calcRelativeDuration(relDur)){ gs.log("\*\*\* calcRelativeDuration failed"); return; } gs.log("Three days later 4:00pm: "+ dc.getEndDateTime());}

/** _ Add a specific schedule to the DurationCalculator object. _ _ @param durationCalculator An instance of DurationCalculator _/ function addSchedule(durationCalculator){ // Load the "8-5 weekdays excluding holidays" schedule into our duration calculator. var scheduleName ="8-5 weekdays excluding holidays"; var grSched =new GlideRecord('cmn_schedule'); grSched.addQuery('name', scheduleName); grSched.query(); if(!grSched.next()){ gs.log('\*** Could not find schedule "'+ scheduleName +'"'); return;}

durationCalculator.setSchedule(grSched.getUniqueValue(),"GMT" );}

Querying tables in script

Using methods in the GlideRecord API, you can return all records from a table, return records from a table that satisfy specific conditions, or return records that include a string from a single table or from multiple tables in a text index group.

Query tables using the GlideRecord API. For API reference, see GlideRecord Scoped.

##### Return all records from a table

To query a table, first create a GlideRecord object. To create a GlideRecord, create the following in script:

var target = new GlideRecord('incident');

Creating a GlideRecord creates a target variable which is a GlideRecord object for the incident table.

To process all records from the incident table, add the following script:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 100

target.query(); // Issue the query to the database to get all records while (target.next()) { // add code here to process the incident record }

###### This script issues the query() to the database. Each call to next() would load the next

record for processing.

##### Return records from a table that satisfy query conditions

Most of the time, you want to retrieve a specific record or a specific set of records, and you have some criteria (query conditions) that define the records you want to obtain. For example, say that you want to obtain all the incident records that have a priority value of 1. Here is the code that would accomplish that.

var target = new GlideRecord('incident'); target.addQuery('priority',1); target.query(); // Issue the query to the database to get relevant records while (target.next()) { // add code here to process the incident record }

Notice that the example script includes target.addQuery('priority', 1);. This line

###### indicates that you only want the records where the priority field is equal to 1. In general, most

queries that you want to perform are equality queries; queries where you want to find records with a field equal to a value. For this reason, you do not need to provide an equality operator.

###### However, lets say you wanted to find all incidents where the priority field is greater than 1. In

this case, you would provide the operator that you want to apply to the query.

var target = new GlideRecord('incident') ; target.addQuery('priority','>',1); target.query(); // Issue the query to the database to get relevant records while (target.next()) { // add code here to process the incident record }

##### Return records from a table that include a string

Use the '123TEXTQUERY321' reserved name to search for string matches in all fields on a table. For example, this script returns records from the Incident table with field values that include the 'email' string.

var now_GR = new GlideRecord('incident'); gr.addQuery('123TEXTQUERY321', 'email'); gr.query();

###### '123TEXTQUERY321' is a reserved option for the name parameter in the

addQuery() method. You can use this option in an encoded query string. For example, instead of gr.addQuery('123TEXTQUERY321', 'email');, you can use gr.addEncodedQuery('123TEXTQUERY321=email').

String search is case-insensitive. The system returns the same results whether you search for email, Email, or EMAIL.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 101

##### Note: Before you can query using a string search, you must configure text indexing (and

optionally search attributes) for the table you want to search. For more information, see Configure a single table for indexing and searching.

##### Return records from multiple tables in a text index group that include a string

Use the '123TEXTINDEXGROUP321' reserved name to search for a string in a table from a text index group. This option returns results with relevancy scores computed using the text index group's settings.

##### Note: You can only query one table in the text index group at a time. Use this option when

you want to issue multiple single-table queries and merge their results, ordering them by relevancy score. The advantage of this option is that search result relevancy scores for the individual table queries are normalized consistently for all tables in the text index group.

For example, this script returns records from the Knowledge table that include the keyword 'email', with relevancy scores computed for the 'portal' index group.

var now_GR = new GlideRecord('kb_knowledge'); gr.addQuery('123TEXTQUERY321', 'email'); gr.addQuery('123TEXTINDEXGROUP321', 'portal'); gr.query();

You can create a similar query for each additional table in the 'portal' index group that you want to search, and then merge the individual queries' results, displaying the results with the highest relevancy scores first. Because all of these search queries use the same text index group search settings, the relevancy scores for their results are all normalized consistently. If you searched the same set of tables without using the gr.addQuery('123TEXTINDEXGROUP321', 'portal') method, the individual queries' relevancy scores would be normalized differently and would not be a useful basis for sorting the merged result set.

###### '123TEXTINDEXGROUP321' is a reserved option for the name parameter in the

addQuery() method. You can use this option in an encoded query string. For example, instead of gr.addQuery('123TEXTINDEXGROUP321', 'portal');, you can use gr.addEncodedQuery('123TEXTINDEXGROUP321=portal').

Multi-table string search is case-insensitive. The system returns the same results whether you search for email, Email, or EMAIL.

##### Note: Before you can query tables in an index group, you must configure text indexing

and search attributes for those tables and include them in the index group. For more information, see Configure multiple tables for indexing and searching. All tables in the index group must use the V4 indexing format.

Available JavaScript operators

###### Describes the operators that can be used within an addQuery() request.

Available JavaScript Operators

Field Definition addQuery

= Field must be equal to value supplied. addQuery('priority', '=', 1);

> Field must be greater than value supplied. addQuery('priority', '>', 1);

< Field must be less than value supplied. addQuery('priority', '<', 3);

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 102

Available JavaScript Operators (continued)

Field Definition addQuery

> = Field must be equal or greater than value supplied.

addQuery('priority', '>=', 1);

<= Field must be equal or less than value supplied.

addQuery('priority', '<=', 3);

!= Field must not equal the value supplied. addQuery('priority', '!=', 1);

STARTSWITH Field must start with the value supplied. The example shown on the right returns all records

###### where the short_description field starts

with the text Error.

addQuery('short_description', 'STARTSWITH', 'Error');

CONTAINS Field must contain the value supplied somewhere in the text. The example shown on the right returns all records where the

###### short_description field contains the text

Error anywhere in the field.

##### Note: The LIKE operation is not

supported. Administrators must use CONTAINS in the query.

addQuery('short_description', 'CONTAINS', 'Error');

IN Takes a map of values that allows commas, and gathers a collection of records that meet some other requirement. Behaves as Select _ from <table> where short_description IN ('Error', 'Success', 'Failure'), which is identical to Select _ from <table> where short_description='Error'. For example, to query all variable values that

###### belong to a specific Activity, use the IN clause,

and store their sys_ids in a map, or commaseparated list. Then query the variable value table and supply this list of sys_ids.

addQuery('short_description', 'IN', 'Error,Success,Failure');

ENDSWITH Field must terminate with the value supplied. The example shown on the right returns all

###### records where the short_description

field ends with text Error.

addQuery('short_description', 'ENDSWITH', 'Error');

DOES NOT CONTAIN

Selects records that do NOT match the pattern in the field. This operator does not retrieve empty fields. For empty values, use the operators "is empty" or "is not empty."The example shown on the right returns all records

###### where the short_description field does

not have the word "Error."

addQuery('short_description', 'DOES NOT CONTAIN', 'Error');

NOT IN Takes a map of values that allows commas, and gathers a collection of records that meet some other requirement. Behaves as: Select \* from <table> where

addQuery('short_description', 'NOT IN', 'Error,Success,Failure');

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 103

Available JavaScript Operators (continued)

Field Definition addQuery

short_description NOT IN ('Error').

INSTANCEOF Special operator that retrieves only records of a specified "class" for extended tables. The code example on the right, shows how to retrieve all configuration items that are classified as computers.

addQuery('sys_class_name', 'INSTANCEOF', 'cmdb_ci_computer');

For additional information on the operators that are available for filters and queries, see Operators available for filters and queries.

There are also some special methods that you can use to search for data that is NULL or NOT

###### NULL. To search for all incidents where the short_description field has not been supplied

(is null), use the following query:

var target = new GlideRecord('incident'); target.addNullQuery('short_description'); target.query(); // Issue the query to the database to get all records while (target.next()) { // add code here to process the incident record }

###### To find all incidents in which a short_description has been supplied, use the following

query:

var target = new GlideRecord('incident'); target.addNotNullQuery('short_description'); target.query(); // Issue the query to the database to get all records while (target.next()) { // add code here to process the incident record }

###### For more information on the GlideRecord API and its available methods, see GlideRecord.

GlideRecord query examples

###### These examples demonstrate how to perform various GlideRecord queries.

##### query

var rec = new GlideRecord('incident'); rec.query(); while(rec.next()) { gs.print(rec.number + ' exists'); }

##### update

var rec = new GlideRecord('incident'); rec.addQuery('active',true); rec.query(); while(rec.next()) { rec.active = false;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 104

gs.print('Active incident ' + rec.number = ' closed'); rec.update(); }

##### insert

var rec = new GlideRecord('incident'); rec.initialize(); rec.short_description = 'Network problem'; rec.caller_id.setDisplayValue('Joe Employee'); rec.insert();

##### delete

var rec = new GlideRecord('incident'); rec.addQuery('active',false); rec.query(); while(rec.next()) { gs.print('Inactive incident ' + rec.number + ' deleted'); rec.deleteRecord(); }

##### Querying Service Catalog Tables

You cannot directly query the variables of the Service Catalog Request Item table [sc_req_item]. Instead, query the Variable Ownership table, [sc_item_option_mtom], by adding two queries, one for the variable name and another for the value. The query returns the many-to-many relationship, which you can dot-walk to the requested item. The following example finds the

###### request items that have the variable item_name with a value of item_value and displays the

request item numbers:

var now_GR = new GlideRecord('sc_item_option_mtom'); gr.addQuery('sc_item_option.item_option_new.name','item_name'); gr.addQuery('sc_item_option.value','item_value'); gr.query();

while(gr.next()) { gs.addInfoMessage(gr.request_item.number); }

For additional information see GlideRecord.

Running order guides automatically

Service catalog order guides allow customers to make a single service catalog request that can generate several ordered items. Administrators can configure order guides to run automatically, from a workflow or a script to generate a set of ordered items without manually submitting a service catalog request. Administrators can also review and reprocess the order guide failures.

As a use case, an onboarding workflow for a new employee can run an order guide to automatically order items for that employee.

##### Note: You can only save catalog items, not the order guide (that is, initial landing page

options).

Running order guides from scripts

Running order guides with a server-side script is more complex than using workflows, but it allows more flexibility and can be used in non-workflow situations.

For example, you can use order guide scripts with UI actions or server-side business rules.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 105

##### Note: When order guides run automatically, order guide UI policies are not enforced. Also,

options in the Choose Options screen cannot be selected, so make sure that order guide rules define sensible defaults for these options to avoid processing failures.

###### Use the SNC.ScriptableOrderGuide Java class to run order guides with a script.

###### Use the SNC.ScriptableOrderGuide(String orderGuideId) constructor to create

a new ScriptableOrderGuide object.

##### Method summary

Method Return Value Description

process(String json) boolean Runs the order guide using the JSON encoded string parameter as the input for the order guide. Returns true or false depending on whether processing was successful or not.

##### Note: Both opened_by and requested_for

parameters must be passed to the order guide, and both must have valid user record sys_id values.

If processing is successful and a request is created by the order guide, you can retrieve the request

###### GlideRecord using getRequest().

If the processing fails, you can retrieve the failure

###### GlideRecord using getFailure(), then submit the

script for reprocessing using reprocess.

reprocess(GlideRecord failure)

boolean Runs the order guide again using the JSON encoded string parameter stored in the failure GlideRecord.

getMessage() String Retrieves the message populated after processing or reprocessing.

getRequest() GlideRecord Retrieves the request GlideRecord.

getFailure() GlideRecord Retrieves the failure GlideRecord from the Scriptable Order Guide Failures [sc_script_order_guide_failure] table.

##### Script example

This script processes an order guide called IT Onboarding SOG.

// Creating the object to later be JSON encoded var json = {"opened_by":"62826bf03710200044e0bfc8bcbe5df1","requested_for" :"06826bf03710200044e0bfc8bcbe5d8a","department":"221f3db5c61122 84009f4becd3039cc9"};

var now_GR = new GlideRecord("sc_cat_item_guide"); if (gr.get("name","IT Onboarding SOG")) { var sog = new SNC.ScriptableOrderGuide(gr.getValue("sys_id")); var result = sog.process(new JSON().encode(json)); if(!result)

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 106

gs.log("Processing the scriptable order guide failed with message: " + sog.getMessage()); else { var request = sog.getRequest(); gs.log("Request created " + request.sys_id); } }

Running order guides from workflows

Running an order guide from a workflow is suitable if you include order guides as part of a broader workflow-based process.

For example, an activity within an onboarding workflow for a new employee can automatically run an order guide to order items for that employee.

##### Note: When order guides run automatically, order guide UI policies are not enforced. Also,

options in the Choose Options screen cannot be selected, so make sure that order guide rules define sensible defaults for these options to avoid processing failures.

To run order guides from a workflow, use the Scriptable Order Guide workflow activity.

Running order guides from workflows

Field Description

Order Guide

The name of the order guide that this activity processes. For example, Example Employee Onboarding IT.

Script A script passing information to the order guide. This information is sent as a JSON

###### encoded string parameter assigned to the answer variable.

The script must meet these requirements:

**-** The names of the variables in the script must match the names used within the

###### order guide. For example, if the order guide uses a department variable in a rule

###### condition, the script must also pass a department parameter.

**-** Both opened_by and requested_for parameters must be passed to the order guide, and both must have valid user record sys_id values.

##### Results

**- Success** : the activity successfully processed the order guide. This does not mean a request was created. If a request was created, the request sys_id is added to the workflow scratchpad

###### under the sc_request variable.

**- Failure** : while processing the order guide a failure occurred, creating a failure record. If the processing fails, you can view and edit the failure record.

##### Workflow example

The Example Employee Onboarding IT Workflow workflow uses this example to generate IT catalog items for a new employee as part of an onboarding process.

The activity uses this script to:

**1.** Take a JSON string generated previously from the HR change record.

###### 2. Append the mandatory opened_by and requested_for parameters to that string.

**3.** Submit the new string for processing by the order guide.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 107

var parameters = new JSON().decode(current.payload);

// Need to amend the json object to include additional values. parameters.opened_by = current.opened_by + ""; parameters.requested_for = current.opened_for + "";

answer = new JSON().encode(parameters);

View order guide failures

Order guide processing can fail, for example if the order guide being run does not exist. When a failure occurs during the order guide processing, the Scriptable Order Guide Failures submodule allows you to review and reprocess the failures. A record is created for each failure and once you fix the errors that caused the initial failure, you can reprocess the failed order guides.

###### About this task

If a failure occurs, a failure record is created in the Scriptable Order Guide Failures [sc_script_order_guide_failure] table.

To view details of a failure, navigate to Service Catalog > Catalog Administration > Scriptable Order Guide Failures , then open a failure record.

Reprocessing failures: If you have fixed the error that caused the initial failure, you can reprocess failed order guides.

###### Procedure

**1.** Navigate to **Service Catalog** > **Catalog Administration** > **Scriptable Order Guide Failures**.

**2.** Open the failure record.

**3.** Click the **Reprocess** related link.

To reprocess one or more failures:

a. Navigate to Service Catalog > Catalog Administration > Scriptable Order Guide Failures.

b. Select the check box beside one or more records to reprocess.

c. Select Reprocess from the Actions choice list.

Scriptable assignment of execution plans

Each catalog item has an associated execution plan, used whenever an item of that type is ordered; if no plan is specified, the default plan is used. This default is effective for most organizations, but your execution plan may need to vary based on additional criteria.

For example, in the base system service catalog, a request for a new PC always uses the PC Delivery Plan. However, this plan may need to vary for unusual circumstances such as when a requester is working from home, at a remote location.

To provide this flexibility, you can use a script to override the default execution plan on a specific catalog item.

Limitations during script execution

Execution plan scripts have limitations that need to be considered during their implementation.

While the execution plan script runs:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 108

**-** You cannot interact with any catalog tasks as catalog tasks are only created after the execution plan is selected.

**-** Some fields such as **total delivery time** and **due date** are not yet calculated, although the

###### request itself is available within the script via current.request().

**-** Approvals have not yet been generated.

Writing the scripts

Follow these guidelines when writing execution plan scripts.

Execution plan scripts can access the same global variables and other functions as in any other server side execution plan.

**-** current is the currently-requested catalog item, sc_req_item.

**-** current.delivery_plan() is the assigned execution plan for this catalog item.

The evaluated value from the script is used as the sys_id of the execution plan.

Simple example:

current.delivery_plan.setDisplayValue('PC Delivery Plan')

If an invalid value is returned, such as undefined or not found, then the existing assigned value is used.

More complex example:

getexecutionplan(); function getexecutionplan() { var location = current.request.requested_for.location.getDisplayValue(); // if we're in Atlanta if (location == 'Atlanta') { // use the remote pc delivery plan instead of the normal one var remote_plan = new GlideRecord('sc_cat_item_delivery_plan'); remote_plan.addQuery('name', 'Remote PC Delivery Plan'); remote_plan.query(); remote_plan.next(); current.delivery_plan = remote_plan.sys_id; return remote_plan_sys_id; } return current_delivery_plan; }

In this example, any time a request is for a user in Atlanta, ServiceNow uses the Remote PC Delivery Plan. Otherwise, the execution plan is not overridden and ServiceNow uses the catalog item's normal execution plan, the PC Delivery Plan.

Add a script to a catalog item

You can add a script to a catalog item so that the script runs each time a user requests that item.

###### Procedure

**1.** Navigate to **All** > **Service Catalog** > **Maintain Items**.

**2.** Select the relevant catalog item to which you wish to add the script. © 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 109

**3.** Configure the catalog item form to add the execution plan script field, often named **Delivery** **Plan Script**.

**4.** Fill in the script details.

**5.** Update the item form with your changes.

###### Result

The script runs each time that item is requested, selecting the execution plan to run with that item.

Use a script to approve an execution plan

You can use an approval rule script to approve an execution plan.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 110

###### Procedure

**1.** Retrieve an approval execution plan task.

**2.** View the **Approval Script** field.

**3.** Fill in an approval script using the same syntax and rules you would use on an approval rule.

###### Example:

For example, in the script below, the requester’s manager is the approver.

Script specifying the approver

Using regular expressions in server-side scripts

JavaScript regular expressions automatically use an enhanced regex engine, which provides improved performance and supports all behaviors of standard regular expressions as defined by Mozilla JavaScript. The enhanced regex engine supports using Java syntax in regular expressions.

###### The SNC.Regex API is not available for scoped applications. For scoped applications, remove

###### the SNC.Regex API and use standard JavaScript regular expressions.

For more information on JavaScript regular expressions, see the Mozilla JavaScript documentation on regular expressions and RegExp.

Using Java syntax in JavaScript regular expressions

The enhanced regex engine includes an additional flag to allow Java syntax to be used in JavaScript regular expressions.

Regular expressions with the additional flag work in all places that expect a regular expression, such as String.prototype.split and String.prototype.replace. To use Java syntax in a regular expression, use the Java inline flag j, for example /(?ims)ex(am)ple/j

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 111

Extended regular expression flags

Flag Description

j Defines a regular expression that executes using the Java regular expression engine. It can be used to access Java-only features of regular expressions (such as look behind, negative look behind) or to use Java regular expressions without translating them into JavaScript regular expressions. For example: var regex = /ex(am)ple/j;

Convert SNC Regex expressions to enhanced regex expressions

When you upgrade to Eureka Patch 5 or later releases, you should convert scripts that use the

###### SNC.Regex API to use regular JavaScript expressions.

###### Procedure

**1.** From the original expression, such as: SNC.Regex("/expr/is");, create a new regular expression object using the pattern with the slashes stripped.

Example

new RegExp('expr');

###### 2. Move the SNC.Regex flags to the start of the expression using Java’s inline flag special

construct.

Example

new RegExp('(?is)expr');

###### 3. Add the j flag to the RegExp to tell the engine to treat the expression as a Java expression.

##### Note: If you know that the script being converted does not use Java syntax, it is not

###### necessary to use the j flag.

Example

new RegExp('(?is)expr', 'j');

###### 4. Add the g flag to handle multiple matches or a global replace.

Example

new RegExp('(?is)expr', 'jg');

###### Example:

Using SNC.Regex:

var r = new SNC.Regex('/world/'); var str = 'helloworld'; var replaced = r.replaceAll(str, 'there'); // replaced == 'hellothere'

Using a JavaScript regular expression:

var r = new RegExp('world', 'jg'); var str = 'helloworld'; var replaced = str.replace(r, 'there'); // replaced == 'hellothere'

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 112

Scriptable service catalog variables

You can use scripting to reference any request item variable from a table in scoped and nonscoped environment.

An example of a variable reference follows.

current.variables.<variable_name>

###### Where current refers to the current record, and <variable_name> is the name of your

variable.

##### Note: In order to reference a variable from JavaScript, it must have a name.

When a variable is part of a variable set, you can reference it as current.variables.<variable_name> or current.variables.<variable_set_name>.<variable_name>.

Variable set is also a first-class citizen in Service Catalog. Like variables, a variable set has read, write, and create roles. If roles are provided for a variable set, the roles are applicable for the variables within the set. Roles of an individual variable are overridden by the roles of the variable set.

##### Print a variable

var original = current.variables.original_number; gs.print(original);

##### Set a variable

current.variables.name = "Auto-Generated:" + current.variables.asset_tag;

##### Create an inventory item with fields set from variables

doCreation();

function doCreation ( ) { var create = current.variables.create_item; if (create == 'true') { // we want to create an asset var computer = new GlideRecord('cmdb_ci_computer'); computer.initialize(); computer.asset_tag = current.variables.asset_tag; computer.serial_number = current.variables.serial_number; computer.name = current.variables.name; computer.manufacturer = current.variables.company; computer.insert(); } }

##### Get GlideElementVariable of variables and variable sets associated with a

##### GlideRecord

now_GR.variables

##### Get the name value pair of variables associated with a GlideRecord

now_GR.variables.getVariableValue();

##### Get a list of GlideElementVariable for variables within a task record

now_GR.variables.getElements();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 113

##### Get a list of GlideElementVariable for variables (including multi-row variable set)

##### within a task record

now_GR.variables.getElements(true);

##### Note: The getElements() method returns all the variables present on the given task

record except for the formatter variables like label, break, container end, container split, and so on.

##### APIs for GlideElementVariable

**-** now_GR.variables.<var_name>.isMultiRow(): Get whether the GlideElementVariable is a multi-row variable set or a variable.

**-** now_GR.variables.<var_name>.getQuestion(): Get the Question object for

###### a variable. Applicable only for a variable ( isMultiRow() is false) and not for a multi-row

variable set.

**-** now_GR.variables.<var_name>.getLabel(): Get the label of the GlideElementVariable. For a variable, the label of the variable is returned. For multi-row variable set, the title of the variable set is returned.

**-** now_GR.variables.<var_name>.canRead(): Get whether the user can view a variable or multi-row variable set.

**-** now_GR.variables.<var_name>.canWrite(): Get whether the user can edit a variable or multi-row variable set.

**-** now_GR.variables.<var_name>.getDecryptedValue(): Get the decrypted value for a masked variable. Applicable only for a masked variable.

**-** now_GR.variables.<var_name>.getRows(): Get the list of row objects for a multi-

###### row variable set. Applicable only for a multi-row variable set ( isMultiRow() is true).

**-** now_GR.variables.<var_name>.getRowCount(): Get the number of rows for multi-

###### row variable set. Applicable only for a multi-row variable set ( isMultiRow() is true).

##### Example to access variables of GlideRecord for the Task table

var now_GR = new GlideRecord('sc_req_item'); if (now_GR.get('635a1f5387320300e0ef0cf888cb0b73')) { var variables = now_GR.variables.getElements(); for (var i=0;i<variables.length;i++) { var question = variables[i].getQuestion(); gs.log(question.getLabel() + ":" + question.getValue()) } }

##### Example to access a multi-row variable set of GlideRecord for the Task table

var now_GR = new GlideRecord('sc_req_item'); now_GR.get('02c38dcd87013300e0ef0cf888cb0bb2');

var vars = now_GR.variables.getElements(true);

for (var i=0; i<vars.length; i++) { var now_V = vars[i]; if (now_V.isMultiRow()) { var rows = now_V.getRows(); for (var j=0; j<now_V.getRowCount(); j++) {

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 114

var row = rows[j]; var cells = row.getCells(); for (var k=0; k<cells.length; k++) { var cell = cells[k]; gs.info(cell.getLabel() + ":" + cell.getCellDisplayValue()) } } } }

##### Multi-row variable set

Multi-row variable set

Operation Usage

Table operations

Return JSON array value as String now_GR.variables.table_var

Set value of a multi-row variable set now_GR.variables.table_var = <val>

##### Note: An array of ordered (key, value)

pairs is also applicable as input.

Get value of column, var1, of a multi-row variable set now_GR.variables.table_var.v ar1

Set value of a variable set, var1 now_GR.variables.table_var.v ar1 = <val>

##### Note: An array of ordered (key, value)

pairs is also applicable as input.

Row operations

Get the current row count now_GR.variables.table_var.get RowCount()

Returns the row specified by the variable "i" getRow(<int> i) var row = now_GR.variables.table_var.ge tRow(<int> i);

Get the cell value for a question column mapped to <var_name> row.<var_name>

Set the cell value for a question column mapped to <var_name> row.setCellValue('<var_name>', value)

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 115

Multi-row variable set (continued)

Operation Usage

Set the cell value for a question column mapped to <var_name>

row.<var_name> = value

Add an empty row at the end of the table and return a scriptable object

var row = now_GR.variables.table_var.ad dRow()

Delete a row row.deleteRow()

##### Notes and limitations

**-** //Single column of table_Var

**-** now_GR.variables.table_var.var1

**-** now_GR.variables.table_var.var1 = <val>

**1.** You can only set a variable in a before business rule. Variables set in an after rule are not written to the database.

**2.** There is nothing in place to prevent namespace collision with variables. Creating two variables named computer_speed would result in only one of them showing up; the second one would overwrite the first one.

**3.** Date/time variables use the same time zone formatting and storage rules as all other dates in the system. They are stored internally in GMT, but translated into the user's local time zone and format for display.

Setting a GlideRecord variable to 'NULL'

GlideRecord variables (including current) are initially null in the database. Setting these back to an empty string, a space, or the JavaScript null value will not result in a return to this initial state.

##### Note: This functionality requires a knowledge of JavaScript.

###### To set it back to the initial state, simply set the value to 'NULL'. Note that the update() function

does not run on the current object but rather on the record. The object displays the initial value until it is called again from the record.

##### Note: Functionality described here requires the Admin role.

##### Example 1

var grIncident = new GlideRecord('incident'); grIncident.addNotNullQuery("assigned_to"); grIncident.query(); if (grIncident.next()) { gs.log(“The incident record that is going to be updated is “ + grIncident.number); gs.log("Previous Value of 'Assigned To' field: " + grIncident.assigned_to); grIncident.assigned_to = "NULL"; grIncident.update();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 116

gs.log("Current Value of 'Assigned To' field: " + grIncident.assigned_to); }

##### Example 2 (Business Rule)

current.u_affected_value = 'NULL'; current.update();

Schedule Pages

A schedule page is a record that contains a collection of scripts that allow for custom generation of a calendar or timeline display.

Creation of timeline schedule pages requires understanding of the page/event flow and the ability to write client and server side JavaScript.

Schedule pages form

To access schedule pages, navigate to System Scheduler > Schedules > Schedule Pages.

The form provides the following fields, depending upon the View Type selected:

Schedule pages form

Field

Field Type

Description

Name String General name that is used to identity the current schedule page.

Schedule type

String The schedule type is a string that is used to uniquely identity the schedule page via the "sy URI parameter. For example, a schedule page could be accessed as follows:

/show_schedule_page.do? sysparm_type=gantt_chart&sysparm_timeline_task_id=d530bf907f00

###### Alternatively, the schedule page can also be accessed by setting the " sysparm_page_s

of the unique 32 character hexadecimal system identifier of the schedule page.

View Type Choice Each view type displays different field combinations. There are two options available:

**-** Calendars

**-** Timelines

Description String General description that provides additional information about the current schedule page.

Init funciton name

String

##### Note: This functionality is only used by Calendar type schedule pages.

The init function name specifies the name of the JavaScript function to call inside the Clien type schedule pages.

HTML String

##### Note: This functionality is only used by Calendar type schedule pages.

The HTML field is a scriptable section that is parsed by Jelly and injected into the display p calendar. It can be used to pass in variables from the server and define extra fields are nec

Client script

String The client script is a scriptable section that allows for configuring options of the schedule p different depending on the schedule page view type and is discussed below.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 117

Schedule pages form (continued)

Field

Field Type

Description

Server AJAX processor

String

##### Note: This functionality is only used by Calendar type schedule pages.

The Server AJAX processor is specific to calendar type schedule pages that is used to retu and spans to be displayed.

Timeline schedule pages

A Timeline Schedule Page is a specific record that contains configuration information for displaying time based points and spans in a "timeline" like fashion.

The timeline schedule page references a script include that extends from AbstractTimelineSchedulePage to perform dynamic modification to the timeline based on different events and conditions. Both the schedule page and the script include for timeline generation allow for extreme customization and their corresponding application programming interface (API) is documented below.

The following diagram shows the series of events that occur when a timeline schedule page is accessed. Once the timeline has been loaded, all subsequent events, such as events resulting from timeline interaction (e.g. moving a timeline span), follow the same logic flow shown in the gray event box.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 118

Timeline Flow

##### Applications that use schedule pages to generate time lines

**-** Project Management

**-** Maintenance Schedules

**-** Group On-Call Rotation

**-** Field Service Management

Timeline schedule page example

The following example demonstrates how to create a timeline schedule page with corresponding script include utilizing a majority of the API described above.

For this example we are going to create an Incident Summary Timeline for a project support manager to visualize all of the new incidents. All new incidents should be displayed as single points where the priority of the incident is distinguished by a different point icon. Additionally, all closed incidents should be displayed on the timeline in a separate group that shows the duration of the incident before it was closed. Since the Project Manager wants to be able to easily close

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 119

new items that are resolved without using any form lists, we will handle the vertical move event allowing the new incidents to be dragged into the closed incident group or items within.

##### Schedule Page

Create a new schedule page with the following properties:

**- Name** : Hardware Incidents

**- Schedule type** : incident_timeline

**- View Type** : Timeline

**- Client Script** :

// Set our page configuration glideTimeline.setReadOnly(false); glideTimeline.showLeftPane(true); glideTimeline.showLeftPaneAsTree(true); glideTimeline.showTimelineText(true); glideTimeline.showDependencyLines(false); glideTimeline.groupByParent(true); glideTimeline.setDefaultPointIconClass('milestone');

// We will define what items to display and provide a custom event handler for moving new items to the closed state glideTimeline.registerEvent('getItems', 'IncidentTimelineScriptInclude'); glideTimeline.registerEvent('elementMoveY', 'IncidentTimelineScriptInclude');

##### Script Include

Now that the schedule page has been created we need to generate a matching script include for the events that were registered. Create a new script include with the following properties:

**- Name** : IncidentTimelineScriptInclude

**- Active** : Checked

**- Glide AJAX enabled** : Checked

**- Script** :

// Class Imports

var IncidentTimelineScriptInclude = Class.create(); IncidentTimelineScriptInclude.prototype = Object.extendsObject(AbstractTimelineSchedulePage, {

/////////////////////// // GET_ITEMS /////////////////////////////////////// getItems:function() { // Specify the page title this.setPageTitle('My Custom Incident Summary Timeline');

var groupNew = new GlideTimelineItem('new'); groupNew.setLeftLabelText('New Incidents'); groupNew.setImage('../images/icons/all.gifx'); groupNew.setTextBold(true);

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 120

this.add(groupNew);

var groupClosed = new GlideTimelineItem('closed'); groupClosed.setLeftLabelText('Closed Incidents'); groupClosed.setImage('../images/icons/all.gifx'); groupClosed.setTextBold(true); groupClosed.setIsDroppable(true);

// This allows us to drag an open incident onto the closed group row. this.add(groupClosed);

// Get all the incidents and let's add only the new/closed ones appropriately var now_GR = new GlideRecord('incident'); gr.query(); while(gr.next()) { // Only loop through new/closed incidents if(gr.incident_state != '1' && gr.incident_state != '7') continue;

// Ok, we have a new/closed incident. Create the item and the span first. var item = new GlideTimelineItem(gr.getTableName(), gr.sys_id); var span = item.createTimelineSpan(gr.getTableName(), gr.sys_id);

// Specific properties for a new incident if(gr.incident_state == '1') { // New item.setParent(groupNew.getSysId()); item.setImage('../images/icons/open.gifx');

span.setTimeSpan(gr.getElement('opened_at').getGlideObject().ge tNumericValue(),

gr.getElement('opened_at').getGlideObject().getNumericValue());

// We will show different colors based upon the priorities only for new incidents switch(gr.getElement('priority').toString()) { case '1': span.setPointIconClass('red_circle'); break; case '2': span.setPointIconClass('red_square'); break; case '3': span.setPointIconClass('blue_circle'); break; case '4': span.setPointIconClass('blue_square'); break; case '5': span.setPointIconClass('sepia_circle'); break; default: // Otherwise, the default point icon class will be used (Milestone) } } // Specific properties for a closed incident else if(gr.incident_state == '7') {

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 121

item.setParent(groupClosed.getSysId()); item.setImage('../images/icons/closed.gifx');

span.setTimeSpan(gr.getElement('opened_at').getGlideObject().ge tNumericValue(),

gr.getElement('closed_at').getGlideObject().getNumericValue() ); }

// Common item properties item.setLeftLabelText(gr.short_description);

// Common span properties span.setSpanText(gr.short_description); span.setTooltip('<strong>' + GlideStringUtil.escapeHTML(gr.short_description) + '</strong><br>' + gr.number); span.setAllowXMove(false); span.setAllowYMove(gr.canWrite()? true:false); span.setAllowYMovePredecessor(false); span.setAllowXDragLeft(false); span.setAllowXDragRight(false);

// Now we add the actual item this.add(item); } } ,

//////////////////////// // ELEMENT_MOVE_Y // ///////////////////////////////////////////////////////////

/\*\* _ This is one of the AbstractTimelineSchedulePage event handler methods that corresponds to a vertical _ move. The arguments for this function are defined in the API section of the event handler methods. \*/ elementMoveY: function(spanId, itemId, newItemId) {

// Get information about the current incident var now_GR = new GlideRecord('incident'); gr.addQuery('sys_id', spanId); gr.query(); if(!gr.next()) return this.setStatusError('Error', 'Unable to lookup the current incident.');

// Only allow the new incidents to have their state adjusted. if(gr.incident_state != '1') return this.setStatusError('Error','Only new incidents can have their state adjusted.');

// Get information about the dropped GlideTimelineItem. If it was dropped in an item on the "New Incidents"

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 122

// group let's do nothing. If it was dropped in the "Closed Incidents" then let's adjust the state automatically. var grDropped = new GlideRecord('incident'); grDropped.addQuery('sys_id', newItemId ); grDropped.query(); if(!grDropped.next() || grDropped.incident_state == '7') { // This means the dropped item was either the 'Closed Incidents' group (which has no record or sys_id) or an // existing incident that is closed. The 'New Incidents' also has no sys_id; however, the default behavior for // items without a sysId is to be non-droppable. This is why we explicitly denoted the 'Closed Incidents' to // be marked as "droppable".

// Return a dialog prompt this.setStatusPrompt('Confirm', 'Are you sure you want to close: ' + '<div style="margin:10px 0 10px 14px;padding:4px;background-color:﷯EBEBEB;"strong' + GlideStringUtil.escapeHTML(gr.short_description) + '</strong><br/><div class="font_smaller">' + now_GR. number + '</div></div>', 'this.\_elementMoveYHandler_DoClose', // This function is for when the OK button is clicked. 'this.\_elementMoveYHandler_DoNothing', // This function is for when the Cancel button is clicked. 'this.\_elementMoveYHandler_DoNothing'); // This function is for when the Close button is clicked. } } ,

\_elementMoveYHandler_DoClose: function(spanId, itemId, newItemId) { // Notice that this function takes the same function arguments as the original function for which it // is a custom event handler for.

// Update the database record from 'New' to 'Closed'. var now_GR = new GlideRecord('incident'); gr.addQuery('sys_id', spanId); gr.query(); gr.next(); gr.setValue('incident_state', '7'); gr.update();

// This will re-render the timeline showing the updated item in the closed group. this.setDoReRenderTimeline(true);

// Let's show a success message this.setStatusSuccess('Success', '<strong>' + gr.short_description + '</strong> was successfully closed.'); } ,

// Since the user clicked cancel or close we simply do nothing.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 123

\_elementMoveYHandler_DoNothing: function(spanId, itemId, newItemId) { }

});

##### Screenshots / Results

**1.** Navigate to:

http://[YOURINSTANCE]:8080/show_schedule_page.do? sysparm_page_schedule_type=incident_timeline

Notice the bold text is the value of the schedule page Schedule type field.

**2.** The page displays a timeline as specified by the schedule page and script include created. A link to this page can be created and placed as a module or UI action as necessary.

Timeline Example Incident Preview

**3.** Attempting to move a closed incident anywhere displays the expected error message.

Timeline Example Error Moving

**4.** Moving the incident: _I need more memory_ displays the following confirmation box.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 124

Timeline Example Confirm Close

**5.** Clicking the **Cancel** button closes the overlay. Clicking the **OK** button actually updates the incident_state of the record and then displays the following success box.

Timeline Example Close Success

**6.** After clicking **OK** , it is clear the incident is now listed in the **Closed Incidents** group.

Timeline Example Incident Updated

XMLDocument script object

A JavaScript object wrapper for parsing and extracting XML data from an XML document (String).

Use this Javascript class to instantiate an object from an XML string, usually a return value from a Web Service invocation, or the XML payload of ECC Queue. Using the XMLDocument object in a Javascript business rule lets you query values from the XML elements and attributes directly.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 125

##### Constructor

The constructor of a script object creates a new instance of the object to be used.

var xmlString = "<test>" + " <one>" + " <two att=\"xxx\">abcd1234</two>" + " <three boo=\"yah\" att=\"yyy\">1234abcd</three>" + " <two>another</two>" + " </one>" + " <number>1234</number>" + "</test>";

var xmldoc = new XMLDocument(xmlString);

To perform XML parsing of an XML string that is name space qualified, specify "true" for the second argument for the XMLDocument constructor. The following is an example of parsing and XML string that contains name space qualification of its elements.

var xmlString = "<bk:book xmlns:bk='urn:loc.gov:books' xmlns:isbn='urn:ISBN:0-395-36341-6'>" + "<bk:title>Cheaper by the Dozen</bk:title>" + "<isbn:number>1568491379</isbn:number>" + "</bk:book>";

var xmldoc = new XMLDocument(xmlString, true); // XML document is name space aware

##### Locating nodes and elements

Now that we have the XMLDocument object, we can call the following APIs to locate nodes and elements of the XML document, as well as extract text from it directly. The query syntax for locating nodes and attributes is based on XPath.

##### Note: XML parsing with this object is not namespace aware, this means that if you are

locating a node name with namespace in it eg. "<names:myelement> ...", the XPath search string would be "//myelement"

The following are examples of locating a node by its XPath and getting the text value out of the resulting node.

var str = xmldoc.getNodeText("//two"); // returns the first occurrence of the node // str == "abcd1234"

str = xmldoc.getNodeText("//three"); // str == "1234abcd"

str = xmldoc.getNodeText("/test/one/\*"); // str == "abcd1234"

str = xmldoc.getNodeInt("//number"); // str == 1234

The following examples locates the node by XPath and uses the API on node and element to get attributes and value.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 126

var node = xmldoc.getNode("/test/one/two"); // node.getNodeName() == "two" // node.getNodeType() == "1" // 1 == ELEMENT_NODE // node.getLastChild().getNodeType() == "3" // 3 == TEXT_NODE // node.getLastChild().getNodeValue() == "abcd1234"

Or you can use the following convenience functions to get the node name and type

str = xmldoc.getNodeName("//three"); // str == "three"

str = xmldoc.getNodeType("//three"); // str == "1"

You can also get a list of nodes that you can iterate or access directly by position

var nodelist = xmldoc.getNodes("//one/\*"); // two, three, and two // nodelist.getLength() == "3" // nodelist.item(0).getNodeName() == "two" // nodelist.item(1).getNodeName() == "three"

The following is an example of parsing an XML string that is qualifed with name spaces.

var xmlString = "<bk:book xmlns:bk='urn:loc.gov:books' xmlns:isbn='urn:ISBN:0-395-36341-6'>" + "<bk:title>Cheaper by the Dozen</bk:title>" + "<isbn:number>1568491379</isbn:number>" + "</bk:book>";

var xmldoc = new XMLDocument(xmlString, true); var str = xmldoc.getNodeText("//bk:title"); // returns the first occurence of the node gs.log(str);

str = xmldoc.getNodeText("/bk:book/\*"); gs.log(str);

str = xmldoc.getNodeInt("//isbn:number"); gs.log(str);

##### Getting attribute values

An attribute is just an extension of a node and so it has all the same APIs.

The following example shows how to query for a node to get its attribute by position

node = xmldoc.getNode("//two"); // node.getAttributes().item(0).getNodeValue() == "xxx"

str = xmldoc.getAttribute("//two", "att"); // str == "xxx"

XPath also has a query syntax for locating the attribute node directly, for example

str = xmldoc.getNodeText("//\*[@att=\"yyy\"]"); // str == "1234abcd"

str = xmldoc.getNode("//@boo").getNodeValue();

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 127

// str == "yah"

##### Creating new elements

An XML element can be created at any level of the XML document once it has been created. Use the setCurrent function to position where the new element will be created as a child element, and use the createElement function to create the element.

var xmlString = "<test>" + " <one>" + " <two att=\"xxx\">abcd1234</two>" + " <three boo=\"yah\" att=\"yyy\">1234abcd</three>" + " <two>another</two>" + " </one>" + " <number>1234</number>" + "</test>";

var xmldoc = new XMLDocument(xmlString); xmldoc.createElement("new", "test"); // creates the new element at the document element level if setCurrent is never called xmldoc.createElement("new2"); // calling without a value will create a new element by itself

var el = xmldoc.createElement("new3"); xmldoc.setCurrent(el); // this is now the parent of any new elements created subsequently using createElement() xmldoc.createElement("newChild", "test");

The resulting XML document looks like this

<test> <one> <two att="xxx">abcd1234</two> <three boo="yah" att="yyy">1234abcd</three> <two>another</two> </one> <number>1234</number> <new>test<new> <new2/> <new3> <newChild>test</newChild> </new3> </test>

XMLHelper

The XML helper script include makes it easy to parse XML in scripts.

Use the following methods to export XML to JSON, or JSON to XML.

**-** The toObject() method returns the XML elements as JSON properties. This method works properly whether the supplied parameter is an XML document or an XML string. This method has an optional parameter of the XML input for conversion as an alternative to specifying the XML input in the constructor.

**-** The toXMLDoc() method returns JSON provided as XML elements.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 128

##### Note: You must escape ampersand characters (&amp) in your XML or the conversion

silently fails.

##### Example

The following example shows how to convert an XML document into JSON and uses a recursive function to output each member. The recursive function helps indicate how the XML document structure is rendered as JSON.

var xmlString = "<company>" + "<employee>" + "<id>10</id>" + "<firstname>Tom</firstname>" + "<lastname>Cruise</lastname>" + "<test>test1</test>" + "<test>test3</test>" + "</employee>" + "<employee>" + "<id>20</id>" + "<firstname>Paul</firstname>" + "<lastname>Enderson</lastname>" + "<test>test6</test>" + "<test>test5</test>" + "</employee>" + "<employee>" + "<id>30</id>" + "<firstname>Paul</firstname>" + "<lastname>Bush</lastname>" + "<test>test2</test>" + "<test>test4</test>" + "</employee>" + "</company>"; var helper = new XMLHelper(xmlString); var obj = helper.toObject(); logObj(obj, "\*");

function logObj(obj, sep) { for (x in obj) { if (typeof obj[x] != "function") { gs.log(sep + x + ":: " + obj[x]); } logObj(obj[x], sep + "\*"); } }

Output:

*** Script: *employee:: [object Object],[object Object],[object Object] \*** Script: **2:: [object Object] \*** Script: **_id:: 30 _** Script: **_test:: test2,test4 _** Script: \***_0:: test2 _** Script: \***_1:: test4 _** Script: **_firstname:: Paul _** Script: **_lastname:: Bush _** Script: **0:: [object Object] \*** Script: **_id:: 10 _** Script: **_test:: test1,test3 _** Script: \***_0:: test1 _** Script: \***_1:: test3 _** Script: **_firstname:: Tom _** Script: **_lastname:: Cruise _** Script: **1:: [object Object] \*** Script: **_id:: 20 _** Script: **_test:: test6,test5 _** Script: \***_0:: test6 _** Script: \***_1:: test5 _** Script: **_firstname:: Paul _** Script: \*\*\*lastname:: Enderson

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 129

JavaScript engine on the platform

The JavaScript engine that evaluates server-side scripts supports the ECMAScript 2021 (ES12) standard.

No plugins or properties are required to install the new JavaScript engine.

The benefits of the new engine are:

**-** Modern library code and scripting features, such as optional chaining, destructuring, const and let declarations, and arrow functions

**-** Follows standard ECMAScript 2021 behavior

##### What to know

The JavaScript engine provides an improved environment for developing scripts.

**-** Beginning with the Xanadu release, when you create new scripts, ECMAScript 2021 (ES12) mode is turned on by default regardless of the JavaScript mode configured for the application.

**-** Beginning with the Tokyo release, new and existing scoped applications can run in ECMAScript 2021 (ES12) mode.

**-** Compatibility mode supports the legacy modifications to the legacy JavaScript engine.

**-** Legacy code continues to work.

You configure the mode that the JavaScript engine uses in the design and runtime settings for applications. Available modes are ECMAScript 2021 (ES12), ES5 Standards, and Compatibility.

Related topics

Update a custom application record

JavaScript modes

JavaScript mode is a design and runtime setting for custom applications and scripts. To support existing server-side scripts and new scripts developed to the ECMAScript 2021 standard, the JavaScript engine has three modes: ECMAScript 2021 (ES12), ES5 Standards, and Compatibility.

The JavaScript mode controls which JavaScript features you have access to in an application or script. The default mode for new scoped applications is ECMAScript 2021 (ES12) and for new global applications, it’s ES5 Standards. You can also turn on ECMAScript 2021 (ES12) mode for individual scripts in applications that use ES5 Standards or Compatibility mode.

For more information about features supported by the ECMAScript 2021 (ES12) and ES5 Standards modes, see JavaScript engine feature support.

##### ECMAScript 2021 (ES12) mode

ECMAScript 2021 (ES12) mode is the default mode when you create new scoped applications. When you create new scripts, ECMAScript 2021 (ES12) mode is turned on by default regardless of the JavaScript mode configured for the application. This mode doesn’t preserve the legacy behaviors in the pre-Tokyo JavaScript engine or work with global scripts.

ECMAScript 2021 (ES12) mode supports a subset of ECMAScript 2021 (ES12) and ECMAScript 2022 (ES13) syntax and features, including the following features:

**-** Default function parameters

**-** Rest parameters

**-** For-of loops

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 130

**-** Template literals

**-** Destructuring

◦ Declarations

◦ Assignment

◦ Parameters

**-** Const declaration

**-** Let declaration

**-** Arrow functions

**-** Class declarations

**-** Map set

**-** Optional chaining operator (?.)

To learn about specific ECMAScript 2021 (ES12) features, see the Let's Learn ECMAScript 2021 videos on the ServiceNow Dev Program YouTube channel.

##### ES5 Standards mode

ES5 Standards mode is the default mode for global applications and is an option for scoped applications. This mode doesn’t preserve the legacy behaviors in the pre-Helsinki JavaScript engine.

ES5 standards mode supports ECMAScript5 syntax and features, including the following features:

**-** The "use strict" declaration

**-** Control over extensibility of objects

**-** Get and set properties on objects (accessors)

**-** Control over writability, configurability, and enumerability of object properties

**-** New Array and Date methods

**-** Native JSON support

**-** Support for modern third-party libraries such as lodash.js and moment.js

##### Compatibility mode

Compatibility mode is used for all scripts developed prior to the addition of ES5 Standards mode. Compatibility mode has some differences from the previous JavaScript engine.

JSON support changes:

**-** JSON.stringify() and JSON.parse() are implemented using the ES5 Native JSON object.

**-** The new JSON().encode() and new JSON().decode() are still supported, but should only be used when the legacy behavior is required.

The use of third-party JavaScript libraries isn’t supported in Compatibility mode.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 131

Considerations for switching JavaScript modes

Switching the JavaScript mode for an application or script might change the behavior of existing scripts. Review some examples of behavior changes before switching JavaScript modes or to troubleshoot any issues that you experience after switching.

For more information about each JavaScript mode, see JavaScript modes and JavaScript engine feature support.

This table highlights how JavaScript behavior has evolved from the lenient and error-prone pre-ES5 environment, to the stricter and more predictable ES5, and lastly the more feature-rich environment of ES12 (ECMAScript 2021).

Behavioral differences in JavaScript modes

Feature Compatibility Mode ES5 Standards Mode

ECMAScript 2021 (ES12)

Arguments object The arguments object exists, but there's no strict mode, so modifications reflect on arguments. Prints:

**_ Script: [object Arguments] _** Script: [object Arguments] **_ Script: [object Arguments] _** Script: 123

In strict mode, the arguments object doesn’t reflect parameter modifications and throws an error. Prints:

sn_es5: 123 sn_es5: undefi ned sn_es5: [object Arguments] sn_es5: 123

The same as ES5.

Boolean overrides Primitive Booleans (true, false) can be overridden, causing unexpected behavior.

Primitive Booleans are more protected, though still can be overridden when assigned to variables.

The same as ES5, but strict mode helps prevent some assignments. The conditional expression should be written in this form:

(cond_expr inst anceof Boolean? cond_expr.val ueOf() : cond_expr).

Exception for syntax errors

Syntax errors throw exceptions at runtime. Error handling is inconsistent. Example:

Javascript compiler

More consistent syntax error handling, especially in strict mode. Example:

Evaluator: com.glide.scr

The same as ES5, but with more robust handling and clearer error messages in updated engines. Example:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 132

Behavioral differences in JavaScript modes (continued)

Feature Compatibility Mode ES5 Standards Mode

ECMAScript 2021 (ES12)

exception: unterminated string literal (null.null.sc ript; line 1 ) in : var b = '

ipt.RhinoEcmaE rror: unterminated string literal script : Line( 1 ) column( 9 ) ==> 1 : var b = '

SyntaxError : Unterminated string constant at line 1

==> 1 : var b = '

Increment and decrement

Allowed on variables but could behave unexpectedly with complex expressions. Prints:

**_ Script: c: 1 _** Script: gr.related_in cidents: 1 **_ Script: 2 _** Script: 3

Improved clarity, but still allowed on variables (var, let, const). Prints:

sn_es5: c: 0 sn_es5: gr.related_in cidents: 1 sn_es5: 1 sn_es5: 2

The same as ES5, with stricter rules in some contexts (for example, const).

Line continuations Allowed with a backslash (\) but discouraged due to readability issues. In this example, all three functions are called.

var expr = doFoo(); // do foo

doBar(); // do bar

finish(); // all done eval (expr);

Same as Compatibility mode; no change in handling line continuations. In the previous example, ES5 only calls the first function and treats everything after the first comment including the newline as comment until the expression end.

The same as ES5, but template literals provide a more readable alternative.

Missing semicolons Automatic semicolon insertion (ASI) often led to unexpected behavior.

Throws a syntax error when a semicolon is missing.

The same as ES5. Updated practices encourage explicit semicolons.

Non-existent functions

Calling a non-existent function throws a ReferenceError.

Throws a TypeError if a nonfunction is called.

Throws an EcmaError when a non-existent function is called

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 133

Behavioral differences in JavaScript modes (continued)

Feature Compatibility Mode ES5 Standards Mode

ECMAScript 2021 (ES12)

or a property is referenced.

Non-existent properties

Accessing a nonexistent property returns undefined; no error thrown.

Same as pre-ES5. The same as Compatibility mode and ES5 Standards mode.

Numeric literals Basic decimal and hexadecimal literals.

Introduced stricter parsing rules and better handling of numeric literals.

Added binary (0b), octal (0o), and BigInt literals (123n).

Reserved keyword as property

Using reserved keywords isn't possible.

Reserved keywords can be used as property names without error, for example, obj.for. Prints the object when returned.

The same as ES5.

Treat let and yield as keywords

let and yield aren’t keywords and can be used as identifiers only.

let is introduced as a keyword. yield is reserved in strict mode.

Both are keywords. Using them as identifiers throws syntax errors.

Set the JavaScript mode for an application

Configure which ECMAScript features can be used in an application by selecting the JavaScript mode.

###### Before you begin

Role required: delegated developer role granting full access or admin

###### About this task

The JavaScript mode is a design and runtime setting for custom applications and scripts. To support existing server-side scripts and new scripts developed to the ECMAScript 2021 standard, the JavaScript engine has three modes: ECMAScript 2021 (ES12), ES5 Standards, and Compatibility. For more information about each mode, see JavaScript modes.

For applications that use ES5 Standards or Compatibility mode, you can also turn on ECMAScript 2021 (ES12) for individual scripts in the application. For more information, see Turn on ECMAScript 2021 (ES12) mode for a script.

##### Note: Switching the JavaScript mode to ECMAScript 2021 (ES12) for an existing

application might change the behavior of its scripts. For more information, see Considerations for switching JavaScript modes.

###### Procedure

**1.** In the application navigator, enter sys_app.list.

**2.** Select an application.

**3.** In the **JavaScript Mode** field, select the mode to use.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 134

◦ ECMAScript 2021 (ES12): Supports a subset of ECMAScript 2021 (ES12) and ECMAScript 2022 (ES13) syntax and features.

◦ ES5 Standards Mode: Supports ECMAScript5 syntax and features.

◦ Compatibility Mode: Used for all scripts developed prior to the addition of ES5 Standards mode.

**4.** Select **Update**.

Related topics

Legacy Update a custom application record

Turn on ECMAScript 2021 (ES12) mode for a script

Use the latest JavaScript features supported with ECMAScript 2021 (ES12) mode in server-side scripts in applications that use ES5 Standards mode or Compatibility mode.

###### Before you begin

Role required: delegated developer role or admin

###### About this task

Turning on ECMAScript 2021 (ES12) mode for individual scripts is an option for scripts in global or scoped applications configured to use ES5 Standards mode or Compatibility mode. All scripts in applications with the JavaScript mode set to ECMAScript 2021 (ES12) use ECMAScript 2021 (ES12). Switching the JavaScript mode to ECMAScript 2021 (ES12) for an existing script might change the behavior of the script. For more information, see Considerations for switching JavaScript modes.

##### Note: Global applications can use ECMAScript 2021 (ES12) mode for individual scripts but

not across the application.

###### Procedure

**1.** Navigate to a form with a script field.

Example For example, to open a script include form, navigate to All > System Definition > Script Includes or enter sys_script_include.list in the navigation filter.

**2.** Select an existing script or **New**.

**3.** Select **Turn on ECMAScript 2021 (ES12) mode**.

Example

##### Note: This option is read only for scripts in applications with the JavaScript mode set to

ECMAScript 2021 (ES12), which automatically use ECMAScript 2021 (ES12).

**4.** Select **Submit** or **Update** to save your changes.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 135

JavaScript engine feature support

Compare ECMAScript features between the ECMAScript 2021 (ES12) and ES5 Standards JavaScript modes in Zurich. Both modes support a subset of ECMAScript features.

For more information about these features, see the ECMAScript language specifications (ECMA-262) on the Ecma International website.

##### Support definitions

Supported

The feature has been tested and validated.

Not Supported

The feature has not been validated in the current release.

Disallowed

The feature does not align with the ServiceNow AI Platform programming model or poses a security or performance risk. Disallowed features result in an error.

##### ECMAScript 2022 (ES13) features

##### Important: Prior to deploying code to production, you should test scripts using

supported ECMAScript 2022 (ES13) features thoroughly due to the newly added and partial support of features across this ECMAScript version.

Instance class fields

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

public instance class fields Supported Not Supported

private instance class fields basic support Not Supported Not Supported

private instance class fields initializers Not Supported Not Supported

optional private instance class fields access Not Supported Not Supported

optional deep private instance class fields access

Not Supported Not Supported

computed instance class fields Supported Not Supported

Static class fields

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

public static class fields Supported Not Supported

static class fields use [[Define]] Supported Not Supported

private static class fields Supported Not Supported

computed static class fields Supported Not Supported

Private class methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

private instance methods Not Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 136

Private class methods (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

private static methods Supported Not Supported

private accessor properties Not Supported Not Supported

private static accessor properties Supported Not Supported

.at() method on the built-in indexables

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype.at() Supported Not Supported

String.prototype.at() Supported Not Supported

%TypedArray%.prototype.at() Supported Disallowed

Object.hasOwn

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Basic functionality Supported Not Supported

ToObject called before ToPropertyKey Supported Not Supported

Error.cause property

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Error has cause Supported Not Supported

Error.prototype lacks cause Supported Not Supported

EvalError has cause Supported Not Supported

EvalError.prototype lacks cause Supported Not Supported

RangeError has cause Supported Not Supported

RangeError.prototype lacks cause Supported Not Supported

ReferenceError has cause Supported Not Supported

ReferenceError.prototype lacks cause Supported Not Supported

SyntaxError has cause Supported Not Supported

SyntaxError.prototype lacks cause Supported Not Supported

TypeError has cause Supported Not Supported

TypeError.prototype lacks cause Supported Not Supported

URIError has cause Supported Not Supported

URIError.prototype lacks cause Supported Not Supported

AggregateError has cause Supported Not Supported

AggregateError.prototype lacks cause Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 137

RegExp Match Indices (hasIndices / d flag)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

constructor supports it Not Supported Not Supported

shows up in flags Not Supported Not Supported

Ergonomic brand checks for private fields

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Ergonomic brand checks for private fields Not Supported Not Supported

Class static initialization blocks

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Class static initialization blocks Supported Not Supported

##### ECMAScript 2021 (ES12) features

Promise.any

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

fulfillment Supported Disallowed

AggregateError Supported Disallowed

WeakReferences

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

WeakRef minimal support Disallowed Disallowed

FinalizationRegistry minimal support Disallowed Disallowed

Logical assignment

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

||= basic support Supported Not Supported

||= short-circuiting behavior Supported Not Supported

||= setter not unnecessarily invoked Supported Not Supported

&&= basic support Supported Not Supported

&&= short-circuiting behavior Supported Not Supported

&&= setter not unnecessarily invoked Supported Not Supported

??= basic support Supported Not Supported

??= short-circuiting behavior Supported Not Supported

??= setter not unnecessarily invoked Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 138

Numeric separators

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

numeric separators Supported Not Supported

String.prototype.replaceAll

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

String.prototype.replaceAll Supported Supported

##### ECMAScript 2020 (ES11) features

String.prototype.matchAll

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

throws on non-global regex Supported Not Supported

BigInt

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

constructor Supported Not Supported

BigInt.asUintN Supported Not Supported

BigInt.asIntN Supported Not Supported

BigInt64Array Not Supported Not Supported

BigUint64Array Not Supported Not Supported

DataView.prototype.getBigInt64 Not Supported Not Supported

DataView.prototype.getBigUint64 Not Supported Not Supported

globalThis

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

"globalThis" global property is global object Supported Disallowed

"globalThis" global property has correct property descriptor

Supported Disallowed

Optional chaining operator (?.)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

optional property access Supported Not Supported

optional bracket access Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 139

Optional chaining operator (?.) (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

optional method call Supported Not Supported

optional function call Supported Not Supported

spread parameters after optional chaining Supported Not Supported

Promise.allSettled

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Promise.allSettled Supported Disallowed

Nullish coalescing operator (??)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

nullish coalescing operator (??) Supported Not Supported

##### ECMAScript 2019 (ES10) features

Symbol.prototype.description

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic Supported Not Supported

empty description Supported Not Supported

undefined description Supported Not Supported

String trimming

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

String.prototype.trimLeft Supported Supported

String.prototype.trimRight Supported Supported

String.prototype.trimStart Supported Not Supported

String.prototype.trimEnd Supported Not Supported

Array.prototype.{flat, flatMap}

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Array.prototype.flat Supported Not Supported

Array.prototype.flatMap Supported Not Supported

flat and flatMap in Array.prototype[@@unscopables]

Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 140

Object.fromEntries

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Object.fromEntries Supported Not Supported

Optional catch binding

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic Supported Disallowed

await Disallowed Disallowed

yield Disallowed Disallowed

Function.prototype.toString revision

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

functions created with the Function constructor

Disallowed Disallowed

arrows Disallowed Disallowed

[native code] Disallowed Disallowed

class expression with implicit constructor Disallowed Disallowed

class expression with explicit constructor Disallowed Disallowed

unicode escape sequences in identifiers Disallowed Disallowed

methods and computed property names Disallowed Disallowed

JSON superset

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Line separator can appear in string literals Disallowed Disallowed

Paragraph separator can appear in string literals

Disallowed Disallowed

Well-formed JSON.stringify

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Well-formed JSON.stringify Disallowed Disallowed

##### ECMAScript 2018 (ES9) features

Object rest/spread properties

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

object rest properties Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 141

Object rest/spread properties (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

object spread properties Supported Not Supported

Promise.prototype.finally

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic support Supported Disallowed

don't change resolution value Supported Disallowed

change rejection value Supported Disallowed

Asynchronous iterators

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

async generators Disallowed Disallowed

for-await-of loops Disallowed Disallowed

s (dotAll) flag for regular expressions

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

s (dotAll) flag for regular expressions Supported Not Supported

RegExp named capture groups

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

RegExp named capture groups Supported Not Supported

RegExp Lookbehind Assertions

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

RegExp Lookbehind Assertions Supported Not Supported

RegExp Unicode Property Escapes

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

RegExp Unicode Property Escapes Supported Not Supported

Template literal revision

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

template literal revision Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 142

##### ECMAScript 2017 (ES8) features

Object static methods

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Object.values Supported Not Supported

Object.entries Supported Not Supported

Object.getOwnPropertyDescriptors Supported Not Supported

Object.getOwnPropertyDescriptors doesn't provide undefined descriptors

Not Supported Not Supported

String padding

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

String.prototype.padStart Supported Not Supported

String.prototype.padEnd Supported Not Supported

Trailing commas in function syntax

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

in parameter lists Supported Not Supported

in argument lists Supported Not Supported

Async functions

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

return Supported Disallowed

throw Supported Disallowed

no line break between async and function Supported Disallowed

no "prototype" property Disallowed Disallowed

await Supported Disallowed

await, rejection Supported Disallowed

must await a value Disallowed Disallowed

can await non-Promise values Supported Disallowed

cannot await in parameters Disallowed Disallowed

async methods, object literals Supported Disallowed

async methods, classes Disallowed Disallowed

async arrow functions in methods, classes Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 143

Async functions (continued)

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

async arrow functions Supported Disallowed

correct prototype chain Disallowed Disallowed

async function prototype, Symbol.toStringTag

Disallowed Disallowed

async function constructor Disallowed Disallowed

Shared memory and atomics

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

SharedArrayBuffer Disallowed Disallowed

SharedArrayBuffer[Symbol.species] Disallowed Disallowed

SharedArrayBuffer.prototype.byteLength Disallowed Disallowed

SharedArrayBuffer.prototype.slice Disallowed Disallowed

SharedArrayBuffer.prototype[Symbol.toStringTag] Disallowed Disallowed

Atomics.add Disallowed Disallowed

Atomics.and Disallowed Disallowed

Atomics.compareExchange Disallowed Disallowed

Atomics.exchange Disallowed Disallowed

Atomics.wait Disallowed Disallowed

Atomics.wake Disallowed Disallowed

Atomics.isLockFree Disallowed Disallowed

Atomics.load Disallowed Disallowed

Atomics.or Disallowed Disallowed

Atomics.store Disallowed Disallowed

Atomics.sub Disallowed Disallowed

Atomics.xor Disallowed Disallowed

Object.prototype getter/setter methods

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

**defineGetter** Supported Disallowed

**defineGetter**, symbols Supported Disallowed

**defineGetter**, ToObject(this) Disallowed Disallowed

**defineSetter** Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 144

Object.prototype getter/setter methods (continued)

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

**defineSetter**, symbols Supported Disallowed

**defineSetter**, ToObject(this) Disallowed Disallowed

**lookupGetter** Supported Disallowed

**lookupGetter**, prototype chain Supported Disallowed

**lookupGetter**, symbols Supported Disallowed

**lookupGetter**, ToObject(this) Disallowed Disallowed

**lookupGetter**, data properties can shadow accessors

Disallowed Disallowed

**lookupSetter** Supported Disallowed

**lookupSetter**, prototype chain Supported Disallowed

**lookupSetter**, symbols Supported Disallowed

**lookupSetter**, ToObject(this) Disallowed Disallowed

**lookupSetter**, data properties can shadow accessors

Disallowed Disallowed

Proxy internal calls, getter/setter methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

**defineGetter** Supported Disallowed

**defineSetter** Supported Disallowed

**lookupGetter** Supported Disallowed

**lookupSetter** Supported Disallowed

##### ECMAScript 2016 (ES7) features

Exponentiation (\*\*) operator

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

basic support Supported Not Supported

assignment Supported Not Supported

early syntax error for unary negation without parentheses

Disallowed Disallowed

Array.prototype.includes

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype.includes Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 145

Array.prototype.includes (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype.includes is generic Not Supported Not Supported

%TypedArray%.prototype.includes Supported Disallowed

##### ECMAScript 2015 (ES6) features

Proper tail calls (tail call optimization)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

direct recursion Disallowed Disallowed

mutual recursion Disallowed Disallowed

Default function parameters

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

explicit undefined defers to the default Supported Not Supported

defaults can refer to previous parameters Supported Not Supported

arguments object interaction Supported Not Supported

temporal dead zone Disallowed Disallowed

separate scope Supported Not Supported

new Function() support Disallowed Disallowed

Rest parameters

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

function 'length' property Supported Not Supported

arguments object interaction Not Supported Not Supported

can't be used in setters Disallowed Disallowed

new Function() support Disallowed Disallowed

Spread syntax for iterable objects

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

with arrays, in function calls Supported Not Supported

with arrays, in array literals Supported Not Supported

with sparse arrays, in function calls Supported Not Supported

with sparse arrays, in array literals Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 146

Spread syntax for iterable objects (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

with strings, in function calls Supported Not Supported

with strings, in array literals Supported Not Supported

with astral plane strings, in function calls Supported Not Supported

with astral plane strings, in array literals Supported Not Supported

with generator instances, in calls Disallowed Disallowed

with generator instances, in arrays Disallowed Disallowed

with generic iterables, in calls Supported Not Supported

with generic iterables, in arrays Supported Not Supported

with instances of iterables, in calls Supported Not Supported

with instances of iterables, in arrays Supported Not Supported

spreading non-iterables is a runtime error Supported Not Supported

Object literal extensions

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

computed properties Supported Not Supported

shorthand properties Supported Not Supported

shorthand methods Supported Not Supported

string-keyed shorthand methods Supported Not Supported

computed shorthand methods Supported Not Supported

computed accessors Supported Not Supported

For-of loops

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

with arrays Supported Not Supported

with sparse arrays Supported Not Supported

with strings Supported Not Supported

with astral plane strings Supported Not Supported

with generator instances Disallowed Disallowed

with generic iterables Supported Not Supported

with instances of generic iterables Supported Not Supported

iterator closing, break Supported Not Supported

iterator closing, throw Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 147

Octal and binary literals

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

octal literals Supported Not Supported

binary literals Supported Not Supported

octal supported by Number() Not Supported Not Supported

binary supported by Number() Not Supported Not Supported

Template literals

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

toString conversion Supported Not Supported

tagged template literals Supported Not Supported

passed array is frozen Supported Not Supported

line break normalization Disallowed Disallowed

TemplateStrings call site caching Supported Not Supported

TemplateStrings permanent caching Supported Not Supported

RegExp "y" and "u" flags

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

"y" flag Supported Not Supported

"y" flag, lastIndex Supported Not Supported

"u" flag Supported Not Supported

"u" flag, non-BMP Unicode characters Supported Not Supported

"u" flag, Unicode code point escapes Supported Not Supported

"u" flag, case folding Supported Not Supported

Destructuring, declarations

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

with arrays Supported Not Supported

with sparse arrays Supported Not Supported

with strings Supported Not Supported

with astral plane strings Supported Not Supported

with generator instances Disallowed Disallowed

with generic iterables Supported Not Supported

with instances of generic iterables Supported Not Supported

iterator closing Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 148

Destructuring, declarations (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

trailing commas in iterable patterns Supported Not Supported

with objects Supported Not Supported

object destructuring with primitives Supported Not Supported

trailing commas in object patterns Supported Not Supported

throws on null and undefined Supported Not Supported

computed properties Supported Not Supported

multiples in a single var statement Supported Not Supported

nested Supported Not Supported

in for-in loop heads Supported Not Supported

in for-of loop heads Supported Not Supported

in catch heads Supported Not Supported

rest Supported Not Supported

defaults Supported Not Supported

defaults, let temporal dead zone Disallowed Disallowed

Destructuring, assignment

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

with arrays Supported Not Supported

with sparse arrays Supported Not Supported

with strings Supported Not Supported

with astral plane strings Supported Not Supported

with generator instances Disallowed Disallowed

with generic iterables Supported Not Supported

with instances of generic iterables Supported Not Supported

iterator closing Supported Not Supported

iterable destructuring expression Supported Not Supported

chained iterable destructuring Supported Not Supported

trailing commas in iterable patterns Supported Not Supported

with objects Supported Not Supported

object destructuring with primitives Supported Not Supported

trailing commas in object patterns Supported Not Supported

object destructuring expression Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 149

Destructuring, assignment (continued)

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

parenthesized left-hand-side is a syntax error

Disallowed Disallowed

chained object destructuring Supported Not Supported

throws on null and undefined Supported Not Supported

computed properties Supported Not Supported

nested Supported Not Supported

rest Supported Not Supported

nested rest Supported Not Supported

empty patterns Supported Not Supported

defaults Supported Not Supported

Destructuring, parameters

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

with arrays Supported Not Supported

with sparse arrays Supported Not Supported

with strings Supported Not Supported

with astral plane strings Supported Not Supported

with generator instances Disallowed Disallowed

with generic iterables Supported Not Supported

with instances of generic iterables Supported Not Supported

iterator closing Supported Not Supported

trailing commas in iterable patterns Supported Not Supported

with objects Supported Not Supported

object destructuring with primitives Supported Not Supported

trailing commas in object patterns Supported Not Supported

throws on null and undefined Supported Not Supported

computed properties Supported Not Supported

nested Supported Not Supported

'arguments' interaction Supported Not Supported

new Function() support Disallowed Disallowed

in parameters, function 'length' property Supported Not Supported

rest Supported Not Supported

empty patterns Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 150

Destructuring, parameters (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

defaults Supported Not Supported

defaults, separate scope Supported Not Supported

defaults, new Function() support Disallowed Disallowed

aliased defaults, arrow function Supported Not Supported

shorthand defaults, arrow function Supported Not Supported

duplicate identifier Disallowed Disallowed

Unicode code point escapes

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

in strings Supported Not Supported

in identifiers Not Supported Not Supported

in property key definitions Not Supported Not Supported

in property key accesses Not Supported Not Supported

New.target

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

in constructors Not Supported Not Supported

assignment is an early error Disallowed Disallowed

Const

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic support Supported Supported

is block-scoped Supported Not Supported

scope shadow resolution Supported Not Supported

cannot be in statements Disallowed Disallowed

redefining a const is an error Disallowed Disallowed

for loop statement scope Supported Not Supported

for-in loop iteration scope Supported Not Supported

for-of loop iteration scope Supported Not Supported

temporal dead zone Not Supported Not Supported

basic support (strict mode) Supported Supported

is block-scoped (strict mode) Supported Not Supported

scope shadow resolution (strict mode) Supported Not Supported

cannot be in statements (strict mode) Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 151

Const (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

redefining a const (strict mode) Disallowed Disallowed

for loop statement scope (strict mode) Supported Not Supported

for-in loop iteration scope (strict mode) Supported Not Supported

for-of loop iteration scope (strict mode) Supported Not Supported

temporal dead zone (strict mode) Not Supported Not Supported

Let

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

basic support Supported Not Supported

is block-scoped Supported Not Supported

scope shadow resolution Supported Not Supported

cannot be in statements Disallowed Disallowed

for loop statement scope Supported Not Supported

temporal dead zone Not Supported Not Supported

for/for-in loop iteration scope Supported Not Supported

for-in loop binding shadowing parameter Disallowed Disallowed

basic support (strict mode) Supported Not Supported

is block-scoped (strict mode) Supported Not Supported

scope shadow resolution (strict mode) Supported Not Supported

cannot be in statements (strict mode) Disallowed Disallowed

for loop statement scope (strict mode) Supported Not Supported

temporal dead zone (strict mode) Not Supported Not Supported

for/for-in loop iteration scope (strict mode) Supported Not Supported

for-in loop binding shadowing parameter (strict mode)

Disallowed Disallowed

Block-level function declaration

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

block-level function declaration Supported Not Supported

Arrow functions

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

0 parameters Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 152

Arrow functions (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

1 parameter, no brackets Supported Not Supported

multiple parameters Supported Not Supported

lexical "this" binding Supported Not Supported

"this" unchanged by call or apply Supported Not Supported

can't be bound, can be curried Supported Not Supported

lexical "arguments" binding Supported Not Supported

no line break between parameters and => Disallowed Disallowed

correct precedence Disallowed Disallowed

no "prototype" property Not Supported Not Supported

lexical "super" binding in constructors Supported Not Supported

lexical "super" binding in methods Supported Not Supported

lexical "new.target" binding Not Supported Not Supported

Class

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

class statement Supported Not Supported

is block-scoped Supported Not Supported

class expression Supported Not Supported

anonymous class Supported Not Supported

constructor Supported Not Supported

prototype methods Supported Not Supported

string-keyed methods Supported Not Supported

computed prototype methods Supported Not Supported

optional semicolons Supported Not Supported

static methods Supported Not Supported

computed static methods Supported Not Supported

accessor properties Supported Not Supported

computed accessor properties Supported Not Supported

static accessor properties Supported Not Supported

computed static accessor properties Supported Not Supported

class name is lexically scoped Supported Not Supported

computed names, temporal dead zone Not Supported Not Supported

methods aren't enumerable Supported Not Supported

implicit strict mode Not Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 153

Class (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

constructor requires new Supported Not Supported

extends Supported Not Supported

extends expressions Supported Not Supported

extends null Supported Not Supported

new.target Supported Not Supported

Super

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

statement in constructors Supported Not Supported

expression in constructors Supported Not Supported

in methods, property access Supported Not Supported

in methods, method calls Supported Not Supported

method calls use correct "this" binding Supported Not Supported

constructor calls use correct "new.target" binding

Supported Not Supported

is statically bound Supported Not Supported

super() invokes the correct constructor Supported Not Supported

Generators

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Disallowed

generator function expressions Supported Disallowed

correct "this" binding Supported Disallowed

can't use "this" with new Supported Disallowed

sending Supported Disallowed

%GeneratorPrototype% Disallowed Disallowed

%GeneratorPrototype% prototype chain Disallowed Disallowed

%GeneratorPrototype%.constructor Disallowed Disallowed

%GeneratorPrototype%.throw Disallowed Disallowed

%GeneratorPrototype%.return Disallowed Disallowed

yield operator precedence Disallowed Disallowed

yield \*, arrays Supported Disallowed

yield \*, sparse arrays Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 154

Generators (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

yield \*, strings Supported Disallowed

yield \*, astral plane strings Supported Disallowed

yield \*, generator instances Supported Disallowed

yield \*, generic iterables Supported Disallowed

yield \*, instances of iterables Supported Disallowed

yield \* on non-iterables is a runtime error Supported Disallowed

yield \*, iterator closing Supported Disallowed

yield \*, iterator closing via throw() Supported Disallowed

shorthand generator methods Supported Disallowed

string-keyed shorthand generator methods Supported Disallowed

computed shorthand generators Supported Disallowed

shorthand generator methods, classes Supported Disallowed

computed shorthand generators, classes Supported Disallowed

shorthand generators can't be constructors Disallowed Disallowed

Typed arrays

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Int8Array Supported Disallowed

Uint8Array Supported Disallowed

Uint8ClampedArray Supported Disallowed

Int16Array Supported Disallowed

Uint16Array Supported Disallowed

Int32Array Supported Disallowed

Uint32Array Supported Disallowed

Float32Array Supported Disallowed

Float64Array Supported Disallowed

DataView (Int8) Supported Disallowed

DataView (Uint8) Supported Disallowed

DataView (Int16) Supported Disallowed

DataView (Uint16) Supported Disallowed

DataView (Int32) Supported Disallowed

DataView (Uint32) Supported Disallowed

DataView (Float32) Supported Disallowed

DataView (Float64) Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 155

Typed arrays (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

ArrayBuffer[Symbol.species] Supported Disallowed

constructors require new Supported Disallowed

constructors accept generic iterables Supported Disallowed

correct prototype chains Disallowed Disallowed

%TypedArray%.from Supported Disallowed

%TypedArray%.of Supported Disallowed

%TypedArray%.prototype.subarray Supported Disallowed

%TypedArray%.prototype.join Supported Disallowed

%TypedArray%.prototype.indexOf Supported Disallowed

%TypedArray%.prototype.lastIndexOf Supported Disallowed

%TypedArray%.prototype.slice Supported Disallowed

%TypedArray%.prototype.every Supported Disallowed

%TypedArray%.prototype.filter Supported Disallowed

%TypedArray%.prototype.forEach Supported Disallowed

%TypedArray%.prototype.map Supported Disallowed

%TypedArray%.prototype.reduce Supported Disallowed

%TypedArray%.prototype.reduceRight Supported Disallowed

%TypedArray%.prototype.reverse Supported Disallowed

%TypedArray%.prototype.some Supported Disallowed

%TypedArray%.prototype.sort Supported Disallowed

%TypedArray%.prototype.copyWithin Supported Disallowed

%TypedArray%.prototype.find Supported Disallowed

%TypedArray%.prototype.findIndex Supported Disallowed

%TypedArray%.prototype.fill Supported Disallowed

%TypedArray%.prototype.keys Supported Disallowed

%TypedArray%.prototype.values Supported Disallowed

%TypedArray%.prototype.entries Supported Disallowed

%TypedArray%.prototype[Symbol.iterator] Supported Disallowed

%TypedArray%[Symbol.species] Disallowed Disallowed

Map

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

constructor arguments Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 156

Map (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

constructor requires new Supported Not Supported

constructor accepts null Supported Not Supported

constructor invokes set Supported Not Supported

iterator closing Supported Not Supported

Map.prototype.set returns this Supported Not Supported

-0 key converts to +0 Supported Not Supported

Map.prototype.size Supported Not Supported

Map.prototype.delete Supported Not Supported

Map.prototype.clear Supported Not Supported

Map.prototype.forEach Supported Not Supported

Map.prototype.keys Supported Not Supported

Map.prototype.values Supported Not Supported

Map.prototype.entries Supported Not Supported

Map.prototype[Symbol.iterator] Supported Not Supported

Map.prototype isn't an instance Supported Not Supported

Map iterator prototype chain Supported Not Supported

Map[Symbol.species] Supported Not Supported

Set

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

constructor arguments Supported Not Supported

constructor requires new Supported Not Supported

constructor accepts null Supported Not Supported

constructor invokes add Supported Not Supported

iterator closing Supported Not Supported

Set.prototype.add returns this Supported Not Supported

-0 key converts to +0 Supported Not Supported

Set.prototype.size Supported Not Supported

Set.prototype.delete Supported Not Supported

Set.prototype.clear Supported Not Supported

Set.prototype.forEach Supported Not Supported

Set.prototype.keys Supported Not Supported

Set.prototype.values Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 157

Set (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Set.prototype.entries Supported Not Supported

Set.prototype[Symbol.iterator] Supported Not Supported

Set.prototype isn't an instance Supported Not Supported

Set iterator prototype chain Supported Not Supported

Set[Symbol.species] Supported Not Supported

WeakMap

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

basic functionality Supported Disallowed

constructor arguments Supported Disallowed

constructor requires new Supported Disallowed

constructor accepts null Supported Disallowed

constructor invokes set Supported Disallowed

frozen objects as keys Supported Disallowed

iterator closing Supported Disallowed

WeakMap.prototype.set returns this Supported Disallowed

WeakMap.prototype.delete Supported Disallowed

no WeakMap.prototype.clear method Supported Disallowed

.has, .get and .delete methods accept primitives

Disallowed Disallowed

WeakMap.prototype isn't an instance Disallowed Disallowed

WeakSet

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Disallowed

constructor arguments Supported Disallowed

constructor requires new Supported Disallowed

constructor accepts null Supported Disallowed

constructor invokes add Supported Disallowed

iterator closing Supported Disallowed

WeakSet.prototype.add returns this Supported Disallowed

WeakSet.prototype.delete Supported Disallowed

no WeakSet.prototype.clear method Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 158

WeakSet (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

.has and .delete methods accept primitives Disallowed Disallowed

WeakSet.prototype isn't an instance Disallowed Disallowed

Proxy

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

constructor requires new Supported Disallowed

no "prototype" property Supported Disallowed

"get" handler Supported Disallowed

"get" handler, instances of proxies Supported Disallowed

"get" handler invariants Supported Disallowed

"set" handler Supported Disallowed

"set" handler, instances of proxies Supported Disallowed

"set" handler invariants Supported Disallowed

"has" handler Supported Disallowed

"has" handler, instances of proxies Supported Disallowed

"has" handler invariants Supported Disallowed

"deleteProperty" handler Supported Disallowed

"deleteProperty" handler invariant Supported Disallowed

"getOwnPropertyDescriptor" handler Supported Disallowed

"getOwnPropertyDescriptor" handler invariants

Supported Disallowed

"defineProperty" handler Supported Disallowed

"defineProperty" handler invariants Supported Disallowed

"getPrototypeOf" handler Supported Disallowed

"getPrototypeOf" handler invariant Supported Disallowed

"setPrototypeOf" handler Supported Disallowed

"setPrototypeOf" handler invariant Supported Disallowed

"isExtensible" handler Supported Disallowed

"isExtensible" handler invariant Supported Disallowed

"preventExtensions" handler Supported Disallowed

"preventExtensions" handler invariant Supported Disallowed

"ownKeys" handler Supported Disallowed

"ownKeys" handler invariant Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 159

Proxy (continued)

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

"apply" handler Supported Disallowed

"apply" handler invariant Supported Disallowed

"construct" handler Supported Disallowed

"construct" handler invariants Supported Disallowed

Proxy.revocable Supported Disallowed

Array.isArray support Supported Disallowed

JSON.stringify support Supported Disallowed

Reflect

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Reflect.get Disallowed Disallowed

Reflect.set Disallowed Disallowed

Reflect.has Disallowed Disallowed

Reflect.deleteProperty Disallowed Disallowed

Reflect.getOwnPropertyDescriptor Disallowed Disallowed

Reflect.defineProperty Disallowed Disallowed

Reflect.getPrototypeOf Disallowed Disallowed

Reflect.setPrototypeOf Disallowed Disallowed

Reflect.isExtensible Disallowed Disallowed

Reflect.preventExtensions Disallowed Disallowed

Reflect.ownKeys, string keys Disallowed Disallowed

Reflect.ownKeys, symbol keys Disallowed Disallowed

Reflect.apply Disallowed Disallowed

Reflect.construct Disallowed Disallowed

Reflect.construct sets new.target meta-property Disallowed Disallowed

Reflect.construct creates instances from third argument

Disallowed Disallowed

Reflect.construct, Array subclassing Disallowed Disallowed

Reflect.construct, RegExp subclassing Disallowed Disallowed

Reflect.construct, Function subclassing Disallowed Disallowed

Reflect.construct, Promise subclassing Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 160

Promise

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Disallowed

constructor requires new Supported Disallowed

Promise.prototype isn't an instance Supported Disallowed

Promise.all Supported Disallowed

Promise.all, generic iterables Supported Disallowed

Promise.race Supported Disallowed

Promise.race, generic iterables Supported Disallowed

Promise[Symbol.species] Supported Disallowed

Symbol

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Not Supported

typeof support Supported Not Supported

symbol keys are hidden to pre-ES6 code Supported Not Supported

Object.defineProperty support Supported Not Supported

symbols inherit from Symbol.prototype Supported Not Supported

cannot coerce to string or number Supported Not Supported

can convert with String() Supported Not Supported

new Symbol() throws Supported Not Supported

Object(symbol) Not Supported Not Supported

JSON.stringify ignores symbol primitives Supported Not Supported

JSON.stringify ignores symbol objects Not Supported Not Supported

global symbol registry Supported Not Supported

Well-known symbols

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Symbol.hasInstance Supported Disallowed

Symbol.isConcatSpreadable Supported Disallowed

Symbol.iterator, existence Supported Disallowed

Symbol.iterator, arguments object Supported Disallowed

Symbol.species, existence Supported Disallowed

Symbol.species, Array.prototype.concat Disallowed Disallowed

Symbol.species, Array.prototype.filter Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 161

Well-known symbols (continued)

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Symbol.species, Array.prototype.map Disallowed Disallowed

Symbol.species, Array.prototype.slice Disallowed Disallowed

Symbol.species, Array.prototype.splice Disallowed Disallowed

Symbol.species, RegExp.prototype[Symbol.split]

Disallowed Disallowed

Symbol.species, Promise.prototype.then Disallowed Disallowed

Symbol.replace Supported Disallowed

Symbol.search Supported Disallowed

Symbol.split Supported Disallowed

Symbol.match Supported Disallowed

Symbol.match, RegExp constructor Disallowed Disallowed

Symbol.match, String.prototype.startsWith Disallowed Disallowed

Symbol.match, String.prototype.endsWith Disallowed Disallowed

Symbol.match, String.prototype.includes Disallowed Disallowed

Symbol.toPrimitive Supported Disallowed

Symbol.toStringTag Supported Disallowed

Symbol.toStringTag affects existing built-ins Supported Disallowed

Symbol.toStringTag, new built-ins Supported Disallowed

Symbol.toStringTag, misc. built-ins Supported Disallowed

Symbol.unscopables Supported Disallowed

Object static methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Object.assign Supported Not Supported

Object.is Supported Not Supported

Object.getOwnPropertySymbols Supported Not Supported

Object.setPrototypeOf Supported Not Supported

Function "name" property

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

function statements Supported Supported

function expressions Supported Supported

new Function Not Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 162

Function "name" property (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

bound functions Not Supported Not Supported

variables (function) Supported Not Supported

object methods (function) Supported Not Supported

accessor properties Not Supported Not Supported

shorthand methods Supported Not Supported

shorthand methods (no lexical binding) Supported Not Supported

symbol-keyed methods Not Supported Not Supported

class statements Supported Not Supported

class expressions Supported Not Supported

variables (class) Supported Not Supported

object methods (class) Not Supported Not Supported

class prototype methods Supported Not Supported

class static methods Supported Not Supported

isn't writable, is configurable Supported Not Supported

String static methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

String.raw Supported Not Supported

String.fromCodePoint Supported Not Supported

String.prototype methods

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

String.prototype.codePointAt Supported Supported

String.prototype.normalize Supported Supported

String.prototype.repeat Supported Supported

String.prototype.startsWith Supported Supported

String.prototype.startsWith throws on RegExp

Not Supported Not Supported

String.prototype.endsWith Supported Supported

String.prototype.endsWith throws on RegExp Not Supported Not Supported

String.prototype.includes Supported Supported

String.prototype[Symbol.iterator] Supported Not Supported

String iterator prototype chain Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 163

RegExp.prototype properties

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

RegExp.prototype.flags Supported Not Supported

RegExp.prototype[Symbol.match] Supported Not Supported

RegExp.prototype[Symbol.replace] Supported Not Supported

RegExp.prototype[Symbol.split] Supported Not Supported

RegExp.prototype[Symbol.search] Supported Not Supported

RegExp[Symbol.species] Supported Not Supported

Array static methods

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Array.from, array-like objects Supported Not Supported

Array.from, generator instances Supported Disallowed

Array.from, generic iterables Supported Not Supported

Array.from, instances of generic iterables Supported Not Supported

Array.from map function, array-like objects Supported Not Supported

Array.from map function, generator instances Supported Disallowed

Array.from map function, generic iterables Supported Not Supported

Array.from map function, instances of iterables

Supported Not Supported

Array.from, iterator closing Supported Not Supported

Array.of Supported Not Supported

Array[Symbol.species] Supported Not Supported

Array.prototype methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype.copyWithin Supported Not Supported

Array.prototype.find Supported Not Supported

Array.prototype.findIndex Supported Not Supported

Array.prototype.fill Supported Not Supported

Array.prototype.keys Supported Not Supported

Array.prototype.values Supported Not Supported

Array.prototype.entries Supported Not Supported

Array.prototype[Symbol.iterator] Supported Not Supported

Array iterator prototype chain Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 164

Array.prototype methods (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype[Symbol.unscopables] Supported Not Supported

Number properties

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Number.isFinite Supported Not Supported

Number.isInteger Supported Not Supported

Number.isSafeInteger Supported Not Supported

Number.isNaN Supported Not Supported

Number.parseFloat Supported Disallowed

Number.parseInt Supported Disallowed

Number.EPSILON Supported Not Supported

Number.MIN_SAFE_INTEGER Supported Not Supported

Number.MAX_SAFE_INTEGER Supported Not Supported

Math methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Math.clz32 Supported Not Supported

Math.imul Supported Not Supported

Math.sign Supported Not Supported

Math.log10 Supported Not Supported

Math.log2 Supported Not Supported

Math.log1p Supported Not Supported

Math.expm1 Supported Not Supported

Math.cosh Supported Not Supported

Math.sinh Supported Not Supported

Math.tanh Supported Not Supported

Math.acosh Supported Not Supported

Math.asinh Supported Not Supported

Math.atanh Supported Not Supported

Math.trunc Supported Not Supported

Math.fround Supported Not Supported

Math.cbrt Supported Not Supported

Math.hypot Supported Not Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 165

Date.prototype[Symbol.toPrimitive]

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Date.prototype[Symbol.toPrimitive] Supported Not Supported

Array is subclassable

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

length property (accessing) Disallowed Disallowed

length property (setting) Disallowed Disallowed

correct prototype chain Disallowed Disallowed

Array.isArray support Supported Disallowed

Array.prototype.concat Supported Disallowed

Array.prototype.filter Supported Disallowed

Array.prototype.map Supported Disallowed

Array.prototype.slice Supported Disallowed

Array.prototype.splice Supported Disallowed

Array.from Supported Disallowed

Array.of Supported Disallowed

RegExp is subclassable

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Disallowed Disallowed

correct prototype chain Disallowed Disallowed

RegExp.prototype.exec Disallowed Disallowed

RegExp.prototype.test Disallowed Disallowed

Function is subclassable

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

can be called Disallowed Disallowed

correct prototype chain Disallowed Disallowed

can be used with "new" Disallowed Disallowed

Function.prototype.call Disallowed Disallowed

Function.prototype.apply Disallowed Disallowed

Function.prototype.bind Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 166

Promise is subclassable

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Disallowed Disallowed

correct prototype chain Disallowed Disallowed

Promise.all Disallowed Disallowed

Promise.race Disallowed Disallowed

Miscellaneous subclassables

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Boolean is subclassable Disallowed Disallowed

Number is subclassable Disallowed Disallowed

String is subclassable Disallowed Disallowed

Error is subclassable Disallowed Disallowed

Map is subclassable Disallowed Disallowed

Set is subclassable Disallowed Disallowed

Prototype of bound functions

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functions Disallowed Disallowed

generator functions Disallowed Disallowed

arrow functions Disallowed Disallowed

classes Disallowed Disallowed

subclasses Disallowed Disallowed

Proxy, internal 'get' calls

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

ToPrimitive Supported Disallowed

CreateListFromArrayLike Supported Disallowed

instanceof operator Supported Disallowed

HasBinding Supported Disallowed

CreateDynamicFunction Supported Disallowed

ClassDefinitionEvaluation Supported Disallowed

IteratorComplete, IteratorValue Supported Disallowed

ToPropertyDescriptor Supported Disallowed

Object.assign Supported Disallowed

Object.defineProperties Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 167

Proxy, internal 'get' calls (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Function.prototype.bind Supported Disallowed

Error.prototype.toString Supported Disallowed

String.raw Supported Disallowed

RegExp constructor Supported Disallowed

RegExp.prototype.flags Supported Disallowed

RegExp.prototype.test Supported Disallowed

RegExp.prototype.toString Supported Disallowed

RegExp.prototype[Symbol.match] Supported Disallowed

RegExp.prototype[Symbol.replace] Supported Disallowed

RegExp.prototype[Symbol.search] Supported Disallowed

RegExp.prototype[Symbol.split] Supported Disallowed

Array.from Supported Disallowed

Array.prototype.concat Supported Disallowed

Array.prototype iteration methods Supported Disallowed

Array.prototype.pop Supported Disallowed

Array.prototype.reverse Supported Disallowed

Array.prototype.shift Supported Disallowed

Array.prototype.splice Supported Disallowed

Array.prototype.toString Supported Disallowed

JSON.stringify Supported Disallowed

Promise resolve functions Supported Disallowed

String.prototype.match Supported Disallowed

String.prototype.replace Supported Disallowed

String.prototype.search Supported Disallowed

String.prototype.split Supported Disallowed

Date.prototype.toJSON Supported Disallowed

Proxy, internal 'set' calls

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Object.assign Supported Disallowed

Array.from Supported Disallowed

Array.of Supported Disallowed

Array.prototype.copyWithin Supported Disallowed

Array.prototype.fill Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 168

Proxy, internal 'set' calls (continued)

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype.pop Supported Disallowed

Array.prototype.push Supported Disallowed

Array.prototype.reverse Supported Disallowed

Array.prototype.shift Supported Disallowed

Array.prototype.splice Supported Disallowed

Array.prototype.unshift Supported Disallowed

Proxy, internal 'defineProperty' calls

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

[[Set]] Supported Disallowed

SetIntegrityLevel Supported Disallowed

Proxy, internal 'deleteProperty' calls

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Array.prototype.copyWithin Supported Disallowed

Array.prototype.pop Supported Disallowed

Array.prototype.reverse Supported Disallowed

Array.prototype.shift Supported Disallowed

Array.prototype.splice Supported Disallowed

Array.prototype.unshift Supported Disallowed

Proxy, internal 'getOwnPropertyDescriptor' calls

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

[[Set]] Supported Disallowed

Object.assign Supported Disallowed

Object.prototype.hasOwnProperty Supported Disallowed

Function.prototype.bind Supported Disallowed

Proxy, internal 'ownKeys' calls

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

SetIntegrityLevel Supported Disallowed

TestIntegrityLevel Supported Disallowed

SerializeJSONObject Supported Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 169

Object static methods accept primitives

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Object.getPrototypeOf Disallowed Disallowed

Object.getOwnPropertyDescriptor Disallowed Disallowed

Object.getOwnPropertyNames Disallowed Disallowed

Object.seal Disallowed Disallowed

Object.freeze Disallowed Disallowed

Object.preventExtensions Disallowed Disallowed

Object.isSealed Disallowed Disallowed

Object.isFrozen Disallowed Disallowed

Object.isExtensible Disallowed Disallowed

Object.keys Disallowed Disallowed

Own property order

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Object.keys Supported Disallowed

Object.getOwnPropertyNames Supported Disallowed

Object.assign Disallowed Disallowed

JSON.stringify Disallowed Disallowed

JSON.parse Disallowed Disallowed

Reflect.ownKeys, string key order Disallowed Disallowed

Reflect.ownKeys, symbol key order Disallowed Disallowed

Updated identifier syntax

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

var â¸¯; Disallowed Disallowed

var ð ‹€; Disallowed Disallowed

no escaped reserved words as identifiers Disallowed Disallowed

Non-strict function semantics

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

hoisted block-level function declaration Supported Disallowed

labeled function statements Disallowed Disallowed

function statements in if-statement clauses Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 170

**proto** in object literals

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic support Supported Disallowed

multiple **proto** is an error Disallowed Disallowed

not a computed property Disallowed Disallowed

not a shorthand property Disallowed Disallowed

not a shorthand method Disallowed Disallowed

Object.prototype.**proto**

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

get prototype Disallowed Disallowed

set prototype Disallowed Disallowed

absent from Object.create(null) Disallowed Disallowed

present in hasOwnProperty() Disallowed Disallowed

correct property descriptor Disallowed Disallowed

present in Object.getOwnPropertyNames() Disallowed Disallowed

String.prototype HTML methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

existence Supported Disallowed

tags' names are lowercase Supported Disallowed

quotes in arguments are escaped Supported Disallowed

RegExp.prototype.compile

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

basic functionality Supported Disallowed

returns this Supported Disallowed

RegExp syntax extensions

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

hyphens in character sets Disallowed Disallowed

invalid character escapes Disallowed Disallowed

invalid control-character escapes Disallowed Disallowed

invalid Unicode escapes Disallowed Disallowed

invalid hexadecimal escapes Disallowed Disallowed

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 171

RegExp syntax extensions (continued)

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

incomplete patterns and quantifiers Disallowed Disallowed

octal escape sequences Disallowed Disallowed

invalid backreferences become octal escapes

Disallowed Disallowed

##### ECMAScript 2009 (ES5) features

Object/array literal extensions

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Getter accessors Supported Supported

Setter accessors Supported Supported

Trailing commas in object literals Supported Supported

Trailing commas in array literals Supported Supported

Reserved words as property names Supported Supported

Object static methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Object.create Supported Supported

Object.defineProperty Supported Supported

Object.defineProperties Supported Supported

Object.getPrototypeOf Supported Supported

Object.keys Supported Supported

Object.seal Supported Supported

Object.freeze Supported Supported

Object.preventExtensions Supported Supported

Object.isSealed Supported Supported

Object.isFrozen Supported Supported

Object.isExtensible Supported Supported

Object.getOwnPropertyDescriptor Supported Supported

Object.getOwnPropertyNames Supported Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 172

Array methods

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Array.isArray Supported Supported

Array.prototype.indexOf Supported Supported

Array.prototype.lastIndexOf Supported Supported

Array.prototype.every Supported Supported

Array.prototype.some Supported Supported

Array.prototype.forEach Supported Supported

Array.prototype.map Supported Supported

Array.prototype.filter Supported Supported

Array.prototype.reduce Supported Supported

Array.prototype.reduceRight Supported Supported

Array.prototype.sort: compareFn must be function or undefined

Supported Not Supported

Array.prototype.sort: compareFn may be explicit undefined

Supported Supported

String properties and methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Property access on strings Supported Supported

String.prototype.split Supported Not Supported

String.prototype.trim Supported Supported

Date methods

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Date.prototype.toISOString Supported Supported

Date.now Supported Supported

Date.prototype.toJSON Supported Not Supported

Immutable globals

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

undefined Supported Supported

NaN Supported Supported

Infinity Supported Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 173

Number methods

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

Number.prototype.toExponential rounds properly Supported Supported

Number.prototype.toExponential throws on Â±Infinity fractionDigits

Supported Supported

Number.prototype.toExponential does not throw on edge cases

Supported Supported

Strict mode

Feature

ECMAScript 2021 (ES12) mode

ES5 Standards mode

reserved words Disallowed Disallowed

"this" is undefined in functions Disallowed Disallowed

"this" is not coerced to object in primitive methods Disallowed Disallowed

"this" is not coerced to object in primitive accessors Disallowed Disallowed

legacy octal is a SyntaxError Supported Disallowed

assignment to unresolvable identifiers is a ReferenceError

Supported Disallowed

assignment to eval or arguments is a SyntaxError Supported Disallowed

assignment to non-writable properties is a TypeError Supported Disallowed

eval or arguments bindings is a SyntaxError Disallowed Disallowed

arguments.caller removed or is a TypeError Supported Disallowed

arguments.callee is a TypeError Supported Disallowed

(function(){}).caller and (function(){}).arguments is a TypeError

Supported Disallowed

arguments is unmapped Disallowed Disallowed

eval() can't create bindings Disallowed Disallowed

deleting bindings is a SyntaxError Disallowed Disallowed

deleting non-configurable properties is a TypeError Disallowed Disallowed

"with" is a SyntaxError Supported Disallowed

repeated parameter names is a SyntaxError Supported Disallowed

function expressions with matching name and argument are valid

Disallowed Disallowed

Function.prototype.bind

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

Function.prototype.bind Supported Supported

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 174

JSON

Feature ECMAScript 2021 (ES12) mode ES5 Standards mode

JSON Supported Supported

JavaScript API Context-sensitive help

The syntax editor can display context-sensitive API information.

JavaScript API Context-sensitive help includes the ability to:

**-** List script elements that are valid at the cursor's location. The system displays suggestions in a pop-up window.

**-** Add a selected script element at the cursor's location. If the cursor is within or adjacent to a partial entry, the system completes the entry with the selected script element.

**-** View API documentation for a selected suggestion.

**-** View the expected parameters and format of the current script element.

If the cursor is adjacent to a text string, the system searches for script elements that start with this text string. For example, while the cursor is within or adjacent to the string GlideR, the system displays script elements such as:

**-** GlideRecord

**-** GlideRecordSecure

Context-sensitive suggestions are based on script type. For example, when working on a

###### business rule, only suggestions from the server API and for objects such as current and

###### previous display. When working on a client script, the system only displays suggestions from

the client API.

##### Client-side scripting

Run JavaScript on the client (web browser) when client-based events occur, such as when a form loads, after form submission, or when a field changes value.

The client-side Glide API provides classes and methods that you can use in client scripts.

##### Before you begin

Understand the limitations of your scripting environment. For example, client scripts run on forms in the Service Portal or Mobile environments can only include certain APIs. For more information, see Mobile client GlideForm (g form) scripting and migration.

Client-side scripting design and processing

Well-designed client scripts can reduce the amount of time it takes users to complete a form.

Proper client-side processing depends on the form loading first. Making record updates prior to form load can produce unexpected results that bypass client-side processing.

If you create client scripts to control field values on a form, you must use another method to control these field values in a list. You can:

**-** Disable list editing for the table.

**-** Create appropriate business rules or access controls for list editing.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 175

**-** Create data policies.

**-** Create a separate onCellEdit client script.

Restrict list editing

If you create UI policies or client scripts for fields on a form, you must use another method to ensure that data in those fields is similarly controlled in a list.

With the exception of onCellEdit client scripts, UI policies and client scripts apply to forms only. Use the following methods to restrict list editing when using client scripts:

**-** Disable list editing for the table.

**-** Create appropriate business rules or access controls for list editing.

**-** Create data policies.

**-** Create a separate onCellEdit client script.

Minimize server lookups

Use client data as much as possible to eliminate the need for time-consuming server lookups.

Client scripting uses either data available on the client or data retrieved from the server. The top ways to get information from the server are g_scratchpad and asynchronous GlideAjax lookup.

The primary difference between these methods is that g_scratchpad is sent once when a form is loaded (information is pushed from the server to the client), whereas GlideAjax is dynamically triggered when the client requests information from the server.

##### Note: GlideRecord and g_form.getReference() are also available for retrieving

server information. However, these methods are no longer recommended due to their performance impact. Both methods retrieve all fields in the requested GlideRecord when most cases only require one field.

##### Example: Retrieve server data using g_scratchpad

The g_scratchpad object passes information from the server to the client, such as when the client requires information not available on the form.

For example, if you have a client script that needs to access the field u_retrieve, and the field is not on the form, the data is not available to the client script. A typical solution to this situation is to place the field on the form and then always hide it with a client script or UI policy. While this solution may be faster to configure, it is slower to execute.

If you know what information the client needs from the server before the form is loaded, a display business rule can create g_scratchpad properties to hold this information. Theg_scratchpad is sent to the client when the form is requested, making it available to all client-side scripting methods. This is a very efficient means of sending information from the server to the client. However, you can only load data this way when the form is loaded. The business rule cannot be triggered dynamically. In those cases, use an asynchronous GlideAjax call.

For example, assume you open an incident and need to pass this information to the client:

**-** The value of the system property css.base.color

**-** Whether or not the current record has attachments

**-** The name of the caller's manager

A display business rule sends this information to the client using the following script:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 176

g_scratchpad.css = gs.getProperty('css.base.color'); g_scratchpad.hasAttachments = current.hasAttachments(); g_scratchpad.managerName = current.caller_id.manager.getDisplayValue();

To access scratchpad data using a client script:

// Check if the form has attachments if (g_scratchpad.hasAttachments) // do something interesting here else alert('You need to attach a form signed by ' + g_scratchpad.managerName);

##### Example: Retrieve server data using asynchronous GlideAjax

Asynchronous GlideAjax allows you to dynamically request information from the server.

This script compares the support group of the CI and the assignment group of the incident by name:

//Alert if the assignment groups name matches the support group function onChange(control, oldValue, newValue, isLoading) {

if (isLoading) return;

var ga = new GlideAjax('ciCheck');

ga.addParam('sysparm_name', 'getCiSupportGroup'); ga.addParam('sysparm_ci', g_form.getValue('cmdb_ci')); ga.addParam('sysparm_ag', g_form.getValue('assignment_group')); ga.getXML(doAlert); // Always try to use asynchronous (getXML) calls rather than synchronous (getXMLWait) }

// Callback function to process the response returned from the server function doAlert(response) {

var answer = response.responseXML.documentElement.getAttribute("answer");

alert(answer); }

This script relies on the accompanying script include:

var ciCheck = Class.create();

ciCheck.prototype = Object.extendsObject(AbstractAjaxProcessor, {

getCiSupportGroup: function() {

var retVal = ''; // Return value var ciID = this.getParameter('sysparm_ci');

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 177

var agID = this.getParameter('sysparm_ag'); var ciRec = new GlideRecord('cmdb_ci');

// If we can read the record, check if the sys_ids match if (ciRec.get(ciID)) { if (ciRec.getValue('support_group') == agID) retVal = 'CI support group and assignment group match'; else retVal = 'CI support group and assignment group do not match';

// Can't read the CI, then they don't match } else { retVal = 'CI support group and assignment group do not match'; }

return retVal; }

});

Use the setValue() displayValue parameter for reference fields

When using setValue() on a reference field, include the displayValue parameter to avoid additional server calls.

###### When using setValue() on a reference field, be sure to include the reference field display

value as the 3rd parameter. If you set the value without the displayValue, the instance does a synchronous call to retrieve the display value for the record you specified. This extra round trip to the server can impact performance.

This example demonstrates the incorrect way to call setValue:

var id = '5137153cc611227c000bbd1bd8cd2005';

g_form.setValue('assigned_to', id); // Client needs to go back to the server to // fetch the name that goes with this ID

###### Instead, include the display value as an optional parameter in setValue():

var id = '5137153cc611227c000bbd1bd8cd2005'; var name = 'Fred Luddy';

g_form.setValue('assigned_to', id, name); // No server call required

Use UI policy instead of a client script

When possible, consider using a UI policy instead of a client script.

UI policies provide these benefits over client scripts:

**-** UI policies have an **Order** field to allow full control over the order in which client-side operations take place.

**-** UI policies do not require scripting to make a field mandatory, read-only, or visible.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 178

##### Note: UI policies apply after client scripts.

Validating the input by using a client script

An excellent use for a client script is to validate the input from the user.

This validation improves the user experience because the user finds out if there are data issues before submitting the information.

An example of validation is to verify that the Impact field value is valid with the Priority field value. In this example, Low impact is not allowed with High priority.

if (g_form.getValue('impact') == '3' && g_form.getValue('priority') == '1') g_form.showFieldMsg('impact', getMessage('Low impact now allowed with High priority'), 'error');

Set client script order

Control the order of execution for your client scripts using the Order field. To avoid having two or more client scripts run concurrently and then conflict, you can add an order for the scripts to run in.

###### Before you begin

Role required: admin

###### About this task

Adding an order to the client script creates a processing sequence, ordered from lowest to highest number. If two scripts conflict, the client script with the lower number executes first.

###### Procedure

**1.** Navigate to **All** > **System Definition** > **Client Script** and open an existing client script or click **New**.

**2.** Configuring the form layout to include the **Order** field.

**3.** Add a number to the order field based on what order you want it to run in relation to other client scripts. Choose a lower number for the script you want to execute first.

Avoid DOM manipulation

Avoid Document Object Model (DOM) manipulation if possible. It can cause a maintainability issue when browsers are updated.

Instead, use the GlideForm API or consider a different approach for the solution. In general, when using DOM manipulation methods, you have to reference an element in the DOM by ID or using a CSS selector. When referencing out-of-box DOM elements, there is a risk that the element ID or placement within the DOM could change, causing the code to stop working and/ or generate errors. Use forethought, caution, and have a full understanding of the risk you are incurring. Review these objects and reduce the use of DOM manipulation methods as much as possible.

Avoid global client scripts

A global client script is any client script where the selected Table is Global. Global client scripts have no table restrictions, therefore they will load on every page in the system introducing browser load delay in the process.

There is no benefit to loading this kind of scripts on every page.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 179

As an alternative, and for a more modular and scalable approach, consider moving client scripts to a base table (such as Task[task] or Configuration Item[cmdb_ci]) that can be derived for all the child/extending tables. This eliminates the system loading the scripts on every form in the UI such as home pages or Service Catalog where they are rarely (if ever) needed.

Enclose code in functions

Enclose the code in a client script inside a function.

Client scripts without a function cause issues with variable scope. When code is not enclosed in a function, variables and other objects are available and shared to all other client-side scripts. If you are using the same variable names, it is possible that they could collide. This can lead to unexpected consequences that are difficult to troubleshoot.

Consider this example:

var state = "6";

function onSubmit() {

if(g_form.getValue('incident_state') == state) { alert("This incident is Resolved"); } }

###### Because the state variable is not enclosed in a function, all client-side scripts, have access

###### to it. Other scripts may also use the common variable name state. The duplicate names can

conflict and lead to unexpected results. These issues are difficult to isolate and resolve. To avoid this issue, ensure that all code is wrapped in a function:

function onSubmit() {

var state = "6";

if(g_form.getValue('incident_state') == state) { alert("This incident is Resolved"); } }

###### This solution is much safer because the scope of the variable state is limited to the onSubmit()

###### function. Therefore, the state variable does not conflict with state variables in other client

side scripts.

Run only necessary scripts

To avoid running time-consuming scripts unnecessarily, make sure that client scripts perform only necessary tasks.

The following examples demonstrate improvements to the initial code sample. Each example demonstrates a particular enhancement to the script to improve performance and avoid unnecessary calls.

Remember that client scripts have no Condition field. This means that onLoad() and onChange() scripts run in their entirety every time the appropriate form is loaded. This example is an inefficient onChange() client script set to run when the Configuration item field changes.

//Set Assignment Group to CI's support group if assignment group is empty function onChange(control, oldValue, newValue, isLoading) {

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 180

var ciSupportGroup = g_form.getReference('cmdb_ci').support_group;

if (ciSupportGroup != '' && g_form.getValue('assignment_group) != '') g_form.setValue('assignment_group', ciRec.support_group.sys_id); }

This example improves upon the first by replacing the getReference() or GlideRecord lookup with an asynchronous GlideAjax call.

//Set Assignment Group to support group if assignment group is empty function onChange(control, oldValue, newValue, isLoading) {

var ga = new GlideAjax('ciCheck');

ga.addParam('sysparm_name', 'getSupportGroup'); ga.addParam('sysparm_ci', g_form.getValue('cmdb_ci')); ga.getXML(setAssignmentGroup); }

function setAssignmentGroup(response) {

var answer = response.responseXML.documentElement.getAttribute("answer");

g_form.setValue('assignment_group', answer); }

###### The isLoading flag is the simplest way to prevent unnecessary code from taking up browser

###### time in onChange scripts. The isLoading flag should be used at the beginning of any script

that is not required to run when the form is loading. There is no need to run this script on a form load because the logic would have already run when the field was last changed. Adding the

###### isLoading check to the script prevents it from doing a cmdb_ci lookup on every form load.

###### The isTemplate flag indicates that a template is loading.

//Set Assignment Group to CI's support group if assignment group is empty function onChange(control, oldValue, newValue, isLoading, isTemplate) {

if (isLoading) return;

var ga = new GlideAjax('ciCheck');

ga.addParam('sysparm_name', 'getSupportGroup'); ga.addParam('sysparm_ci', g_form.getValue('cmdb_ci')); ga.getXML(setAssignmentGroup); }

function setAssignmentGroup(response) {

var answer = response.responseXML.documentElement.getAttribute("answer");

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 181

g_form.setValue('assignment_group', answer); }

If the onChange script should run during loading, use the following convention:

function onChange(control, oldValue, newValue, isLoading, isTemplate) {

if (isLoading) {}; // run during loading

// rest of script here

}

The newValue check tells this script to continue only if there is a valid value in the relevant field. This prevents the script from running when the field value is removed or blanked out. This also ensures that there will always be a valid value available when the rest of the script runs.

//Set Assignment Group to CI's support group if assignment group is empty function onChange(control, oldValue, newValue, isLoading, isTemplate) {

if (isLoading) return;

if (newValue) { var ga = new GlideAjax('ciCheck');

ga.addParam('sysparm_name', 'getSupportGroup'); ga.addParam('sysparm_ci', g_form.getValue('cmdb_ci')); ga.getXML(setAssignmentGroup); } }

function setAssignmentGroup(response) {

var answer = response.responseXML.documentElement.getAttribute("answer");

g_form.setValue('assignment_group', answer); }

To have the script react to a value that changes after the form loads, use the newValue != oldValue check.

##### Note: This example does not catch users changing a value and then changing it back to

its original value.

//Set Assignment Group to CI's support group if assignment group is empty function onChange(control, oldValue, newValue, isLoading, isTemplate) {

if (isLoading) return;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 182

if (newValue) { if (newValue != oldValue) { var ga = new GlideAjax('ciCheck');

ga.addParam('sysparm_name', 'getSupportGroup'); ga.addParam('sysparm_ci', g_form.getValue('cmdb_ci')); ga.getXML(setAssignmentGroup); } } }

function setAssignmentGroup(response) {

var answer = response.responseXML.documentElement.getAttribute("answer");

g_form.setValue('assignment_group', answer); }

In this example, the GlideAjax call is buried one level deeper by rearranging the script to check as many things available to the client as possible before running the server calls. The script checks the assignment before executing the GlideAjax call. This prevents the server lookup when the assignment_group field is already set.

//Set Assignment Group to CI's support group if assignment group is empty function onChange(control, oldValue, newValue, isLoading, isTemplate) {

if (isLoading) return;

if (newValue) { if (newValue != oldValue) { if (g_form.getValue('assignment_group') == '') { var ga = new GlideAjax('ciCheck');

ga.addParam('sysparm_name', 'getSupportGroup'); ga.addParam('sysparm_ci', g_form.getValue('cmdb_ci')); ga.getXML(setAssignmentGroup); } } } }

function setAssignmentGroup(response) {

var answer = response.responseXML.documentElement.getAttribute("answer");

g_form.setValue('assignment_group', answer); }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 183

Client scripts

Client scripts allow the system to run JavaScript on the client (web browser) when client-based events occur, such as when a form loads, after form submission, or when a field changes value.

Introduction to client scripts, script types, APIs, and good practices

Use client scripts to configure forms, form fields, and field values while the user is using the form. Client scripts can:

**-** make fields hidden or visible

**-** make fields read only or writable

**-** make fields optional or mandatory based on the user's role

**-** set the value in one field based on the value in other fields

**-** modify the options in a choice list based on a user's role

**-** display messages based on a value in a field

##### Warning:

Client scripts are intended to optimize the user experience on a form. Client scripts are not meant to protect unwanted access to data.

To prevent unwanted access to data, ensure that sensitive fields are hidden or read-only through ACLs or data policies.

For more information, see Access Control List Rules or Data policy.

##### Where client scripts run

###### With the exception of onCellEdit() client scripts, client scripts only apply to forms and

search pages. If you create a client script to control field values on a form, you must use one of these other methods to control field values when on a list.

**-** Create an access control to restrict who can edit field values.

**-** Create a business rule to validate content.

**-** Create a data policy to validate content.

**-** Create an onCellEdit() client script to validate content.

**-** Disable list editing for the table.

##### Note: Client scripts are not supported on ServiceNow mobile applications.

##### Client script form

Field Description

Name Name of the client script.

Table Table to which the client script applies.

UI Type Target user interface to which the client script applies.

Type

###### onLoad() — runs when the system first renders the form and before

###### users can enter data. Typically, onLoad() client scripts perform

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 184

Field Description

client-side-manipulation of the current form or set default record values.

###### onSubmit() — runs when a form is submitted. Typically,

###### onSubmit() scripts validate things on the form and ensure that the

###### submission makes sense. An onSubmit() client script can cancel

form submission by returning a value of false.

###### onChange() — runs when a particular field value changes on the

###### form. The onChange() client script must specify these parameters.

**-** control: the DHTML widget whose value changed.

##### Note: control is not accessible in mobile and service

portal.

**-** oldValue: the value the widget had when the record was loaded.

##### Note: Old values aren't returned for the HTML field type.

**-** newValue: the value the widget has after the change.

**-** isLoading: identifies whether the change occurs as part of a form load.

**-** isTemplate: identifies whether the change occurs as part of a template load.

###### onCellEdit() — runs when the list editor changes a cell value.

###### The onCellEdit() client script must specify these parameters.

**-** sysIDs: an array of the sys_ids for all items being edited.

**-** table: the table of the items being edited.

**-** oldValues: the old values of the cells being edited.

**-** newValue: the new value for the cells being edited.

**-** callback: a callback that continues the execution of any other related cell edit scripts. If _true_ is passed as a parameter, the other scripts are executed or the change is committed if there are no more scripts. If _false_ is passed as a parameter, any further scripts are not executed and the change is not committed.

Field Name Name of the field to which the script applies. Available only if the script responds to a field value change (onChange or onCellEdit script types).

Application Application where this client script resides.

Active Enables the client script when selected. Unselect this field to disable the client script.

Inherited Indicates whether the client script applies to extended tables.

Global If true, the client script runs on all views of the table.

View Only visible when Global is unselected. Views on which the client script will run.

Description Content describing the functionality and purpose of the client script.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 185

Field Description

Messages Text string (one per line) available to the client script as localized

###### messages using getmessage('[message]'). For additional

information, see Translate a client script message.

Script Contains the client script.

Isolate script New client scripts are run in strict mode, with direct DOM access disabled. Access to jQuery, prototype, and the window object are also disabled. To disable this on a per-script basis, configure this form and select the Isolate script check box. To disable this feature for all new globally-scoped client-side scripts set the system property glide.script.block.client.globals to false.

UI scripts

UI scripts provide a way to package client-side JavaScript into a reusable form, similar to how script includes store server-side JavaScript. Administrators can create UI scripts and run them from client scripts and other client-side script objects and from HTML code.

UI scripts are not supported for mobile.

Global UI scripts

You can create a UI script and designate it as global, which makes the script available on any form in the system. You cannot create a global UI script in a scoped application.

You can mark a UI script as Global to make it available on any form in the system. For example,

###### you can create a UI script that has a function helloWorld(), and has the Global field

checked:

function helloWorld() { alert('Hi'); }

###### After you create this global UI script, you can call the helloWorld() function from any client

script or UI policy you write.

Create a UI script

Create a UI script to define reusable client-side JavaScript code.

###### Procedure

To create UI scripts, navigate to System UI > UI Scripts and create or edit a record (see table for field descriptions).

UI scripts

Field Description

Script Name

Name of the UI script. Ensure the name is unique on your system.

API Name The API name of the UI script, including the scope and script name (for example, x_custom_app.HelloWorld).

Application Application that contains the UI script.

Active Indicator of whether the UI script is active. Only active UI scripts can run.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 186

Field Description

Global Indicator of whether the script loads on every page in the system.

##### Note: Use caution when creating global UI scripts because they can impact

performance. You cannot create a global UI script in a scoped application.

Description Summary of the purpose of the script.

Script Client-side script to run when called from other scripts.

Run UI scripts

Follow these guidelines when running UI scripts.

##### Run a UI script from a form

To run a UI script on a form, Create a formatter and add it to a form. In the associated UI macro,

###### include a g:requires tag and specify the name= parameter as the name of the UI script

followed by the .jsdbx extension. Add the formatter on the form view.

This code ensures that the definitions and results of the UI script are immediately available in the browser.

 <?xml version="1.0" encoding="utf-8" ?> <j:jelly trim="false" xmlns:j="jelly:core" xmlns:g="glide" xmlns:j2="null" xmlns:g2="null"> <g2:evaluate var="jvar_stamp"> var now_GR = new GlideRecord('sys_ui_script'); gr.orderByDesc('sys_updated_on'); gr.query(); gr.next(); gr.getValue('sys_updated_on'); </g2:evaluate> <g:requires name="<UI SCRIPT NAME>.jsdbx" params="cache=$[jvar_stamp]" /> </j:jelly>

##### Call a UI script in HTML

To run a UI script from HTML code, use the <script> tag and specify the src= argument as the API name of the UI script followed by the .jsdbx extension. For example, include the UI script named CoolClock with this code:

 <script language="javascript" src="CoolClock.jsdbx" /> 

##### Call a UI script from client-side code 

###### Access UI scripts from within client-side code using the g_ui_scripts global object. For more 

 information, see GlideUIScripts Client. 

##### Note: This class does not support UI scripts with the Global field set to true. 

 Catalog client scripts 

 Client-side scripts can add dynamic effects and validation to forms. Scripts can apply to service catalog items or variable sets, allowing administrators to use the same functionality that is available on other forms. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 187 


 You can use client side scripts to: 

**-** Get or set variable values. 

**-** Hide or display variables. 

**-** Make variables mandatory or not. 

**-** Validate form submission. 

**-** Add something to the cart. 

**-** Order something immediately. 

 Catalog client script considerations 

 When you create catalog client scripts, be aware of the following considerations. 

**-** Catalog client scripts run when a user orders an item from the service catalog. Catalog client     scripts can also run when variables or variable sets for a catalog item are displayed when a     user requests that item. 

**-** For a variable to be accessible using a catalog client script, it must have a variable name.     Variables without names do not appear in the list of available variables. 

**-** When using standard client scripts on a Requested Item or Catalog Task form, make a note     of fields with the same name as variables. If a table field and a variable of the same name are     both present on a form, the table field is matched when it is accessed using a script. If this     happens, specifically address the variable by naming it variables.variable name. For     example: g_form.setValue('variables.replacement', 'false'); 

**-** If you are using record producers to pass variables from the service catalog to other     types of records, these variables are made visible in those records with a variable editor,     such as the Change Variable Editor UI formatter on Change request forms. You can     manipulate these variables using standard client script methods, such as setDisplay,     setMandatory,setValue, and getValue. 

**-** Catalog client scripts can be used for catalog items included in a wizard. 

**-** You can use the g_form.refreshSlushbucket(fieldName) API to update a list     collector variable. 

 Catalog client script differences 

 Catalog client scripts are very similar to standard client scripts, with a few important differences. 

**-** Instead of selecting a table such as Incident for the script, select a catalog item or variable set.     As your system may have a large number of catalog items, you should select a catalog item     or variable set using a reference field instead of the choice list that the standard Client Script     form uses. 

**-** When using an onChange() catalog client script, it is linked to a particular variable instead     of a field. The system automatically populates the variable name selection list with any named     variables from the catalog item or variable set selected. 

 Create a catalog client script 

 Follow this procedure to create a catalog client script. 

###### Procedure 

**1.** Navigate to **All** > **Service Catalog** > **Catalog Administration** > **Catalog Client Scripts**.     A list of current custom catalog client scripts appears. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 188 


**2.** Click **New**. 

**3.** Fill in the fields, as appropriate (see table). 

 Field Description 

 Name Enter a unique name for the catalog client script. 

 Applies to Select the item type this client script applies to: 

 ◦ A Catalog Item : enables the Catalog item field. 

 ◦ A Variable Set : enables the Variable set field. 

 Active Select the check box to enable the client script. Clear the check box to disable the script. 

 UI Type Whether to apply this to desktop, mobile, or both. 

 Script Enter the client script that should run on the service catalog item. 

 Type Select when the script should run, such as onLoad or onSubmit. 

 Catalog item or Variable set 

 Select a catalog item or variable set from the list. The field name and options available depend on the selection in the Applies to field. 

 Applies on a Catalog Item view 

 Select the check box to apply the catalog client script to catalog items displayed within the order screen on the service catalog. Available in the requester view. 

 Applies on Requested Items 

 Select the check box to apply the catalog client script on a Requested Item form, after the item is requested. Available in the fulfiller view. See VEditor. 

 Applies on Catalog Tasks 

 Select the check box to apply the catalog client script when a Catalog Task form for the item is being displayed. Available in the fulfiller view. See VEditor. 

 Applies on the Target Record 

 Select the check box to support the catalog UI policy on a record created for task-extended tables via record producers. See Default variable editor. 

**4.** Click **Submit**. 

 Catalog client script examples 

 Examples of client scripts to perform common actions. 

##### Example: Get the value of a variable 

 Use the following syntax to obtain the value of a catalog variable. Note that the variable must have a name. Replace variable_name with the name of the variable. 

 g_form.getValue('variable_name'); 

##### Example: Restrict the number of characters a user can type in a variable 

 This is an example of a script that runs when the variable is displayed, rather than when the item is ordered. 

 function onLoad(){ var sd = g_form.getControl('short_description'); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 189 


 sd.maxLength=80; } 

 Mobile client GlideForm (g form) scripting and migration 

 Client scripting for mobile is identical to scripting for the web, with some exceptions. All new scripts must conform to certain guidelines. The following items are affected on the mobile platform: client scripts, UI policies, navigator modules, and UI actions. 

##### Client scripts 

 For new or existing scripts to be valid for mobile, they must conform to the following requirements: 

**-** Use the new mobile methods in place of g_form.getControl(). 

**-** Do not use deprecated methods. 

**-** Do not reference unsupported browser objects. 

**-** Do not make synchronous JavaScript, GlideAjax, and GlideRecord calls. 

**-** Do not call methods that are not available for mobile. 

**-** Enable scripts to run on the mobile UI. 

 Requirements 

 Use the new mobile methods 

 Several new methods are available for modifying form fields instead of directly manipulating the HTML. These methods replace previous usages of 

###### g_form.getControl(), which is deprecated for the mobile platform. 

 In your existing scripts, ensure that the new methods are used in place of methods that are not valid on the mobile platform. For information on these new methods, refer to Mobile GlideForm() API. 

 Do not use deprecated methods 

 The following methods have been deprecated for the mobile platform because direct access to HTML elements is not allowed: 

**-** g_form.getControl() 

**-** g_form.getFormElement() 

**-** g_form.getElement() 

 To ensure that existing scripts are compatible, remove all calls to deprecated methods from your code. For new scripts, do not use deprecated methods if you want the script to be valid for mobile. 

###### For g_form.getControl(), some of the functionality previously 

 included with this method has been extracted to individual methods. Instead 

###### of g_form.getControl(), use the new methods described on the 

 developer site. 

 Do not reference unsupported browser objects 

 The following browser objects are not supported in mobile scripts: 

**-** Window 

**-** jQuery or Prototype ($, $j, or $$) 

**-** Document 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 190 


 Requirements (continued) 

 Make sure that new scripts do not use these objects, and remove any 

###### usage of these objects from your existing scripts. Use GlideForm 

###### (g_form) instead, which provides methods such as setLabel(), 

###### addDecoration(), and hasField() for accomplishing the same tasks. 

 Do not make synchronous JavaScript calls 

 The mobile platform does not allow synchronous JavaScript calls. The 

###### g_form.getReference() method must now have the callback 

 parameter defined. For example: 

 g_form.getReference(fieldName, callback) 

###### Be sure that all g_form.getReference() calls include the callback 

 parameter. For example, the following script does not include a callback and is incompatible with the mobile platform: 

 var userName = g_form.getReference('assigned_to').user_name; g_form.setValue('u_assigned_user_name', userName); 

 The following script has been updated to include the callback and is compatible with the mobile platform: 

 g_form.getReference('assigned_to', function(now_GR) { g_form.setValue('u_assigned_user_name', gr.user_name); }); 

 Do not make synchronous Ajax calls 

###### The mobile platform does not allow synchronous GlideAjax calls. Any 

###### use of getXMLWait() in a GlideAjax call will not work on the mobile 

###### platform. Be sure that all GlideAjax calls are asynchronous. For more on 

###### synchronous versus asynchronous GlideAjax calls and getXMLWait(), 

###### see AJAX. For information on the available GlideAjax methods, refer to the 

 GlideAjax API. 

 Do not make synchronous 

###### GlideRecord 

 calls 

 The mobile platform does not allow synchronous GlideRecord calls. Make 

###### sure that any existing GlideRecord calls include a callback. For example, 

 the following script does not include a callback and is incompatible with the mobile platform: 

 var now_GR = new GlideRecord('incident'); gr.addQuery('number', g_form.getValue('related_incident')); gr.query(); gr.next(); g_form.setValue('u_related_incident_description', gr.short_description); 

 The following script has been updated to include the callback, and is compatible with the mobile platform: 

 var now_GR = new GlideRecord('incident'); gr.addQuery('number', g_form.getValue('related_incident')); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 191 


 Requirements (continued) 

 gr.query(function(now_GR) { gr.next(); 

 g_form.setValue('u_related_incident_description', gr.short_description); }); 

 Do not use methods unavailable on the mobile platform 

 Due to the limitations and reduced functionality that is imposed by the mobile platform, the following methods are not deprecated but are not available on the mobile platform. If these run on the mobile platform, no action occurs: 

**-** showRelatedList () 

**-** hideRelatedList () 

**-** showRelatedLists () 

**-** hideRelatedLists() 

**-** flash() 

**-** getSections() 

**-** enableAttachments() 

**-** disableAttachments() 

**-** setReadonly() (Note that setReadOnly() is available) 

**-** getParameter() 

 Enable scripts for mobile Scripts must be enabled for the mobile platform. 

##### Note: Focusing an element on a mobile form is not supported. 

##### UI policies 

 Use the Run scripts in UI type field to determine whether scripts run on the mobile platform, the desktop, or both. Update existing policies so that they apply to either the mobile platform or both. For new scripts, also ensure that the mobile option or both is selected. 

##### Navigator modules 

 For existing code, modules must be transferred to either the sys_ui_application or sys_ui_module tables to be available on the mobile platform. When developing new code, be sure that all modules are created in the sys_ui_application or sys_ui_module tables. 

##### UI actions 

 UI actions must be transferred to the sys_ui_ng_action table to appear on the mobile platform. UI action scripts that do not use deprecated methods do not require changes to the script itself. For new UI actions, be sure that they are created in the sys_ui_ng_action table. 

 AJAX 

 AJAX (asynchronous JavaScript and XML) is a group of interrelated, client-side development techniques used to create asynchronous Web applications. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 192 


 AJAX enables web applications to send and retrieve information to and from a server in the background, without impacting the user experience with the displayed web page. 

 GlideAjax 

###### The GlideAjax class allows the execution of server-side code from the client. GlideAjax 

 calls pass parameters to the script includes, and, using naming conventions, allows the use of these parameters. 

##### Note: This functionality requires a knowledge of JavaScript. 

###### Using GlideAjax: 

**-** Initialize GlideAjax with the name of the script include that you want to use. 

**-** When creating the script include, you must set the name field to be exactly the same as the     class name. 

**-** When creating the script include, you must select the **Client callable** check box. 

**-** Specify the parameter sysparm_name. GlideAjax uses sysparm_name to find which     function to use. 

**-** Any extra parameters may be passed in, all of which must begin with sysparm_. Avoid using     predefined parameter names: 

###### ◦ sysparm_name 

###### ◦ sysparm_function 

###### ◦ sysparm_value 

###### ◦ sysparm_type 

**-** Code is then executed with the getXML() or getXMLWait() functions. 

 For additional information, refer to the GlideAjax API. 

 Examples of asynchronous GlideAjax 

###### There are two parts to the asynchronous GlideAjax script: client-side and server-side code. 

##### Hello World: Returning a value from the server 

##### Example: Client side 

 This code runs on the client (the web browser). Create a client script as normal. This sends the parameters to server, which then does the processing. So that the client does not wait for the 

###### result, a callback function is used to return the result, passed to the getXML() function. (In this 

 case it is called HelloWorldParse.) 

###### The getXMLWait() function does not need a separate callback function, but this will block the 

 client. If the client-server communication takes a long time (for example on slow networks), the 

###### application will seem unresponsive and slow. An example of getXMLWait() is in the following 

 section. 

 var ga = new GlideAjax('HelloWorld'); ga.addParam('sysparm_name', 'helloWorld'); ga.addParam('sysparm_user_name', "Bob"); ga.getXML(HelloWorldParse); 

 function HelloWorldParse(response) { 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 193 


 var answer = response.responseXML.documentElement.getAttribute("answer"); alert(answer); } 

##### Example: Server side 

 The server-side code for the above function. Do not create a business rule, but instead navigate to System Definition > Script Include and create a new script. Paste in the code below. 

##### Note: You must set the name of the script include to HelloWorld. 

**-** The sys_script_include code must extend the AbstractAjaxProcessor class and     be Glide AJAX enabled. 

**-** Function names starting with "_" are considered private and are not callable from the client. 

**-** Avoid overriding methods of AbstractAjaxProcessor, including initialize. While     it is possible to invoke methods of your superclass object which you have overridden, it is     complicated and best avoided altogether. 

 var HelloWorld = Class.create(); HelloWorld.prototype = Object.extendsObject(AbstractAjaxProcessor, { helloWorld:function() { return "Hello " + this.getParameter('sysparm_user_name') + "!"; } , _privateFunction: function() { // this function is not client callable } }); 

 This results in an alert box that says 'Hello Bob!' when you visit the form. 

##### Returning multiple values 

 Since the response is an XML document we are not limited to returning a single answer value. Here is a more complex example returning multiple XML nodes and attributes. 

##### Example: AJAX processor script include 

 /* * MyFavoritesAjax script include Description sample AJAX processor returning multiple value pairs */ var MyFavoritesAjax = Class.create(); MyFavoritesAjax.prototype = Object.extendsObject(AbstractAjaxProcessor, { 

 /* * method available to client scripts call using: * var gajax = new GlideAjax("MyFavoritesAjax"); * gajax.addParam("sysparm_name","getFavorites"); */ getFavorites: function() { // build new response xml element for result var result = this.newItem("result"); result.setAttribute("message","returning all favorites"); 

 //add some favorite nodes with name and value attributes 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 194 


 this._addFavorite("color","blue"); this._addFavorite("beer","lager"); this._addFavorite("pet","dog"); }, // all items are returned to the client through the inherited methods of AbstractAjaxProcessor _addFavorite: function(name, value) { var favs = this.newItem("favorite"); favs.setAttribute("name",name); favs.setAttribute("value",value); }, 

 type:"MyFavoritesAjax" 

 }); 

##### Example: Client script 

 // new GlideAjax object referencing name of AJAX script include var ga = new GlideAjax("MyFavoritesAjax"); // add name parameter to define which function we want to call // method name in script include will be getFavorites ga.addParam("sysparm_name","getFavorites"); 

 // submit request to server, call ajaxResponse function with server response 

 ga.getXML(ajaxResponse); 

 function ajaxResponse(serverResponse) { // get result element and attributes var result = serverResponse.responseXML.getElementsByTagName("result"); var message = result[0].getAttribute("message"); 

 //check for message attribute and alert user if(message) alert(message); 

 //build output to display on client for testing var output = ""; 

 // get favorite elements var favorites = serverResponse.responseXML.getElementsByTagName("favorite"); for(var i = 0; i < favorites.length; i ++) { var name = favorites[i].getAttribute("name"); var value = favorites[i].getAttribute("value"); output += name + " = " + value + "\n "; } 

 alert(output); } 

##### Example: XML response 

 <xml sysparm_max= "15" sysparm_name="getFavorites" sysparm_processor="MyFavoritesAjax"> <result message = "returning all favorites"></result> <favorite name = "color" value = "blue"></favorite> <favorite name = "beer" value = "lager"></favorite> 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 195 


 <favorite name = "pet" value = "dog"></favorite> </xml> 

 Examples of synchronous GlideAjax 

###### Use synchronous when your script cannot continue without the GlideAjax response. This 

 stops the session until the response is received. 

###### If your use case demands that no further processing can occur until the GlideAjax response 

###### has been received, you can use getXMLWait(). However, because this will slow down your 

 code and lock the user session until the response is received, it is generally recommended that 

###### you use getXML() with a callback function. 

##### Note: Do not use AJAXEvaluateSynchronously. 

###### The getXMLWait() method is not available in scoped applications. 

 This code results in a client-side alert that displays The Server Says Hello Bob!. 

 The client code. 

 var ga = new GlideAjax('HelloWorld') ; ga.addParam('sysparm_name','helloWorld'); ga.addParam('sysparm_user_name',"Bob"); ga.getXMLWait(); alert(ga.getAnswer()); 

 The server-side script include code. 

 var HelloWorld = Class.create(); HelloWorld.prototype = Object.extendsObject(AbstractAjaxProcessor, { helloWorld: function() { return "The Server Says Hello " + this.getParameter('sysparm_user_name') + "!"; } } ); 

 AJAXClientHelper 

 Provides helper functions for Ajax clients to retrieve a value from an Ajax client. 

##### Where to use 

 Use this script include wherever your need to retrieve a value from an Ajax client. 

##### Method summary 

 Method summary Description 

###### getDisplay() Gets the display value from the choice list. 

##### Method detail 

 API method Description 

 Input parameters 

 Output returns 

###### getDisplay() Gets the display value from the choice 

 list. 

 none The display value. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 196 


##### Example: Curl 

 // getDisplay (function(table, sysId) { var ga = new GlideAjax('AjaxClientHelper'); ga.addParam("sysparm_name", "getDisplay"); ga.addParam('sysparm_table', 'incident'); ga.addParam('sysparm_value', "0598b22b877313003c1c8467a7cb0b71"); ga.getXMLWait(); return ga.getAnswer(); }("incident", "0598b22b877313003c1c8467a7cb0b71")); // Returns 'INC0010001' 

##### Useful scripts 

 Server-side and client scripts that provide useful functionality not included in the core system. 

 Business rule use cases 

 Use cases for business rules include aborting a database action and restricting record access. 

 Abort a database action 

 You can use a before business rule script to cancel or abort the current database action using 

###### the current.setAbortAction(true) method. 

 If the before business rule is executed during an insert action, and a condition in the script calls 

###### current.setAbortAction(true), the new record stored in current is not created in 

 the database. 

 Related topics 

 GlideRecord setAbortAction(Boolean b) 

 Scoped GlideRecord setAbortAction(Boolean b) 

 Restricting record access 

 You can use a query business rule that executes before the database query to prevent users from accessing certain records. 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

 Consider the following example from a default business rule that limits access to incident records. 

 Default business rule limits access to incident records 

 Name Table When 

 incident query Incident before, query 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 197 


##### Example: Restricting record access 

 In the following example, users are restricted from accessing incident records unless they have the itil role and are listed in the Caller or Opened by field. When self-service users open a list of incidents, they can only see the incidents they submitted. 

 if (!gs.hasRole("itil")&& gs.isInteractive()) { var u = gs.getUserID(); var qc = current.addQuery("caller_id", u).addOrCondition("opened_by", u).addOrCondition("watch_list","CONTAINS", u); gs.print("query restricted to user: " + u);} 

##### Note: You can also use access controls to restrict the records that users can see. For 

 information, see Access Control List Rules. 

##### Schedule script for weekdays 

 Type: Business Rules/Client Scripts. 

 This script schedules the script for weekdays. Insert any script where it says "Your Script Here." 

 var go ='false'; var now =new Date(); 

 // Correct time zone, which is by default GMT -7 now.setHours(now.getHours()+8); var day = now.getDay(); 

 // No go on Saturday or Sunday if(day !=0&& day !=6){ 

 // (your script here) 

 } 

##### Set date field according to current date 

 This script sets a date field depending on the current day of the week. In this example, if the day is Monday through Wednesday, it sets the date to this coming Monday; otherwise it sets the date field to next Monday. 

 function setCabDate(){ var today = new Date(); var thisDay = today.getDay(); 

 //returns 0 for Sunday, 1 for Monday, through 6 for Saturday. var thisMon = new GlideDateTime(); thisMon.setDisplayValue(gs.beginningOfThisWeek()); var nextMon = thisMon.getNumericValue(); nextMon +=(1000*60*60*24*7); 

 if((thisDay <4)&&(thisDay >0)) //if today is Mon thru Wed (thisDay = 1, 2, or 3), set cab to this coming Monday. 

 current.u_req_cab_rev_date.setDateNumericValue(thisMon.getNumer icValue()); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 198 


 else if((thisDay >=4)||(thisDay ==0)) //if today is Thurs thru Sun (thisDay = 4, 5, 6, or 0), set cab to next Monday. current.u_req_cab_rev_date.setDateNumericValue(nextMon); } 

 To validate the input of all date/time fields, you can use the following in a validation script ( System Definition > Validation Scripts ). Because the date/time format is hard coded in this script, it must match your instance's date/time format. If your instance's date/time format changes, you must update your validation script. 

 Set the validation script's type to Date/Time. Then, with this validation script, if a user enters an incorrect format in a date/time field, they receive an error message. 

 function validate(value){ // empty fields are still valid dates if(!value) return true; 

 // We "should" have the global date format defined always defined. But there's always that edge case. if(typeof g_user_date_time_format !=='undefined') return isDate(value, g_user_date_time_format); 

 // if we don't have that defined, we can always try guessing return parseDate(value)!==null;} 

 For more information, see Validation script use case Date and time. 

 Client-side script use cases 

 Use cases for client-side scripts include displaying field messages, changing form colors, adding fields, and creating UI routing actions. 

 Add a field to the service catalog checkout 

 This is an example of adding a Company field to the checkout below the Requested for field 

###### using non-cart layout macros, that is, glide.sc.use_cart_layouts is false. 

###### Before you begin 

 Role required: Admin 

###### About this task 

 Requested for field 

 This field passes a provided value to the Company field of the Service Catalog Request. 

 This example makes the following assumptions: 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 199 


**-** The instance using two-step checkout. If two-step checkout is not enabled, enable it before     beginning. For more information, see Service Catalog checkout models. 

**-** This example populates the **Company** field on the Service Catalog Request form. If the field     does not appear on the form, configure the form before beginning. For instructions, see     Personalize a form. 

###### Procedure 

**1.** Go to **System UI > UI Macros** and select **servicecatalog_cart_template**. 

**2.** Find where there are hidden variables declared and add the following line: 

 <input type="HIDDEN" name="cart_id" id="cart_id" value="$[sc_cart.sys_id]" /> 

**3.** Find the following code, which generates the **Requested For** code: 

 <tr class="header"> <td width = "30%"> ${gs.getMessage('Requested for')}: </td> <td width="70%"> <label for="requestor_location">${gs.getMessage('Deliver to')}:</label> </td> </tr> <tr><td>$[SP]</td> </tr> <tr><td valign="top"> <j2:if test="$[jvar_can_delta_rf == false]"> $[sc_cart.requested_for.getDisplayValue()] </j2:if> <j2:if test="$[jvar_can_delta_rf != false]"> <g2:catalog_requested_for /> </j2:if> </td> <td> <textarea id="requestor_location" style="width:100%" rows="4" name="requestor_location" wrap="soft" onChange="catDeliveryAddress('$[sc_cart.sys_id]', 'requestor_location');"> $[sc_cart.delivery_address] </textarea> </td> </tr> <tr> <td>$[SP]</td> </tr> 

**4.** Add the following code afterward: 

 <tr class="header"> <td colspan="2">Company</td> </tr> <tr> <td>$[SP]</td> 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 200 


 </tr> <tr> <td colspan="2"> <g2:ui_reference name="core_company" table="core_company" onchange="setCartValue()"/> </td> </tr> <tr> <td>$[SP]</td> </tr> 

##### Note: The 'ui_reference' macro defines a reference field. There are several 

 macros for different field types. You can see examples of these field types under System UI -> UI Macros. These macros start with 'ui_'. For this example, the reference field created is named core_company. For more information, see UI macros. 

**5.** Now navigate to **System UI > UI Pages** and select the **servicecatalog_checkout_one** UI Page. 

**6.** Add the followings script to the **Client script** field. 

 function setCartValue() { var newField = gel('core_company'); var myCart = gel('cart_id'); var cart_item = new GlideRecord('sc_cart_item'); cart_item.addQuery('cart', myCart.value); cart_item.query(); if(cart_item.next()) { cart_item.hints = "<hints><entry key='sysparm_processing_hint' value='setfield:request.company=" + newField.value + "'/></hints>"; cart_item.update(); } } 

 For this example, the reference field was called core_company , and the field being populated on the request is company. If different fields are used: 

 ◦ Find this line: var company = gel('core_company'); and replace core_company with the name of the field in the checkout. 

 ◦ In the line that starts with 'cart_item.hints' replace 'request.company' with the name of the field to be populated on the request ticket where 'request' is the request being generated and 'company' is the name of the field. 

###### Result 

 When an item is ordered, the company field appears on the Catalog form: 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 201 


 Add autofill functionality 

 Add autofill functionality is also called incident template, auto assignments, quick calls, call script, or auto populate. 

 To auto-fill a Short Description field based on the Subcategory selected: 

**1.** Create a lookup table. 

**2.** Populate the key field, **Subcategory**. 

**3.** Populate the auto-filled field, **Short Description**. 

 function onChange(control, oldValue, newValue, isLoading) { if (isLoading) { return; } var newrec = gel('sys_row'); //Check if new record if (newrec.value == -1) { var lookup = new GlideRecord('u_short_desc_lookup'); lookup.addQuery('u_subcategory', g_form.getValue('subcategory')); lookup.query(); var temp; //temp var reusable if (lookup.next()) { temp = lookup.u_short_description; if (null != temp) { //Set the form value from lookup if there is a lookup value g_form.setValue('short_description', temp); } else { g_form.setValue('short_description', "" ); } } else { 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 202 


 //If a lookup record does not exist based on lookup.addQuery //Then set to UNDEFINED or NULL depending on type g_form.setValue('short_description', ""); } } } 

 You can populate many fields or pull in call script questions into the Comments field so call center personnel gather good information to pass on to a technician. 

 Setting a field to password reset 

 Lookup table has a record with the following key and auto-fill settings: 

**- Subcategory** = _Password_ 

**- Short Description** = _Password Reset_ 

 Client script settings: 

**- Type** = _onChange_ 

**- Table name** = _incident_ 

**- Field name** = _Subcategory_ 

 When the user selects the subcategory of Password on the Incident form, a client script looks up the matching record and sets the short description equal to Password Reset. 

 Change form color on state change 

 Changes color of a form field of the form on state change. The script can easily be changed to adjust any property of any object on the page accessible via the HTML DOM. 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

 Name : Change Form Color on State Change 

 Type : Client script 

 Description : Changes color of a form field of the form on state change. The script can easily be changed to adjust any property of any object on the page accessible via the HTML DOM. 

 Script : 

 function onChange(control, oldValue, newValue, isLoading) { var elementID = gel("incident.priority"); switch(newValue) { case "1": elementID.style.backgroundColor = "red"; break; case "2": elementID.style.backgroundColor = "tomato"; break; case "3": elementID.style.backgroundColor = "orange"; break; case "4": elementID.style.backgroundColor = "yellow"; break; case "5": elementID.style.backgroundColor = "green"; break; default: elementID.style.backgroundColor = "white"; break; } } 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 203 


 Create a UI routing action 

 This solution enables you to create a record with the service desk without knowing whether it is an incident or request item; the service desk can then route the record to the appropriate table. 

###### Before you begin 

 Role required: Admin 

###### Procedure 

**1.** Create a new table that extends the task table (for example, New Call). 

**2.** Create a module to create a new New Call record. 

**3.** Create any fields that you want on the New Call table. 

 The only fields you need are those fields necessary to determine whether the new call should route to an Incident or a Request Item. Ensure that the form contains any fields that you want to pass to the Incident or Request Item. In this example, the following are created on the form: 

 ◦ Requested for (reference) 

 ◦ Location (reference) 

 ◦ Call type (choice with two values--Incident and Request) 

 ◦ Request Item (reference to the sc_cat_item Item table) 

**4.** Add some UI policies to set a couple of fields to mandatory and hide the **Request item** field     based on the **Call type** selection. 

**5.** Remove unnecessary buttons and functionality from the form. 

**6.** Create a new UI Action button.     This button redirects the user to either an incident or a request. It also creates the incident     record and copies values to the incident and the Request Item form. 

 var reqItem = current.u_item; var requestedFor = current.u_requested_for; var location = current.location; 

 if(current.u_incident_request == 'Incident'){ //Create a new incident record and redirect to the new incident var rec = new GlideRecord('incident'); rec.initialize(); rec.caller_id = requestedFor; rec.location = location; rec.insert(); action.setRedirectURL(rec); } 

 if(current.u_incident_request == 'Request'){ //Build the url and route the user to the request item var url = ''; if(current.u_item.sys_class_name == 'sc_cat_item_guide'){ url = 'com.glideapp.servicecatalog_cat_item_guide_view.do?sysparm_in itial=true&sysparm_guide=' + reqItem + '&sysparm_user=' + requestedFor + '&sysparm_location=' + location; } 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 204 


 else{ url = 'com.glideapp.servicecatalog_cat_item_view.do?sysparm_id=' + reqItem + '&sysparm_user=' + requestedFor + '&sysparm_location=' + location; } action.setRedirectURL(url); } 

**7.** The **Route** button in the preceding example passes the **Requested for** and **Location** values in     the URL to the Request Item form. 

###### Ensure that you have variables called requested_for and location on your item, record 

 producer, or order guide that map these values using the following client script. There is a limit as to how much information you can pass, as the URL has a restricted length. Avoid sending information from long text fields using this method. 

 function onLoad() { var url = document.location.toString(); var userKey = 'sysparm_user='; var locKey = 'sysparm_location='; var userPosition = url.indexOf(userKey); var locPosition = url.indexOf(locKey) if (userPosition != -1) { var user = url.substr(userPosition+userKey.length, 32); g_form.setValue('requested_for', user); } if (locPosition != -1) { var loc = url.substr(locPosition+locKey.length, 32); g_form.setValue('location', loc); } } 

 Display field messages 

###### Rather than use JavaScript alert(), for a cleaner look, you can display an error on the form 

###### itself. The methods showFieldMsg() and hideFieldMsg() can be used to display a 

 message just below the field itself. 

###### showFieldMsg and hideFieldMsg are methods that can be used with the g_form object. 

 These methods are used to change the form view of records (Incident, Problem, and Change forms). These methods may also be available in other client scripts, but must be tested to determine whether they work as expected. 

 When a field message is displayed on a form on load, the form scrolls to ensure that the field message is visible. Ensuring that users do not miss a field message because it was off the screen. 

###### The global property glide.ui.scroll_to_message_field controls automatic message 

 scrolling when the form field is offscreen (scrolls the form to the control or field). 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 205 


 Method Detail 

 Method Detail Parameters Example 

 showFieldMsg(input, message, type, [scrollform]) 

**-** input — name of the     field or control 

**-** message — message     you would like to     appear 

**-** type — 'info', 'error', or     'warning'; defaults to     info if not supplied 

**-** scroll form —     (optional) Set 

###### scrollForm to false 

 to prevent scrolling to the field message offscreen 

 Error Message 

 g_form.showFieldMsg('impact',' Low impact not allowed with High priority','error'); 

 Informational Message 

 g_form.showFieldMsg('impact', 'Low impact response time can be one week','info'); //or this defaults to info type // g_form.showFieldMsg('impact', 'Low impact response time can be one week'); 

 hideFieldMsg(input) 

**-** input — name of the     field or control 

**-** clearAll — (optional)     boolean parameter     indicating whether to     clear all messages. If     true, all messages for     the field are cleared.     If false or empty, only     the first message is     removed 

 Removing a Message 

 //this will clear the first message printed to the field g_form.hideFieldMsg('impact'); 

##### Legacy support 

###### The showErrorBox() and hideErrorBox() methods are not recommended. 

 Using client and server code in a UI action 

 You can use a script to validate input upon a UI Action click on the client side before updating the record on the server side. The user will not have to click the button twice to validate the required fields and update the record. 

 The script calls the client function for client-side validation, and the UI action completes the task if it passes. The code that runs without onclick statement ensures that the server

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 206 


 side function does not run until the client function is no longer running. If successful, the serverside function runs and updates the record. 

 // Client-side onclick function function resolveIncident() { // Set the 'Incident state' and 'State' values to 'Resolved', and display mandatory fields g_form.setValue('incident_state', 6); g_form.setValue('state', 6); g_form.setValue('resolved_by', g_user.userID); 

 // Call the UI action and skip the 'onclick' function gsftSubmit(null, g_form.getFormElement(), 'resolve_incident'); //MUST call the 'Action name' set in this UI Action } 

 // Code that runs without 'onclick' // Ensure call to server-side function with no browser errors if (typeof window == 'undefined') serverResolve(); 

 // Server-side function function serverResolve() { current.incident_state = IncidentState.RESOLVED; current.state = IncidentState.RESOLVED; current.resolved_by = gs.getUserID(); current.update(); } 

##### gsftSubmit(String control, Object form, String action_name) 

 Submits a form as if the user had clicked a UI Action after checking for required fields and 

###### executing onSubmit() client scripts. Enables calling client-side code and server-side code 

 and in a single UI action. 

 Parameters 

 Name Type Description 

 control String Name of a form button on which you want to simulate a user click. Use null otherwise. 

 form Object Optional. The form element that contains the submitted input. You can retrieve this value by calling the 

###### g_form.getFormElement() method. 

 action_name String Action name. This value is provided in the record listed in the UI Actions [sys_ui_action] table. 

 For example, 'resolve_incident' is the action name of the Resolve button in the Incident [incident] table. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 207 


 Related topics 

 GlideForm getFormElement() 

 Scoped GlideSystem eventQueue(String name, Object instance, String parm1, String parm2, String queue) 

 GlideUser Client 

 Defining UI actions 

 Field script use cases 

 Common use cases for field customization scripts. 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

 For more information, see Server API reference. 

##### Automatically populate a field 

 The following example shows how to use a client script to auto-fill a Short Description based on the selected Subcategory. 

 In this case, if the table has a record with Subcategory = Password and Short Description = Password Reset. When the user selects the Subcategory of Password on the Incident form, a client script looks up the matching record and sets Short Description equal to Password Reset. 

 Client script settings: 

**-** Type = onChange 

**-** Table name = incident 

**-** Field name = Subcategory 

 function onChange(control, oldValue, newValue, isLoading){ if(isLoading){return;} var newrec = gel('sys_row'); //Check if new record if (newrec.value == -1) { var lookup = new GlideRecord('u_short_desc_lookup'); lookup.addQuery('u_subcategory', g_form.getValue('subcategory')); lookup.query(); var temp; //temp var reusable if(lookup.next()){ temp = lookup.u_short_description; if(null != temp) { //Set the form value from lookup if there is a lookup value g_form.setValue('short_description', temp); } else { g_form.setValue('short_description',""); } } else { //If a lookup record does not exist based on lookup.addQuery 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 208 


 //Then set to UNDEFINED or NULL depending on type g_form.setValue('short_description',""); } } } 

##### Disable HTML tags in descriptions 

 This code disables HTML tags in Description and Short Description fields by substituting the tags with non-executing versions. 

 doit(); 

 function doit(){ var desc = current.description.toString(); var shdesc = current.short_description.toString(); if(desc.indexOf('script>')>-1|| shdesc.indexOf('script>')>-1){ desc = desc.replace(/<script>/g,"(script)"); current.description = desc.replace(/<\/script>/g,"(\/script)"); shdesc = shdesc.replace(/<script>/g,"(script)"); current.short_description = shdesc.replace(/<\/script>/g,"(\/script)");} } 

##### Eliminate leading and trailing spaces in fields 

###### This example of the script trims trailing and leading spaces in the FirstName and LastName 

 fields of the sys_user. 

 doit(); 

 function doit(){ var now_GR =new GlideRecord('sys_user'); gr.query(); while(gr.next()){ if((gr.first_name.toString().length!= gr.first_name.toString().trim().length)||(gr.last_name.toString ().length!= gr.last_name.toString().trim().length)){ gr.first_name= gr.first_name.toString().trim(); gr.last_name= gr.last_name.toString().trim(); gr.autoSysFields(false); gr.update();}} } 

##### Make a field label flash 

 The following client script example is for the number field on incident. The label flashes for two seconds. 

 g_form.flash("incident.number","﷯FFFACD",0); 

 The arguments for the flash method are as follows: 

**-** tablename.fieldname 

**-** RGB color or acceptable CSS color like "blue" or "tomato" 

**-** Integer that determines how long the label flashes: 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 209 


 ◦ 2 for a 1-second flash 

 ◦ 0 for a 2-second flash 

 ◦ -2 for a 3-second flash 

 ◦ -4 for a 4-second flash 

##### Note: Do not specify this argument if you want the field label colored the specified color. 

##### Make a field label bold 

 This client script makes the label of a particular field bold. In this case, the field is the Short Description on the Incident Table. 

 function onLoad(){ var l = g_form.getLabel('incident.short_description'); l.style.fontWeight = 'bold';} 

##### Make fields read-only 

 This onLoad client script makes the following fields on the Incident [incident] table read-only: 

**- Incident state** 

**- Impact** 

**- Urgency** 

**- Priority** 

**- Configuration item** 

**- Assigned to** 

 The script also removes the magnifying glass for the read-only Reference Fields ( Configuration item and Assigned to ). 

 function onLoad(){ var incidentState = g_form.getValue('incident_state'); if( incidentState == '6'|| incidentState == '7'){ g_form.setReadonly('incident_state',true); g_form.setReadonly('impact',true); g_form.setReadonly('urgency',true); g_form.setReadonly('priority',true); g_form.setReadonly('cmdb_ci',true); g_form.setReadonly('assigned_to',true);}} 

##### Set current date/time in field 

 You can set date and time values in client scripts and script includes. 

 Client script 

 You can use the following two lines to set the current date and time in a date/time field. This approach bypasses the problem of getting the value into the proper format and proper time zone. 

 var ajax = new GlideAjax('MyDateTimeAjax'); ajax.addParam('sysparm_name','nowDateTime'); ajax.getXML(function(){ g_form.setValue('put your field name here', ajax.getAnswer());}); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 210 


 For more information on running server-side scripts with the client, refer to GlideAjax. 

 System script include 

 // Be sure the Glide AJAX enabled option is checked 

 var MyDateTimeAjax = Class.create(); MyDateTimeAjax.prototype = Object.extendsObject(AbstractAjaxProcessor,{ nowDateTime:function(){ return gs.nowDateTime();}}); 

##### Toggle the timer field by field name 

 The following client script toggles the timer field based on a particular field name. 

 function toggleTimerByFieldName(fieldName){ //Step 1: Find the timer object //timeObjectName: the timer objects name as it would normally be referenced //timeObjectHidden: the hidden input node in the field td //timeObjectParent: the parent td node containing the field and it's constituent nodes //timeObjectFields: anchor tag with onclick to stop timer 

 var timeObjectName = fieldName; var timeObjectHidden = gel(timeObjectName); 

 //Step 2: simulate click stop button var timeObjectParent; var timeObjectFields; 

 //verify that we got the correct object if(timeObjectHidden.type=="hidden"){ 

 //Get Parent td node timeObjectParent = timeObjectHidden.parentNode; 

 //Get input fields timeObjectFields = timeObjectParent.getElementsByTagName("input"); 

 //simulate click of stop button var timerTestString ="paused"; var timerImg; 

//loop through input objects looking for the pause timer object for(var elIt=0; elIt < timeObjectFields.length; elIt++){ if(timeObjectFields[elIt].id.match(timerTestString)){ if(timeObjectFields[elIt].value=="false"){ timeObjectFields[elIt].value="true"; timerImg = timeObjectParent.getElementsByTagName("img")[0]; timerImg.src="images/timer_start.gifx";} elseif(timeObjectFields[elIt].value=="true"){ timeObjectFields[elIt].value="false"; © 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 211 


 timerImg = timeObjectParent.getElementsByTagName("img")[0]; timerImg.src="images/timer_stop.gifx";}}}}} 

##### Modify GlideDateTime field value 

###### The following example uses a server-side script to access a GlideDateTime field. 

 The following server-side script example shows how to modify values using the 

###### GlideDateTime API. The same concept also applies to the GlideDate object. 

 //You first need a GlideDateTime object //this can be from instantiating a new object "var gdt = new GlideDateTime()" //or getting the object from a GlideDateTime field //getting the field value (for example: var gdt = current.start_date) //only returns the string value, not the object //to get the object use var gdt = current.start_date.getGlideObject(); //now gdt is a GlideDateTime object var gdt = current.start_date.getGlideObject(); 

 //All methods can use negative values to subtract intervals 

 //add 1 hour (60 mins * 60 secs) gdt.addSecondsLocalTime(3600); 

 //add 1 day gdt.addDaysLocalTime(1); 

 //subtract 1 day gdt.addDaysLocalTime(-1); 

 //add 3 weeks gdt.addWeeksLocalTime(3); 

 //subtract 6 months. gdt.addMonthsLocalTime(-6); 

 //add 1 year, representing the date and time using the UTC timezone instead of the local user's timezone. gdt.addYearsUTC(1); 

 Approval assignment scripts 

 This is a searchable version of the useful approval and assignment scripts. 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

 For see Viewing my approvals. 

 Assign a group for ESS requests 

 The following Assignment Rulescript automatically assigns a group for all ESS Requests. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 212 


 if(current.opened_by.roles==""){ 

 current.assignment_group.setDisplayValue('Network'); current.update();} 

 Assign catalog item to group based on delivery plan task 

 This assignment rule assigns a service catalog item to the database group if it uses a delivery plan that has a catalog task assigned to the desktop group. 

 //Return catalog items that have no group but do have a delivery plan assigned var ri =new GlideRecord("sc_cat_item"); ri.addQuery("group","=",null); ri.addQuery("delivery_plan","!=",null); ri.query(); while(ri.next()){ gs.log("Found an item"); //Return tasks that point to the same delivery plan as the above item var dptask =new GlideRecord("sc_cat_item_delivery_task"); 

 dptask.addQuery("delivery_plan","=",ri.delivery_plan); dptask.query();while(dptask.next()){ gs.log("Found a task");var gp = dptask.group.getDisplayValue(); gs.log(gp);//If the task is assigned to desktop, assign the item's group to desktop if(dptask.group.getDisplayValue()=="Desktop"){ ri.group.setDisplayValue("Desktop"); gs.log("updating "+ ri.getDisplayValue()); ri.update();break;}}} 

 Assign items with one task 

 This assignment rule automatically assigns any catalog items with only one task associated to a particular group. 

 //Get the catalog item for the current requested item var scCatItem =new GlideRecord("sc_cat_item"); if(scCatItem.get('sys_id', current.cat_item)){ // If the catalog item already has an assignment group or if using workflow we don't need to make an assignment if(!scCatItem.delivery_plan.nil()&& scCatItem.group.nil()){ var dpTask =new GlideRecord("sc_cat_item_delivery_task"); 

 dpTask.addQuery("delivery_plan","=",scCatItem.delivery _plan); dpTask.query(); if(dpTask.getRowCount()==1&& dpTask.next()){ // Check that there is only 1 record in the GlideRecord dpTask.group;}}} 

 Assignment based on workload 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 213 


 Type: Business Rule. 

 Description: Populate the assigned to based on the assignment group member who has the least amount of active incidents. 

 Parameters: 

**-** order: >1000 if you want to execute after assignment rules 

**-** condition: current.assigned_to == '' && current.assignment_group != '' 

**-** when: before, insert/update 

 var assignTo = getLowestUser(); gs.addInfoMessage("assigning to is "+ assignTo); current.assigned_to= assignTo; 

 function getLowestUser(){ var userList =new Array(); var cg =new GlideRecord('sys_user_grmember'); cg.addQuery('group', current.assignment_group); cg.query(); while(cg.next()){ var tech = cg.user.toString(); var cnt = countTickets(tech); gs.addInfoMessage("Tech counts "+ cg.user.name+' '+ cnt +" "+ tech); userList.push({ sys_id: tech,name: cg.user.name, count: cnt });} 

 for(var i=0; i < userList.length; i++){ gs.addInfoMessage(userList[i].sys_id+" "+ userList[i].name+" "+ userList[i].count);} userList.sort(function(a, b){ gs.addInfoMessage("Sorting: "+ a.sys_id+"("+ a.count+"); "+ b.sys_id+"("+ b.count+")"); return a.countb.count;}); 

 if(userList.length<=0)return""; return userList[0].sys_id;} 

 function countTickets(tech){ var ct =new GlideRecord('incident'); ct.addQuery('assigned_to',tech); ct.addQuery('active',true); ct.query(); return ct.getRowCount();} 

 Run assignment rules when category is changed 

 Type: Client script. 

 Table: Incident. 

 Description: This example is an onChange client script on the category field within Incident. Note: this script used to use synchronous AJAX (asynchronous behavior is specified by the third parameter of the ajaxRequest call). The implementation below 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 214 


 uses asynchronous AJAX. The drawback of using the synchronous version is that a network response problem could cause the browser to hang. 

 // Make an AJAX request to the server to get who this incident would be // assigned to given the current values in the record. This runs the assignment // rules thathave been defined in System Policy and returns the assigned_to and // the assignment_group 

 function onChange(control, oldValue, newValue, isLoading){ if(isLoading){return; // No change, do not do anything } 

 // Construct the URL to ask the server for the assignment var url ="xmlhttp.do?sysparm_processor=AJAXAssignment&sys_targ et=incident"; var uv = gel('sys_uniqueValue'); if(uv){ url +="&sys_uniqueValue="+ uv.value;} // Make the AJAX request to the server and get the response var serial = g_form.serialize(); // get all values currently assigned to the incident var response = ajaxRequest(url, serial,true, responseFunc);} 

 // This callback function handles the AJAX response. function responseFunc(response){ varitem= response.responseXML.getElementsByTagName("item")[0]; // Process the item returned by the server if(item){ // Get the assigned_to ID and its display value and put them on the form varname=item.getAttribute("name"); var name_label =item.getAttribute("name_label"); if(name_label &&name){ g_form.setValue('assigned_to',name, name_label);} else{ g_form.setValue('assigned_to','','');} // Get the assignment_group ID and its display value and put then on the form var group =item.getAttribute("group"); var group_label =item.getAttribute("group_label"); if(group_label && group){ g_form.setValue('assignment_group', group, group_label);} else{ g_form.setValue('assignment_group','','');}}} 

 Custom approval UI macro 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 215 


 For information on creating a custom approval UI macro, see UI macros. 

 Scheduling script use cases 

 A business rule script specifies the actions that the business rule takes. Scripts commonly include predefined global variables to reference items in your system, such as the current record. Global variables are available to all business rules. 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

##### Calculate duration given a schedule 

 Type: Before update/insert business rule. 

 Description: A business duration calculates the open to close duration on an incident based on the particular Creating and using schedules. If there is no schedule specified, the script will simply use the first schedule returned by the query. 

 Script example: 

 The example below sets the resolved duration when the incident state moves to resolved. 

 var gr_rec = new GlideRecord('incident'); gr_rec.get('ed92e8d173d023002728660c4cf6a7bc'); if (gr_rec.incident_state == 6) { var dur = calcDurationSchedule(gr_rec.opened_at, gr_rec.sys_updated_on); } 

 function calcDurationSchedule(start, end){ // Get the user var usr = new GlideRecord('sys_user'); usr.get(gs.getUserID()); // Create schedule pass in the sys_id of your standard work day schedule and pass in the users timezone var sched = new GlideSchedule('08fcd0830a0a0b2600079f56b1adb9ae',usr.time_zon e); // Get duration based on schedule/timezone return(sched.duration(start.getGlideObject(), end.getGlideObject())); } 

##### Check upcoming termination dates 

 Type: Scheduled script. 

 Description: This script checks nightly for termination dates on contracts coming up in 90, 50, or 10 days (depending on the contract duration field). 

 Script example: 

 function contractNoticeDue(){ var now_GR = new GlideRecord("contract"); now_GR.addQuery("u_contract_status","Active"); now_GR.query(); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 216 


 while(now_GR.next()){ if((now_GR.u_termination_date<= gs.daysAgo(-90))&&(now_GR.u_contract_duration=="Long")){ now_GR.u_contract_status="In review";} elseif((now_GR.u_termination_date<= gs.daysAgo(-50))&&(now_GR.u_contract_duration=="Medium")){ now_GR.u_contract_status="In review";} elseif((now_GR.u_termination_date <= gs.daysAgo(-10))&&(now_GR.u_contract_duration=="Short")){ now_GR.u_contract_status="In review";} now_GR.update(); } } 

 Use scripts in business rules to accomplish common tasks such as: 

**-** Comparing two date fields. 

**-** Parsing XML payloads. 

**-** Aborting a database action in a business rule. 

 With scripts, you can also: 

**-** Specify the operation that triggers the business rule. 

**-** Use the scratchpad with display business rules to change form values just before a user loads     the form. 

**-** Use the OR condition like you would in a condition builder. 

 You can also utilize the system's scripting functionality available for server-side scripts. 

 You can use options on the Business Rules form to build conditions, set field values, and display alert messages without needing to write a script. 

 Server-side script use cases 

 Use cases for server-side scripts include logging output, getting user objects, and modifying date/time values. 

 Accessing the workflow scratchpad from business rules 

 A catalog item has been requested, and the attached workflow contains a run script activity that populates a value in the scratchpad. From a business rule running on the requested item, you want to retrieve or set scratchpad values. 

##### Prerequisites 

 Role required: admin. 

 Name: Access Workflow Scratchpad from Business Rules. 

 Type: Business Rule. 

 Table: sc_req_item (Requested Item). 

 Description: A catalog item has been requested, the attached workflow contains a run script activity that populates a value in the scratchpad. From a business rule running on the requested item, you want to retrieve or set scratchpad values. 

 Parameters: n/a. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 217 


 Script: 

 //the run script activity sets a value in the scratchpad workflow.scratchpad.important_msg = "scratch me"; 

 //get the workflow script include helper var workflow = new Workflow(); 

 //get the requested items workflow context //this will get all contexts so you will need to get the proper one if you have multiple workflows for a record var context = workflow.getContexts(current); //make sure we have a valid context if (context.next()) { //get a value from the scratchpad var msg = context.scratchpad.important_msg; //msg now equals "scratch me", that was set in the run script activity 

 //add or modify a scratchpad value context.scratchpad.status = "completed"; //we need to save the context record to save the scratchpad context.update(); } 

 Assign a catalog item to a group based on a delivery plan task 

 Assign a service catalog item to the database group if it uses a delivery plan that has a catalog task that is assigned to the desktop group. 

 Prerequisites 

 Role required: admin 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

 Name: Assign Catalog Item to Group Based on Delivery Plan Task. 

 Type: Assignment Rule. 

 Description: This assignment rule assigns a service catalog item to the database group if it uses a delivery plan that has a catalog task assigned to the desktop group. 

 Script: 

 //Return catalog items that have no group but do have a delivery plan assigned var ri = new GlideRecord ( "sc_cat_item" ) ; ri.addQuery("group", "=", null); ri.addQuery("delivery_plan", "!=", null); ri.query(); while(ri.next()) { gs.log("Found an item"); //Return tasks that point to the same delivery plan as the above item var dptask = new GlideRecord("sc_cat_item_delivery_task"); dptask.addQuery("delivery_plan", "=", ri. delivery_plan); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 218 


 dptask.query(); while(dptask.next()) { gs.log("Found a task"); var gp = dptask.group.getDisplayValue(); gs.log(gp); //If the task is assigned to desktop, assign the item's group to desktop if (dptask.group.getDisplayValue() == "Desktop") { ri.group.setDisplayValue("Desktop"); gs.log("updating " + ri.getDisplayValue()); ri.update(); break; } } } 

 Calculating durations 

 Often you may need to provide users with a way to specify when a task or process is due. Using the DurationCalculator script include, you can calculate the due date using either a simple duration or relative duration. 

 Typically, setting a due date requires that you calculate work time rather than the total time. Only the part of the day when work is performed is considered when determining the due date. For example, a task is due in 10 hours, but is restricted to a business day schedule. If the work starts at 10am on Monday, it is due on Tuesday at 12pm as calculated below. 

 10am-5pm on Monday (6 hours) + 8am-12pm on Tuesday (4 hours) 

 For information on schedules, which you can use as inputs to DurationCalculator methods, see Creating and using schedules. 

 This script demonstrates how to use DurationCalculator to compute a due date. 

 /** * Demonstrate the use of DurationCalculator to compute a due date. * * You must have a start date and a duration. Then you can compute a * due date using the constraints of a schedule. */ 

 gs.include('DurationCalculator'); executeSample(); 

 /** * Function to house the sample script. */ function executeSample(){ 

 // First we need a DurationCalculator object.var dc =new DurationCalculator(); 

 // --------------No schedule examples -----------------

 // Simple computation of a due date without using a schedule. Seconds// are added to the start date continuously to get to a due date. dc.setStartDateTime("5/1/2012"); if (!dc.calcDuration( 2 * 24 * 3600 )){// 2 days gs.log("*** Error calculating duration"); return ;} gs.log("calcDuration no schedule: "+ dc.getEndDateTime());// "2012-05-03 00:00:00" two days later 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 219 


 // Start in the middle of the night (2:00 am) and compute a due date 1 hour in the future// Without a schedule this yields 3:00 am. dc.setStartDateTime("5/3/2012 02:00:00"); if (!dc.calcDuration( 3600 )){ gs.log("*** Error calculating duration"); return ;} gs.log("Middle of night + 1 hour (no schedule): "+ dc.getEndDateTime());// No scheduled start date, just add 1 hour 

 // -------------Add a schedule to the date calculator --------------------addSchedule(dc); 

 // Start in the middle of the night and compute a due date 1 hour in the future.// Since we start at 2:00 am the computation adds the 1 hour from the start// of the day, 8:00am to get to 9:00am dc.setStartDateTime("5/3/2012 02:00:00"); if (!dc.calcDuration( 3600 )){// gs.log("*** Error calculating duration"); return ;} gs.log("Middle of night + 1 hour (with 8-5 schedule): "+ dc.getEndDateTime());// 9:00 am 

 // Start in the afternoon and add hours beyond quiting time. Our schedule says the work day// ends at 5:00pm, if the duration extends beyond that, we roll over to the next work day.// In this example we are adding 4 hours to 3:00pm which gives us 10:00 am the next day. dc.setStartDateTime("5/3/2012 15:00:00"); if (!dc.calcDuration( 4 * 3600 )){// gs.log("*** Error calculating duration"); return ;} gs.log("Afternoon + 4 hour (with 8-5 schedule): "+ dc.getEndDateTime());// 10:00 am. 

 // This is a demo of adding 2 hours repeatedly and examine the result. This// is a good way to visualize the result of a due date calculation. dc.setStartDateTime("5/3/2012 15:00:00");// for(var i=2; i<24; i+=1){if(!dc.calcDuration(i*3600)){// gs.log("*** Error calculating duration"); return ;} gs.log("add "+ i +" hours gives due date: "+ dc.getEndDateTime());} 

 // Setting the timezone causes the schedule to be interpreted in the specified timezone.// Run the same code as above with different timezone. Note that the 8 to 5 workday is// offset by the two hours as specified in our timezone. dc.setTimeZone("GMT-2"); dc.setStartDateTime("5/3/2012 15:00:00"); for ( var i= 2 ; i< 24 ; i+= 1 ){ if (!dc.calcDuration(i* 3600 )){// gs.log("*** Error calculating duration"); return ;} gs.log("add "+ i +" hours gives due date (GMT-2): "+ dc.getEndDateTime());}} 

 /** * Add a specific schedule to the DurationCalculator object. * * @param durationCalculator An instance of DurationCalculator */ function addSchedule(durationCalculator){// Load the "8-5 weekdays excluding holidays" schedule into our duration calculator.var scheduleName ="8-5 weekdays excluding holidays";var grSched =new GlideRecord('cmn_schedule'); grSched.addQuery('name', scheduleName); grSched.query(); if (!grSched.next()){ 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 220 


 gs.log('*** Could not find schedule "'+ scheduleName +'"'); return ;} 

 durationCalculator.setSchedule(grSched.getUniqueValue(),"GMT");} 

 Simple duration vs relative duration 

 How much work is required to complete a task can be expressed as a "relative duration". 

 Relative duration determines the expected due date and time relative to the starting time. Examples of relative durations include "Next business day by 4pm", or "2 business days by 10:30am". 

 To calculate a relative duration, the calendar and time zone must be considered to determine what "next business day" means since it is the calendar that defines which days are valid work days and the time zone will affect the result as well. As an example, consider "Next business day by 4pm": 

**-** If it is Monday at 12pm: Next business day by 4pm => Tuesday at 4pm 

**-** If it is Friday at 2pm: Next business day by 4pm => the following Monday at 4pm 

##### Note: Next business day is often defined by a starting day and time. For example, "next 

 business day at 4pm if before 2pm" indicates that if the current time is after 2pm on a business day, then "Next business day" really means 2 business days since today does not count. 

 For more information on relative durations, see Define a relative duration. 

 Calculating a simple duration 

 This business rule and script example demonstrate how to calculate a simple duration. 

 var dur =new DurationCalculator(); dur.setSchedule(current.schedule); dur.setStartDateTime(""); 

 if(current.duration_type==""){ 

 dur.calcDuration(current.duration.getGlideObject().getNumericVa lue()/1000);}else{ dur.calcRelativeDuration(current.duration_type);} 

 current.end_date_time= dur.getEndDateTime(); current.work_seconds= dur.getSeconds(); 

 This script demonstrates how to use DurationCalculator to calculate a simple duration. 

 /** * Sample script demonstrating use of DurationCalculator to compute simple durations * */ 

 gs.include('DurationCalculator'); executeSample(); 

 /** * Function to house the sample script. */ 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 221 


 function executeSample(){ 

 // First we need a DurationCalculator object. var dc =new DurationCalculator(); 

 // Compute a simple duration without any schedule. The arguments // can also be of type GlideDateTime, such as fields from a GlideRecord. var dur = dc.calcScheduleDuration("5/1/2012","5/2/2012"); gs.log("calcScheduleDuration no schedule: "+ dur); // 86400 seconds (24 hours) 

 // The above sample is useful in limited cases. We almost always want to // use some schedule in a duration computation, let's load a schedule. addSchedule(dc); 

 // Compute a duration using the schedule. The schedule // specifies a nine hour work day. The output of this is 32400 seconds, or // a nine hour span. dur = dc.calcScheduleDuration("5/23/2012 12:00","5/24/2012 12:00"); gs.log("calcScheduleDuration with schedule: "+ dur); // 32400 seconds (9 hours) 

 // Compute a duration that spans a weekend and holiday. Even though this // spans three days, it only spans 9 work hours based on the schedule. dur = dc.calcScheduleDuration("5/25/2012 12:00","5/29/2012 12:00"); gs.log("calcScheduleDuration with schedule spaning holiday: "+ dur); // 32400 seconds (9 hours) 

 // Use the current date time in a calculation. The output of this is // dependent on when you run it. var now =new Date(); dur = dc.calcScheduleDuration("5/15/2012",new GlideDateTime()); gs.log("calcScheduleDuration with schedule to now: "+ dur); // Different on every run.} 

 /** * Add a specific schedule to the DurationCalculator object. * * @param durationCalculator An instance of DurationCalculator */ function addSchedule(durationCalculator){ // Load the "8-5 weekdays excluding holidays" schedule into our duration calculator. var scheduleName ="8-5 weekdays excluding holidays"; var grSched =new GlideRecord('cmn_schedule'); 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 222 


 grSched.addQuery('name', scheduleName); grSched.query();if(!grSched.next()){ gs.log('*** Could not find schedule "'+ scheduleName +'"'); return;} durationCalculator.setSchedule(grSched.getUniqueValue());} 

 Calculating a relative duration 

 An example of a relative duration calculation script. 

 This script calculates the relative duration for "Next day at 4pm if after 10am": 

 // Next day at 4pm if before 10am var days =1; if(calculator.isAfter(calculator.startDateTime,"10:00:00")) days++; 

 calculator.calcRelativeDueDate(calculator.startDateTime, days,"16:00:00"); 

 This script demonstrates how to use DurationCalculator to calculate a relative duration. 

 /** * Sample use of relative duration calculation. * */ 

 gs.include('DurationCalculator'); executeSample(); 

 /** * Function to house the sample script. */ function executeSample(){ 

 // First we need a DurationCalculator object. We will also use // the out-of-box relative duration "2 bus days by 4pm" var dc =new DurationCalculator(); var relDur ="3bf802c20a0a0b52008e2859cd8abcf2"; // 2 bus days by 4pm if before 10am addSchedule(dc); 

 // Since our start date is before 10:00am our result is two days from // now at 4:00pm. dc.setStartDateTime("5/1/2012 09:00:00"); if(!dc.calcRelativeDuration(relDur)){ gs.log("*** calcRelativeDuration failed"); return;} gs.log("Two days later 4:00pm: "+ dc.getEndDateTime()); 

 // Since our start date is after 10:00am our result is three days from // now at 4:00pm. dc.setStartDateTime("5/1/2012 11:00:00"); if(!dc.calcRelativeDuration(relDur)){ 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 223 


 gs.log("*** calcRelativeDuration failed"); return;} gs.log("Three days later 4:00pm: "+ dc.getEndDateTime());} 

 /** * Add a specific schedule to the DurationCalculator object. * * @param durationCalculator An instance of DurationCalculator */ function addSchedule(durationCalculator){ // Load the "8-5 weekdays excluding holidays" schedule into our duration calculator. var scheduleName ="8-5 weekdays excluding holidays"; var grSched =new GlideRecord('cmn_schedule'); grSched.addQuery('name', scheduleName); grSched.query(); if(!grSched.next()){ gs.log('*** Could not find schedule "'+ scheduleName +'"'); return;} 

 durationCalculator.setSchedule(grSched.getUniqueValue(),"GMT" );} 

 How to implement a relative duration 

 You can implement a relative duration by creating the cmn_relative_duration table and the 

###### DurationCalculator script include. 

###### Before you begin 

 Role required: admin 

###### Procedure 

**1.** Create the cmn_relative_duration table. 

**2.** Create the DurationCalculator script include. 

**3.** Create a sample relative duration entry (for example, "Next business day by 4pm"). 

**4.** Add the needed fields to SLA tables to support relative durations. 

**5.** Modify duration calculation for SLAs. 

**6.** Modify SLA Percentage timer calculation for SLAs (this must use work_seconds). 

**7.** Add schedule fields to the Workflow: Schedule and Timezone (selected based on the field     from workflow table). 

**8.** Add duration support fields to the Workflow Task activity. 

**9.** Implement duration calculation script for the task activity. 

 The relative duration table and the DurationCalculator methods 

 The cmn_relative_duration table supports the definition of a due date as either a duration of time or a relative duration. 

 This table consists of two fields: "name" and "script." The "script" field contains the relative duration calculation script. This script includes the "calculator" variable, which is used to calculate the due date. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 224 


 The DurationCalculator script include can be used to perform the duration calculations. The following are methods that are available in this script include. 

 DurationCalculator script include table 

 Method Description 

 setSchedule(String schedID, [String timezone]) 

 Sets the schedule and time zone to be used for calculating the due date. 

 setStartDateTime(GlideDateTime start) 

 Sets the start time for the duration calculations. If 'start' is blank, uses current date/time. 

 calcDuration(int seconds) Calculates the end date and time. Upon completion the this.endDateTime and this.seconds properties will be set to indicate the results of the calculation. 

 calcRelativeDuration(String relativeDurationID) 

 Calculates the duration using the specified relative duration script. Upon completion the this.endDateTime and this.seconds properties will be set to indicate the results of the calculation. 

 getEndDateTime() Gets the this.endDateTime property that was set by calcDuration/calcRelativeDuration indicating the end date and time for the duration. 

 getSeconds() Gets the this.seconds property that was set by calcDuration/ calcRelativeDuration indicating the total number of seconds of work to be performed for the duration. 

##### Note: This is the total work time, not the total time 

 between start and end times and may be used to determine percentages of the work time 

 getTotalSeconds() Gets the this.totalSeconds property that was set by calcDuration/calcRelativeDuration indicating the total number of seconds between the start and end times of the duration. 

 The following functions are used in relative duration scripts: 

 Relative duration script functions 

 Function Description 

 boolean isAfter(GlideDateTime dt, String time) 

 Is 'time' of day after the time of day specified by 'dt'? dt, if blank, uses current date/time. time is in "hh:mm:ss" in 24-hour format. 

 calcRelativeDueDate(GlideDateTime start, int days, String endTime) 

 Calculates the due date starting at 'start' and adding 'days' using the schedule and time zone. When we find the day that the work is due on, set the time to 'endTime' of that day. Upon completion, this.endDateTime and this.seconds properties will be set to indicate the results of the calculation. If endTime is blank, use end of the ending work day. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 225 


 Get a user object 

###### In a business rule or other server script, the gs.getUser() method returns a user object. The 

 user object is an internal representation of the currently logged in user and provides information about the user and various utility functions. 

###### About this task 

 For a list and description of the available scoped methods for the user object, see GlideUser. 

###### Procedure 

**1.** Retrieve the current user. 

 var myUserObject = gs.getUser() 

###### 2. Use the getUserByID method to fetch a different user using the user_name field or 

 sys_id on the target record. For example: 

 var ourUser = gs.getUser(); gs.print(ourUser.getFirstName()); //print the first name of the user you are currently logged in as newUser = ourUser.getUserByID(<user_sys_id>); //fetch a different user, using the sys_id of the target user record. gs.print(newUser.getFirstName()); //first name of the user you fetched above gs.print(newUser.isMemberOf('Capacity Mgmt')); 

 Log output 

###### GSLog is a script include that simplifies script logging and debugging by implementing levels of 

 log output, selectable by per-caller identified sys_properties values. 

##### Log level 

 Logs can be at the level of debug, info, notice, warning, err, or crit (after BSD syslog.h and followers). The default logging level is notice, so levels should be chosen accordingly. 

##### Where to use 

 Use for any server-side script where you want to implement event logging. 

 For the API reference, see GSLog(). 

 For more information, see Debugging scripts 

 Modify a GlideDateTime field value 

###### This example demonstrates how to modify a GlideDateTime field value using a server-side 

 script. 

###### Given a GlideDateTime field or script object, show a variety of ways to easily modify value. 

###### The same concept also applies to the GlideDate object. 

##### Note: The following script is only intended for global applications. 

 //You first need a GlideDateTime object //this can be from instantiating a new object "var gdt = new GlideDateTime()" 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 226 


 //or getting the object from a GlideDateTime field //getting the field value (for example: var gdt = current.start_date) only returns the string value, not the object //to get the object use var gdt = current.start_date.getGlideObject(); //now gdt is a GlideDateTime object var gdt = current.start_date.getGlideObject(); 

 //All methods can use negative values to subtract intervals 

 //add 1 hour (60 mins * 60 secs) gdt.addSeconds(3600); 

 //add 1 day gdt.addDaysLocalTime(1); 

 //subtract 1 day gdt.addDaysLocalTime(-1); 

 //add 3 weeks gdt.addWeeksLocalTime(3); 

 //subtract 6 months gdt.addMonthsLocalTime(-6); 

 //add 1 year, representing the date and time using the UTC timezone instead of the local user's timezone. gdt.addYearsUTC(1); 

 //set the value of the GlideDateTime object to the current session timezone/format GlideSession.get().setTimeZoneName('US/Eastern'); gdt.setDisplayValue('2018-2-28 00:00:00'); gs.info('In ' + GlideSession.get().getTimeZoneName() + ": " + gdt.getDisplayValue()); 

 See also: 

**-** GlideDateTime 

**-** GlideDate - Global 

**-** GlideDate - Scoped 

**-** GlideDateTime - Global 

**-** GlideDateTime - Scoped 

**-** GlideTime - Scoped 

 Using custom queues to process events 

 You can use custom queues for applications that create a large volume of events or events that take a long time to process. This task shows how to create a custom queue, its monitoring process, and use a script to send events to the queue. 

###### Before you begin 

 Role required: admin 

##### Note: This information is for advanced users who understand event processing. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 227 


###### Procedure 

**1.** Navigate to **System Policy** > **Events** > **Registry**. 

**2.** Select the event for which you want to create a custom queue.     The **Event Registration** form displays. 

**3.** Populate the **Queue** field for the event in the Event Registry.     Use only lowercase letters, no spaces, and no special characters except underscore (_). 

**4.** Click **Submit**.     A new event is listed in the Events [sysevent] table. 

 In the following example, when the employeeOccasion event is generated, the event is added to my_queue. The events are stuck in the queue. To resolve this issue, create a process to watch the queue for 

 events. 

**5.** Navigate to **System Scheduler** > **Scheduled Jobs** > **Scheduled Jobs** and open the scheduled     job named **text index events process**. 

**6.** Click the additional actions menu icon )--> and select **Insert and Stay** to create a copy of     **text index events process**. 

##### Important: Be sure to copy the job and not overwrite the text index events process 

 Scheduled Job. 

**7.** In the copied schedule item, change the value in the **Name** field. 

###### 8. In the Job context field, replace the value for the GlideEventManager() parameter with 

 the name of the new queue. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 228 


 The queue monitoring process looks for and processes events in the example my_queue event queue. 

###### 9. Use the gs.eventQueue() method's fifth parameter to send events to the custom queue. 

 The following code shows how to send an event to the my_queue custom queue. 

 gs.eventQueue('x_60157_employee_spe.employeeOccasion', todaysOccasions, todaysOccasions.number, todaysOccasions.u_employee.name, 'my_queue'); 

##### Note: If an event is in the Event Registry and no queue name is provided to 

###### gs.eventQueue, the queue from the Event Registry is still assigned to the event. For 

 example, gs.eventQueue('x_60157_employee_spe.employeeOccasion') still associates the event with my_queue. If the queue name is provided in the gs.eventQueue() call, the queue takes priority. 

 You can verify that the event called was processed by checking the Events [sysevent] table. 

 Related topics 

 GlideEventManager process() 

 GlideSystem eventQueue() 

 Validation script use case Date and time 

 To validate the input of all date/time fields, you can use the following in a validation script ( System Definition > Validation Scripts ). 

 Because the date/time format is hard-coded in this script, it must match your instance's date/ time format. If your instance's date/time format changes, you must update your validation script. 

 Set the validation script's type to "glide_date_time". Then, with this validation script, if a user enters an incorrect format in a date/time field, they will receive an error message. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 229 


 function validate (value){ if (!value) { return true; } 

 return (getDateFromFormat(value, 'yyyy-MM-dd HH:mm:ss') != 0); } 

 For a comprehensive use case, see Restricting record access. 

##### Creating custom UI Pages and UI macros 

 Use UI pages to create custom pages for an application and UI macros for custom controls or interfaces. 

 Every UI Page is a Jelly template. Jelly turns XML into executable code. A UI Page works similar to how an index.html file is used in an AngularJS application. Jelly tags in the HTML field of the UI Page form contain AngularJS logic. 

 Creating UI macros requires knowledge of Jelly script. Review the existing UI macros for examples and suggested approaches. Those who want to build custom interfaces with JavaScript technologies should consider Service Portal as an alternative. 

 UI pages 

 UI pages can be used to create and display forms, dialogs, lists, and other UI components. 

 Use UI pages as widgets on dashboards. To find the UI pages, navigate to System UI > UI Pages. 

 This functionality requires a knowledge of HTML or Jelly. You can also create simple AngularJS applications using UI pages. 

 The UI page form contains the following fields: 

 UI page 

 Field Description 

 Name Name used to invoke the page via a URL (must not contain spaces). 

 Application Displays the current application scope. 

 Description The description of the UI page and what it’s used for. 

 Direct Select this check box for a direct UI page [sys_ui_page]. A direct UI page doesn't include the common HTML, CSS, and scripts. This setting requires adding custom CSS and JavaScript to use in the page. 

 HTML Main component of the page where you define what is rendered when the page is shown. It can contain either static XHTML, dynamically generated content defined as Jelly, or call script includes and UI Macros. 

##### Note: If GlideRecord/GlideDBQuery is used instead of 

###### GlideRecordSecure, a security recommendation message displays. 

 Client Script 

 Include client-side JavaScript that runs in the browser, such as functions called by buttons. It’s intended to handle any client-side processing needed, like setting focus to a field or other interactive DHTML features after a page is loaded. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 230 


 UI page (continued) 

 Field Description 

###### Client scripts for the UI page are deployed to the browser within a <script/ 

###### > tag, so the content can similarly be defined within the HTML field. The Client 

 Script field can be used instead to define these scripts concisely to maintain the Jelly and HTML manageability. 

 Processing Script 

 Script that runs on the server when the page is submitted. This is useful if your page has a form defined with the <g:ui_form/> or <g:form/> tags. 

##### Note: If GlideRecord/GlideDBQuery is used instead of 

###### GlideRecordSecure, a security recommendation message displays. 

 obsoletecustomprocessors 

##### Note: This feature is deprecated. While legacy, existing custom processors 

 continue to be supported, creating new custom processors has been deprecated. Instead, use the Scripted REST APIs. 

###### Related lists on the form view: 

 Access Controls 

 View and configure access controls for the UI page. See Use access controls on UI pages for more information. 

 Versions Shows all versions of the UI page. Use this list to compare versions or to revert to a previous version. 

##### Access control 

 You can secure a UI page by creating an ACL with the following parameters: 

**- Type** : ui_page 

**- Operation** : read 

**- Name** : Name of the UI page to protect 

**- Role** : User role that is allowed to access the record 

 When saving a new UI page, you are prompted to assign a role for access 

 control. 

##### Note: An entry with the same name as the UI page is created in the Access Control table. 

 For details on creating an ACL rule, see Create an ACL rule. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 231 


##### High risk UI pages 

 UI pages are considered high risk with any of the following attributes: 

**-** Uses GlideRecord or GlideDBQuery instead of GlideRecordSecure. 

##### Note: This is applicable for HTML and Processing script fields and not Client 

 scripts. 

**-** Doesn't have a corresponding ACL configured. 

**-** Indicates to be a public UI page and is entered in the sys_public record. 

**-** Shows a message to indicate high risk UI page. 

**-** For instances with glide.installation.developer is set to **true**. 

**-** If resource is customized content for a customer instance. 

 UI page access 

 Each UI page has a URL computed from the application scope, page name, and the .do file extension. 

 For example, to display the page called glidewindow_example on the demo system, you would navigate to https://<instance name>.service-now.com/ glidewindow_example.do. If the page was part of a custom application called example_app, you would instead navigate to https://<instance name>.servicenow.com/x_example_app_glidewindow_example.do. 

 You can also add additional parameters to a URL that can be accessed within a page's HTML section as jelly variables. That is, appending arguments to the URL as follows: / 

###### my_test_page.do?sysparm_verbose=true creates jelly variables called verbose that 

 can be accessed as follows: 

 <j2:if test="$[!empty(sysparm_verbose)]"> <span>show extra stuff </span> </j2:if > 

 A common practical example of this might be retrieving a database record for display. To build a list of a user's roles, pass in a parameter with the user's sys_id. Invoke the following UI page to display a list of roles for that user with Jelly code: 

 role_select.do?sysparm_user=5137153cc611227c000bbd1bd8cd2007 

 <j:set var = "jvar_user_id" value = "${sysparm_user}" /> 

 <g:evaluate> var userRoles = new GlideRecord('sys_user_has_role'); userRoles.addQuery('user','${jvar_user_id}'); userRoles.query(); </g:evaluate> 

 <select id='select_role'> <j:while test = "${userRoles.next()}"> <option value = "${userRoles.sys_id}"> ${userRoles.role.name} </option> </j:while> </select> 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 232 


 An exception to be careful of, though, is the reserved variable name sys_id. This variable always contains the ID of the UI page itself, regardless of what is specified in the URL. A common substitute variable name is sysparm_id. 

 Do not use URL parameters to load client scripts in UI pages. The system no longer evaluates scripts that are passed by URL parameter. If your implementation depends on this behavior, you can add the system property [glide.security.disable_ui_pages_sysparm_client_script] and set it to false to temporarily allow the evaluation of URL parameters passing scripts in UI pages. 

 Use access controls on UI pages 

 See access controls directly from the UI Page form and add role-based access control when creating or editing a UI Page record. 

###### Before you begin 

 Access controls that have been added to an existing UI page can be accessed and edited by opening the UI page record under related links. 

 Role required: security_admin and admin 

###### Procedure 

**1.** Elevate to the **security_admin** role.     For details on role elevation, see Elevate to a privileged role. 

**2.** Navigate to **All** > **System UI** > **UI Pages**. 

**3.** Select **New**. 

**4.** Complete the form.     See UI pages for additional information for UI field descriptions. 

**5.** Select **Submit** or **Save**.     A modal displays prompting you to create a role-based access control for the UI 

 page. 

**6.** Select a role. 

**7.** Select **OK** to assign the role.     You are returned to the UI pages list. 

 Add, edit, or view access controls for an existing UI page: 

**8.** Open a UI page from the UI pages table. 

**9.** View the **Access Controls** under the related lists. 

**10.** Select **New** to create a new access control or select an existing entry for editing.     The Access Control form loads. UI Page details are displayed. 

**11.** Complete the form and assign a role to the UI page.     For additional information on access control, see Create an ACL rule. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 233 


**12.** Select **Submit** for a new access control or **Update** for edits. 

##### Note: There can be multiple access controls per UI page. 

 Secure UI pages 

 Access controls and related security messages are integrated on high risk UI Pages for increased security. 

 An informational message displays on high risk UI pages to inform the customer to add a rolebased Access Control to the UI page. 

 The message displays under the following conditions: 

**-** If an ACL (access control list) is missing 

**-** If GlideRecord/GlideDBQuery is used instead of 

###### GlideRecordSecure in either the HTML or Processing script 

 sections 

**-** If the UI page is configured as public in sys_public 

##### Note: Public UI Pages that are public or that use GlideRecord don’t show a missing 

 ACL warning. 

 See UI pages for details on high risk UI pages. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 234 


##### Conditions that display the security recommendations message 

 The message displays under the following conditions: 

**-** All internal instances eclipse/IJ where glide.installation.developer= true. 

**-** All customer scoped UI Page resources. 

**-** Any customized UI Page when the 

###### glide.script.ui_page.customer_scoped.security_msgs_enabled property 

###### is set to true. (The default value is true). 

##### Conditions that don’t display the security recommendations message 

 The message won’t display under the following conditions: 

**-** UI Page is public. 

**-** UI Page is in the **Global** scope. 

**-** The glide.script.ui_page.customer_scoped.security_msgs_enabled is 

###### set to false. 

##### Note: To disable the role-based ACL creation prompt, set the 

###### glide.ui_page.enable_acl_create_ux property to false. The property is set to 

 true by default. 

 UI page process scripts 

###### If your UI page contains a form (uses the <g:form> tag), you can submit the form and have the 

 process script run. 

 The processing script can naturally access fields on the form. For example, if your form contained 

###### the application_sys_id field: 

 <g:ui_form> <p>Click OK to run the processing script.</p> <g:dialog_buttons_ok_cancel ok="return true" /> <input type="hidden" name="application_sys_id" value="499836460a0a0b1700003e7ad950b5da" /> </g:ui_form> 

###### You can access the field using application_sys_id: 

 var application = new GlideRecord('hr_application'); application.get(application_sys_id); application.status = "Rejected"; application.update(); var urlOnStack = GlideSession.get().getStack().bottom(); response.sendRedirect(urlOnStack); 

##### Important: The preceding script is usable only with Global applications. 

 If you are using the UI page for a dialog, you can also reference the most recent URL on the stack using the code above and then send the response to that location. This is useful if you want to have the dialog's processing script update something and then redisplay the screen that brought up the dialog. 

 UI macros 

 UI macros are discrete scripted components administrators can add to the user interface. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 235 


 UI macros are typically controls that provide inputs or information not provided by existing field types. By default, the system provides UI macros for a variety of user interface elements such as: 

**-** All formatters 

**-** The Service Catalog cart 

**-** The action icons next to fields 

**-** The action icons on forms and lists 

**-** The widgets of a content management system 

**-** The Orchestration activity designer 

 Administrators can create their own UI macros to provide custom controls or interfaces. Creating UI macros requires knowledge of Jelly script. Review the existing UI macros for examples and suggested approaches. Those who want to build custom interfaces with JavaScript technologies should consider Service Portal as an alternative. 

##### Note: To view available UI macros, navigate to All > System UI > UI Macros. 

 UI macro basics 

 UI macros can be used to build solutions that can’t be built using the available catalog variable types. 

##### Accessible UI macros 

 Several UI macros are available in the UI macros [ui_macros] table. These UI macros have names starting with ui_ and emulate the behavior of a subset of standard form field types for use in UI pages. For example, the ui_date_time UI macro can act like a glide_date_time field in a UI page, providing a type-able input field with a date/time selector. 

 A UI macro can be included in a UI page with the <g:> Jelly tag. The following example includes the ui_date_time UI Macro, providing two optional attributes to the UI Macro: 

 <g:ui_date_time name="due_date" value="2023-11-24 08:30:00" onchange="checkDateValue()" /> 

 The attribute values in the <g:> Jelly tag are provided to the UI macro as jvar-prefixed variables. The UI macro can use the jvar-prefixed variables in its XML. 

 Jelly tag attributes used as jvar-prefixed variables 

 Attributes jvar-prefixed variables 

 name jvar_name 

 value jvar_value 

 onchange jvar_onchange 

##### Note: These UI macros aren’t intended to support all features of their corresponding form 

 field type. In many cases, the macros are only intended for specific ServiceNow application use cases. 

 The ui_-prefixed UI macros include descriptions specifying supported attributes that can (or must) be provided in the UI page's <g:> Jelly tag. To view available UI macros, navigate to All > System UI > UI macros. 

 / 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 236 


##### Custom UI macros 

 The ui_example UI macro uses three jvar-prefixed variables: jvar_name, jvar_test_attribute and jvar_laptop_type. These variables can be provided to the UI macro as name, test_attribute and laptop_type attributes in a <g:> Jelly tag in a UI page. 

 Creating the ui_example UI macro 

 Navigate to All > System UI > UI Macros and select New. 

 Name the macro ui_example and add the following script to the XML field: 

 <?xml version="1.0" encoding="utf-8" ?> <j:jelly trim="true" xmlns:j="jelly:core" xmlns:g="glide"> <div>name jvar: ${jvar_name}</div> <div>test_attribute jvar: ${jvar_test_attribute}</div> <div>laptop_type jvar: ${jvar_laptop_type}</div> </j:jelly> 

 Using the macro in a UI page 

 Navigate to All > System UI > UI Pages and select New. You will be asked to select an administrator role. 

 Name the UI page and add the following script to the HTML field: 

 <?xml version="1.0" encoding="utf-8" ?> <j:jelly trim="false" xmlns:j="jelly:core" xmlns:g="glide" xmlns:j2="null" xmlns:g2="null"> <div style="text-decoration:underline">Template include one:</div> <g:ui_example name="Fred Luddy" test_attribute="I am an attribute" laptop_type="ThinkPad" /> <hr/> <div style="text-decoration:underline">Template include two:</div> <g:ui_example name="Pat Casey" test_attribute="I am a different attribute" laptop_type="Macbook Pro" /> </j:jelly> 

 Checking output 

 In the UI page, you can click Try It to view the results. 

##### Note: If you create a macro and it doesn’t display as expected in the UI page, clearing 

 the cache might help. To clear the cache of your instance, in your browser, enter <server_url>/cache.do. 

 Related topics 

 UI pages 

 Jelly tags 

 <g:ui_form/> 

 <g:ui_input_field /> 

 <g:ui_checkbox/> 

 Calling UI macros 

 Administrators can call UI macros from certain record types associated with the user interface. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 237 


 Calling UI macros by record type 

 Record type 

 Example 

 Dictionary attribute Display an icon for a reference field: 

 ref_contributions=ui_macro_name 

 UI page Display something on a UI page: 

 <g:macro_invoke macro="ui_macro_name" /> 

 UI macro Call a UI macro from another UI macro: 

 <?xml version= "1.0" encoding="utf-8"&nbsp;?> <j:jelly trim= "false" xmlns:j="jelly:core" xmlns:g="glide" xmlns:j2="null" xmlns:g2="null"> <g:ui_macro_name /> <g:ui_macro_name_2 /> </j:jelly> 

 UI macro form 

 Each UI macro record consists of a name and an XML document written in Jelly code. 

 UI macro fields 

 Field Description 

 Name A unique and descriptive name for this macro. 

 Active Select the check box to render the element as defined. Clear the check box to disable the element without deleting the code. For example, the email_reply macro is inactive by default. 

 Description Describe the purpose of the macro and parameters passed to it. 

 XML Jelly script that defines the macro. 

 Custom approval UI macro 

 This section describes how to create a custom approval UI macro. 

##### Warning: The customization described here was developed for use in specific instances, 

 and is not supported by Now Support. This method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum. 

 Script Name : Custom Approval UI Macro 

 Type : UI Macro 

 Description : Here is an option to get more detail out of the My Approvals view of an Execution Plan. This can be done by creating a new UI macro. Navigate to System UI and click UI Macros. First, you will need to rename the existing approval_summarizer_sc_task to something like approval_summarizer_sc_task_old and deactivate it. Then you will need to create 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 238 


 a new one using the same name (approval_summarizer_sc_task). The name should basically tell you what the macro does and what it applies to. In this case, we're replacing an existing one so we decided to re-use the existing name. 

 Approval macros 

 Then you should copy the xml script at the bottom of this article into the xml code window in the new UI macro. This is great way to give some detail to an approver when you are doing line item approvals via approval tasks within the Service Catalog Execution Plans. 

##### The old way 

 This is the view you see in My Approvals when using an approval task via the old method. 

 My Approvals (old way) 

 Notice there is not much detail telling the approver what they are actually approving. You can see the short description of the task but not much around what the item is. 

##### The new way 

 This is the view you will see if you use the xml script below in place of the OOB (out-of-box) UI macro. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 239 


 My Approvals 

 Using this method you can see details much like the request approval. You have a link into the item ordered, a short description (which contains the ability to expand the variables from the item), price, quantity and the total price. This helps the approver in that it shows more detail. They can now see what they are actually approving. 

 Script: 

 <?xml version="1.0" encoding="utf-8" ?> <j:jelly trim="true" xmlns:j="jelly:core" xmlns:g="glide" xmlns:j2="null" xmlns:g2="null"> <tr> <td class="label_left" width="100%"> <label style="margin-left: 10px"> ${gs.getMessage('Summary of Item being approved')}: <input style="visibility: hidden" NAME="make_spacing_ok"></input> </label> </td> </tr> <g:evaluate var="jvar_ni" expression=" var sc_task = ${ref}.sysapproval; var sc_req_labels = new GlideRecord('sc_req_item'); sc_req_labels.initialize(); var sc_req_item = new GlideRecord('sc_req_item'); sc_req_item.addQuery('request_item', sc_task.request_item.sys_id); sc_req_item.query(); " /> <tr> <td width="100%"> <table width="100%"> <tr> <td class="label_left" width="150px"> <label style="margin-left: 10px"> 

 ${sc_task.request_item.request.opened_by.sys_meta.label}: </label> </td> <td> 

${sc_task.request_item.request.opened_by.getDisplayValue()} </td> </tr> <tr> © 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 240 


 <td class="label_left" width="150px"> <label style="margin-left: 10px"> 

 ${sc_task.request_item.request.requested_for.sys_meta.label}: </label> </td> <td> 

 ${sc_task.request_item.request.requested_for.getDisplayValue()} </td> </tr> <tr> <td class="label_left" width="150px"> <label style="margin-left: 10px">${gs.getMessage('Total')}:</label> </td> <td> <g:currency_format value="${sc_task.request_item.request.price}" /> </td> </tr> </table> </td> </tr> <j:set var="jvar_line_num" value="0" /> <tr> <td width="100%"> <table width="100%"> <tr class="header"> <td colspan="2"> ${sc_req_labels.number.sys_meta.label} </td> <td> 

 ${sc_req_labels.description.sys_meta.label} </td> <td> ${sc_req_labels.price.sys_meta.label} </td> <td> ${sc_req_labels.quantity.sys_meta.label} </td> <td> ${gs.getMessage('Total')} </td> </tr> <j:set var="jvar_item_price" value="${sc_task.request_item.price * sc_task.request_item.quantity}"/> <j:set var="jvar_overall_total" value="${jvar_overall_total + jvar_item_price}"/> <j:set var="jvar_line_color" value="odd"/> <j:set var="jvar_line_num" value="${jvar_line_num + 1}"/> <j:if test="${jvar_line_num % 2 == 0}"> <j:set var="jvar_line_color" value="even"/> </j:if> 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 241 


 <g:evaluate var="ni" expression=" var smart_description = sc_task.request_item.cat_item.short_description; if (smart_description == null || smart_description == '' || smart_description == 'undefined') smart_description = sc_task.request_item.cat_item.name; "/> <tr class="${jvar_line_color}"> <td valign="top"> <g2:evaluate var="jvar_pop_target" expression="$[ref].getRecordClassName()" /> <a class="linked" target="gsft_main" 

 href="sc_req_item.do?sys_id=${sc_task.request_item.sys_id}" onmousemove="popListDiv(event, 'sc_req_item', '${sc_task.request_item.sys_id}','${sysparm_view}')" onmouseout="lockPopup(event)"> <img src="images/icons/hover_icon.gifx" class="clsshort"/> </a> </td> <td valign="top"> <a class="linked" target="gsft_main" 

 href="sc_req_item.do?sys_id=${sc_task.request_item.sys_id}"> ${sc_task.request_item.number} </a> </td> <td valign="top" width="50%"> <g:call function="variable_summary_approval.xml" 

 question_name="${sc_task.request_item.sys_id}" 

 question_help_tag="${smart_description}" 

 sc_req_item="${sc_task.request_item.sys_id}" help_class="${jvar_line_color}"/> </td> <td valign="top"> <g:currency_format value="${sc_task.request_item.price}"/> </td> <td valign="top"> ${sc_task.request_item.quantity}</td> <td valign="top"> <g:currency_format value="${jvar_item_price}"/></td> </tr> </table> </td> </tr> </j:jelly> 

 Jelly tags 

 Use Jelly to turn XML into HTML. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 242 


 Watch these introductory videos to learn about using Jelly in the ServiceNow AI Platform. 

**-** Introducing Jelly Scripting - Part 1 (Video) 

**-** Introducing Jelly Scripting - Part 2 (Video) 

**-** Introducing Jelly Scripting - Part 3 (Video) 

##### Jelly Tags 

 if 

**-** Description: The if tag is just what it looks like, an if tag. This is like an if     statement in any programming language, but keep in mind that there is no     elseif tag and no else tag. If you want to create that kind of structure, try the     choose/when/otherwise syntax. 

**-** Parameters: test - The condition to evaluate in order to determine if the block     will execute. 

**-** Example: 

 <g:evaluate var="jvar_now_GR" object="true"> var now_GR = new GlideRecord("incident"); now_GR.addQuery("active", true); now_GR.query(); now_GR; </g:evaluate> 

 <j:if test="${!jvar_now_GR.hasNext()}"> We did not find any active incidents. </j:if> <j:if test="${jvar_now_GR.next()}"> We found ${jvar_now_GR.getRowCount()} active incidents. </j:if> 

 while 

**-** Description: The while tag does a while loop. 

**-** Parameters: test - The condition to evaluate in order to determine if the     statement will loop through. This should be an expression enclosed in ${} or     $[] that evaluates to true or false. 

**-** Example: 

 <g:evaluate var="jvar_now_GR" object="true"> var now_GR = new GlideRecord("incident"); now_GR.addQuery("active", true); now_GR.query(); now_GR; </g:evaluate> 

 <j:while test="${jvar_now_GR.next()}"> <a href="incident.do?sys_id=${jvar_now_GR.getValue('sys_ id')}">${jvar_now_GR.getValue('number')}</a> </j:while> 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 243 


 set 

**-** Description: The set tag sets a variable. 

**-** Parameters: 

 ◦ var The variable to set. Often the system prefixes these variables with jvar_ for consistency. 

 ◦ value The value to set var to. This is often an expression enclosed in ${} or $[]. 

 ◦ defaultValue If the value results to null or empty, this value is put into the var. 

**-** Example: 

 <j:set var="jvar_incident_number" value="${jvar_now_GR.getValue('number')}"/> 

 set_if 

**-** Description: The set_if tag sets a variable based on a test. This tag is similar     to the ternary operator in other programming languages (var = <test>?     <if_true> : <if_false>). 

**-** Parameters: 

 ◦ var The variable to set. Often the system prefixes these variables with jvar_ for consistency. 

 ◦ test The condition to evaluate in order to determine if the statement will evaluate the true value or the false value. This should be an expression enclosed in ${} or $[] that evaluates to true or false. 

 ◦ true The value to set the variable to if test evaluates to true. This parameter is optional, so if the field is blank, and if test evaluates to true, the variable is left blank. 

 ◦ false The value to set the variable to if test evaluates to false. This parameter is optional, so if the field is blank, and if test evaluates to false, the variable will be left blank. 

 choose 

**-** Description: The choose tag starts a choose block of code. This is similar to     the if-elseif-else kind of syntax in most programming languages. With a     choose tag, you can use when and otherwise tags to specify other blocks of     code. 

**-** Parameters: None 

**-** Example: 

 <j:choose> <j:when test="${jvar_now_GR.getRowCount() ${AMP}lt; 1}">We found multiple records!</j:when> <j:when test="${jvar_now_GR.next()}">We found record ${jvar_now_GR.getValue('number')}</j:when> <j:otherwise>Sorry, we could not find the record you specified.</j:otherwise> </j:choose> 

 when 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 244 


**-** Description: The when tag is used within a choose block to indicate a condition.     This tag is similar to an if or an elseif in that it specifies a condition, executes     the inner content, and then implies a break at the end to leave the if-elseif     construct. 

**-** Parameters: test - The condition to evaluate in order to determine if the     statement will loop through. This should be an expression enclosed in ${} or     $[] that evaluates to true or false. 

**-** Example: 

 <j:choose> <j:when test="${jvar_now_GR.getRowCount() ${AMP}lt; 1}">We found multiple records!</j:when> <j:when test="${jvar_now_GR.next()}">We found record ${jvar_now_GR.getValue('number')}</j:when> <j:otherwise>Sorry, we could not find the record you specified.</j:otherwise> </j:choose> 

 otherwise 

**-** Description: The otherwise tag is used within a choose/when/otherwise     block, and is like the else or default case. 

**-** Parameters: None 

**-** Example: 

 <j:choose> <j:when test="${jvar_now_GR.getRowCount() ${AMP}lt; 1}">We found multiple records!</j:when> <j:when test="${jvar_now_GR.next()}">We found record ${jvar_now_GR.getValue('number')}</j:when> <j:otherwise>Sorry, we could not find the record you specified.</j:otherwise> </j:choose> 

##### Glide Tags 

 evaluate 

**-** Description: The evaluate tag evaluates JavaScript code (server side), and     makes variables visible to future code. Unlike other tags, the evaluate tag     evaluates the content that is inside the tag as server side JavaScript. 

 The context is the same as that of script includes in the system. Other script 

###### includes, global business rules, GlideRecord, GlideSystem, and Jelly 

 variables (prefixed with jelly. if the parameter jelly="true" is set) are available. 

**-** Parameters: 

 ◦ var The name of the variable that will be set to the result of the script. 

 ◦ object If set to true, the result of the expression is treated as an object instead of a primitive variable (string or integer variable values). 

 ◦ jelly If set to true, allows Jelly context variables to be referenced in the script. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 245 


 ◦ expression This is an expression to be executed for the value to put in var. The expression can be either of two places. First, it can be an attribute on the evaluate tag itself. Otherwise, the content between the beginning tag and ending tag is the expression. The last line of the expression is the actual value passed into var. 

**-** Example: 

 <g:evaluate var="jvar_now_GR" object="true"> var now_GR = new GlideRecord("incident"); now_GR.addQuery("active", "true"); now_GR.query(); now_GR; // this is the variable put into the variable jvar_now_GR </g:evaluate> 

 <g:evaluate var="jvar_now_GR" object="true" expression=" var now_GR = new GlideRecord('incident'); now_GR.addQuery('active', 'true'); now_GR.query(); now_GR; // this is the variable put into the variable jvar_now_GR" /> 

 messages 

**-** Description: The messages tag helps with translation. When 

###### gs.getMessage() is called anywhere on a page, there are two possible 

 places where the translation is found. First, the page checks a local cache of translations. Second, the page makes an AJAX call to the server to find the translation. What g:messages does is allow pages to cache certain messages. 

**-** Parameters: None 

**-** Example: 

 <g:messages> Yes No Cancel </g:messages> 

 breakpoint 

**-** Description: When the breakpoint tag is called, it prints a list of all the     variables in Jelly at the current moment, with their respective values. If a variable     is specified, it prints the requested variable and its value. The output is placed in     the system log. 

**-** Parameters: var - (Optional) The variable to log the value for. If var is not     specified, then all variables are dumped into the log. 

**-** Example: 

 <g:breakpoint /> 

 <g:breakpoint var="sysparm_view"/> 

 no_escape 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 246 


**-** Description: The system, by default, uses escaped output as a security measure.     Output placed inside of no_escape tags is not escaped before output. Be     careful when using these tags, because if user input is displayed here it can open     a security vulnerability on the page. 

**-** Parameters: None 

**-** Example (phase 1) – Disables automatic output escaping of all contained ${}     expressions: 

 <g:no_escape> ${jvar_raw_html_data} </g:no_escape> 

**-** Example (phase 2) – Use NOESC to disable escaping for the specified string. This     implies the expression must evaluate to a string. 

 <g:no_escape>$[NOESC:jvar_expr]</g:no_escape> 

 For information on phase 1 and phase 2 evaluation, refer to the Jelly introduction videos listed at the beginning of this section. 

 macro_invoke 

**-** Description: The macro_invoke tag calls a UI macro that you have specified     in the database. You may also call a UI macro by specifying it in the tag name. For     example, if you had a UI macro named my_macro, you could call that macro with     the tag <g:my_macro/>. For information, see UI macros. 

**-** Parameters: 

 ◦ macro The name of the UI macro to execute. If your tag name is g:macro_invoke, then the macro attribute specifies the name of the macro. If the tag name includes the name of the macro, then there is no need to include a macro attribute. 

 ◦ Other attributes For each attribute you specify, a variable with that name will be available in the context of the UI macro, prefixed with jvar_. 

**-** Example: 

 <!-Will invoke the contents of the UI macro named "sample_macro", which will have the variable jvar_message available within it--> <g:macro_invoke macro="sample_macro" message="This is a sample macro variable." /> 

 <!-Will invoke the contents of the UI macro named "sample_macro", which will have the variable jvar_message available within it--> <g:sample_macro message="This is a sample macro variable." /> 

 if_polaris 

**-** Description: The if_polaris tag checks if Next Experience is enabled for     the current page. It must include at least one of the child tags <g:then /> or     g:else />. 

**-** Parameters: None 

**-** Example: 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 247 


 <g:if_polaris> <g:then><g:inline template="polaris_nav"/></g:then> <g:else><g:inline template="classic_nav"/></g:else> </g:if_polaris> 

 <g:if_polaris> <g:then><a href="…">Click here to see what’s new!</a></g:then> </g:if_polaris> 

 <g:if_polaris> <g:else>Core UI only code here!</g:else> </g:if_polaris> 

 then 

**-** Description: The then tag is used within an if_polaris block to set the page     content when Next Experience is enabled. 

**-** Parameters: None 

**-** Example: 

 <g:if_polaris> <g:then><g:inline template="polaris_nav"/></g:then> <g:else><g:inline template="classic_nav"/></g:else> </g:if_polaris> 

 <g:if_polaris> <g:then><a href="…">Click here to see what’s new!</a></g:then> </g:if_polaris> 

 <g:if_polaris> <g:else>Core UI only code here!</g:else> </g:if_polaris> 

 else 

**-** Description: The else tag is used within an if_polaris block to set the page     content when Next Experience isn't enabled. 

**-** Parameters: None 

**-** Example: 

 <g:if_polaris> <g:then><g:inline template="polaris_nav"/></g:then> <g:else><g:inline template="classic_nav"/></g:else> </g:if_polaris> 

 <g:if_polaris> 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 248 


 <g:then><a href="…">Click here to see what’s new!</a></g:then> </g:if_polaris> 

 <g:if_polaris> <g:else>Core UI only code here!</g:else> </g:if_polaris> 

 Jelly escaping types 

 You use different methods when escaping characters in JavaScript and HTML. JavaScript uses the backslash character, and HTML uses the ampersand character. 

##### Note: This functionality requires a knowledge of JavaScript, HTML, and Apache Jelly 

 (a Java and XML based scripting and processing engine for turning XML into executable code). 

 There are two different types of escaping that is required when generating output from Jelly: 

**-** JavaScript 

**-** HTML 

 The escaping for each of these consists of the following types. 

 Jelly escaping types 

 Type From To 

 JavaScript ' (single quote) \' 

 " (double quote) \" 

 CR (carriage return) 

 (blank) 

 NL (newline) \n ('\' followed by 'n') 

 HTML & (ampersand) &amp; 

 < (less than) &lt; 

 > (greater than) 

 &gt; 

 You can also escape HTML using the getHTMLValue() function which will enforce all line breaks and escape the characters mentioned above. It can be used as follows: 

 ${test.getHTMLValue()} 

 Add escaping to a Jelly replacement 

 You can handle character escaping in Jelly files. XML escaping behavior can be modified only by users with the security_admin role. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 249 


###### About this task 

##### Note: This functionality requires a knowledge of JavaScript, HTML, and Apache Jelly 

 (a Java and XML based scripting and processing engine for turning XML into executable code). 

###### Procedure 

 Add a prefix to the ${expression} or $[expression] indicating the escaping to be performed. 

 ${JS:expression} ${HTML:expression} 

 The prefix tells the system to take the result of the expression and escape it before outputting. The escaping may be combined by specifying a comma-separated list of prefixes: 

 ${JS,HTML:expression} 

 Extensions to Jelly syntax 

 Apache's Jelly syntax is used to render forms, lists, UI pages, and many other things rendered in ServiceNow. 

 With Jelly, logic can be embedded within static content and computed values may be inserted into the static content. 

##### Important: This functionality requires a knowledge of Apache Jelly (a Java and XML 

 based scripting and processing engine for turning XML into executable code). 

 This page from Apache has a summary of the standard Jelly tags: http://commons.apache.org/ jelly/tags.html 

 Namespaces 

 Jelly often includes multiple namespaces when invoking tags. 

 The "j" namespaces are standard Jelly whereas the "g" namespaces are unique to ServiceNow scripts. For example, the <g:evaluate> tag is supplied by ServiceNow to allow you to compute a value using JavaScript. The standard Jelly tag <j:test> is used to evaluate a condition. 

 Phases 

 Usually, there are two phases indicated by namespaces <j> versus <j2> and <g> versus <g2>. 

 The namespaces without the "2" happen in the first phase of processing and these are cached except when used in a UI page. Those with the "2" are never cached. Care must be taken when selecting whether to use phase 1 or phase 2 for efficiency and correct results. 

 In addition to the namespaces, the syntax used to insert values into static content differs depending on which phase is to supply the value. A dollar with braces surrounding a value inserts the value in phase 1. For example, ${jvar_ref} inserts the value jvar_ref during phase 1 of the jelly process. A dollar with brackets surrounding a value inserts the value in phase 2. For example, $[jvar_ref] inserts the value jvar_ref during phase 2. A value surrounded by quotes is treated as a string. For example, '[jvar_ref]' inserts the value jvar_ref as a string during phase 2. 

 <script> if (confirm("$[gs.getMessage('home.delete.confirm') ]")) 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 250 


 ... </script>

 <input type="hidden" id="${jvar_name}" name="${jvar_name}" value="${jvar_value}" class="${jvar_class}" />

If tests

You can use if statements in Jelly scripts.

Testing whether something is true or not can be done as follows:

<j:if test="${jvar_something}">...do something...</j:if> <j:if test="${!jvar_something}">...do something...</j:if>

The reason this statement works, is that, in Jelly, a term like jvar_something is "truthful" in an if tag if:

**1.** it is Boolean and true

**2.** it is a String and = "true", "yes", "on", or "1"

Testing whether something exists can be done as follows:

<j:if test="${empty(jvar_something)}">...do something...</j:if>

The reason this statement works is that the JEXL empty function returns true if its argument is:

**1.** null

**2.** an empty string

**3.** a zero length collection

**4.** a map with no keys

**5.** an empty array

##### Note: You cannot mix javascript and jvar variables in a JEXL expression. They must be

broken into separate expressions.

Set_If

Sets a variable to one of two different values depending on whether a test is true or false.

<g2:set_if var="jvar_style" test="$[gs.getPreference('table.compact') != 'false']" true="margin-top:0px; margin-bottom:0px;" false="margin-top:2px; margin-bottom:2px;" />

<g:insert> versus <g:inline> versus <g:call>

This page provides a comparative explanation of three tags: <g:insert>, <g:inline>, and <g:call>.

##### <g:insert>

The <g:insert> tag inserts a Jelly file into your Jelly in a new context. This means you cannot access the variables previously established in your Jelly.

<g:insert template="get_target_form_function.xml" />

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 251

##### <g:inline>

The <g:inline> tag inserts a Jelly file into your Jelly in the same context. This means that the inserted Jelly can access the variables you previously established and it can change the values of those variables.

<g:inline template="element_default.xml" />

##### <g:call>

For better encapsulation, the <g:call> tag may be used. Your function will only have access to the values passed to it. The Jelly context will look the same after a call as before the call. This means you cannot set a global variable here and read it later. This also means you can't mistakenly set a global variable called "jvar_temp" and overwrite a variable that somebody else was relying on.

Passing values, if needed, is done explicitly by including the name of the parameter on the <g:call> line followed by the equal sign followed by the value in quotes:

<g:call function="collapsing_image.xml" id="${jvar_section_id}" image="$[jvar_cimg]" first_section_id="${jvar_first_section_id}" image_alt="${jvar_cimg_alt}"/>

If values are passed, and you want to have defaults or required parameters, your Jelly referenced in the function must then include a line to declare whether the parameters are required or have a default value:

<g:function id="REQUIRED" image="REQUIRED" image_prefix="" image_alt="REQUIRED"/>

The example above indicates that 3 of the parameter are required and one parameter is option with a blank default value. Note that if you are not passing values or if you do want to have default or required values, you do not need to include the <g:function> line at all. In general, however, you will want to include a <g:function> line.

The value can then be referenced in your template by prepending the "jvar\_" prefix to the parameter's name:

 <img id="img.${jvar_id}" src="images/${jvar_image}" alt="${jvar_image_alt}" onclick="toggleSectionDisplay('${jvar_id}', '${jvar_image_prefix}','${jvar_first_section_id}');"/>

For <g:call>, parameters may also be pass implicitly as a list of named variables in an "arguments" parameter:

<g:call function="item_link_default.xml" arguments="sysparm_view,ref_parent,jvar_target_text"/>

As an alternative to passing variables into the function via separate tag arguments, it is possible to pass a list of variables in a single 'arguments' argument. All variables identified by name

###### (comma separated) in the argument parameter are re-introduced within the function under

the exact same name (e.g. inside the function template, we'd have variables sysparm_view, ref_parent, and jvar_target_text available to us).

The function template may return a value to the calling template using the return= attribute. Within the function the jvar_answer variable sets the return value.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 252

<g:call function="item_body_cell_calc_style.xml" arguments="jvar_type" return="jvar_style"/>

<g:evaluate>

The <g:evaluate> tag is used to evaluate an expression written in Rhino JavaScript and sometimes to set a variable to the value of the expression.

The last statement in the expression is the value the variable will contain.

<g2:evaluate var="jvar_page" jelly="true"> var page = ""; var pageTitle = ""; var pageGR = new GlideRecord("cmn_schedule_page"); pageGR.addQuery("type", jelly.jvar_type"); pageGR.query(); if (pageGR.next()) { page = pageGR.getValue("sys_id"); pageTitle = pageGR.getDisplayValue(); } page; </g2:evaluate>

<g2:evaluate var="not_important" expression="sc_req_item.popCurrent()"/>

##### object="true"

If you would like to have the evaluate return an object (for example an array), use the argument object="true".

<g2:evaluate object="true" var="jvar_items" expression="SncRelationships.getCMDBViews()" />

##### jelly="true"

If you would like to access Jelly variables inside an evaluate, include jelly="true" in the evaulate and add "jelly." before the Jelly variable's name. For example, to access the GlideJellyContext:

<g2:evaluate var="jvar_row_no" jelly="true"> var gf = jelly.context.getGlideForm(); var row = gf.getRowNumber(); row; </g2:evaluate>

Another example of accessing a jvar using the jelly="true" parameter. The value of jvar_h was set previously and we can access it inside the evaluate:

$[NLBR:jvar_h.getHTMLValue('newvalue')] <g2:evaluate var="jvar_fix_escaping" jelly="true"> var auditValue = jelly.jvar_h.getHTMLValue('newvalue'); gs.log("****\*\*\*\***** " + auditValue); </g2:evaluate>

##### copyToPhase2="true"

If you have a need to take the results of an evaluation that occurs in phase 1 and propagate it to phase 2, use copyToPhase2="true". There is some protection for escaping in this use. For example:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 253

<g:evaluate var="jvar_has_special_inc" copyToPhase2="true"> var specialInc = gs.tableExists("special_incident"); specialInc; </g:evaluate> $[jvar_has_special_inc]

If you do not need to evaluate something, you can do this more directly. Beware of escaping issues here (double quotes in jvar_rows would cause a problem in the example):

<j2:set var="jvar_rows" value="${jvar_rows}"/>

<g:breakpoint/>

This tag can be used to display the current Jelly variables and their values in the log.

Be sure to remove this tag before going to production.

<g:ui_form/>

This tag defines a form on the UI page.

For example, if your form contained the application_sys_id field, the g:ui_form might benefit from a processing script.

<g:ui_form> <p>Click OK to run the processing script.</p> <g:dialog_buttons_ok_cancel ok="return true" /> <input type="hidden" name="application_sys_id" value="499836460a0a0b1700003e7ad950b5da"/> </g:ui_form>

For more information, see UI macros.

<g:ui_input_field />

This tag adds a reference to a UI macro that creates an input field on a page that allows users to input information. The ui_input_field passes a label, name, value, and size into the UI macro.

Here is an example from a UI page:

<g:ui_input_field label="sys_id" name="sysid" value="9d385017c611228701d22104cc95c371" size="50"/>

For more information, see UI macros.

<g:ui_checkbox/>

This tag puts a user-editable check mark on a page. The name and value are passed into the UI macro.

Here is an example from a table on a UI page:

 <table> <tr> <td nowrap="true"> <label>Time Card Active:</label> </td> <td> <g:ui_checkbox name="timecard_active" value="${sysparm_timecard_active}"/> </td>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 254

 </tr> </table>

For more information, see UI macros.

<g:dialog_buttons_ok_cancel/>

This tag puts buttons on the UI page that run a specified processing script if the tag returns true.

If your UI page contains a form (uses the <g:form> tag), you can submit the form and have the Processing Script run. The Processing Script can naturally access fields on the form. For example, if your form contained the application_sys_id field:

<g:ui_form> <p>Click OK to run the processing script.</p> <g:dialog_buttons_ok_cancel ok="return true" /> <input type="hidden" name="application_sys_id" value="499836460a0a0b1700003e7ad950b5da"/> </g:ui_form>

<g:ui_reference/>

This tag adds a reference to a page that can be referenced by a Processing Script.

The following example creates a reference defined by name, ID, and table parameters in the tag:

<g:ui_reference name="QUERY:active=true^roles=itil" id="assigned_to" table="sys_user" />

Then in the Processing Script, reference the name field like this:

newTask.assigned_to = request.getParameter("QUERY:active=true^roles=itil");

You can specify a reference qualifier, so that the "name" attribute can be unique. The following example creates a reference defined by name, ID, and table parameters in the tag.

##### Note: The "columns" attribute only applies to the auto-completer.

<g:ui_reference name="parent_id" id="parent_id" table="pm_project" query="active=true" completer="AJAXTableCompleter" columns="project_manager;short_description"/>

Ampersand

Ampersands in Jelly can cause you grief because Jelly is XML.

Use ${AMP} to insert an ampersand in Jelly. If you are writing JavaScript that appears in the HTML part of say a UI page or UI macro that is actually going to run on the browser you are better off putting this code in the "client script" field and that way you can avoid escaping issues. However, if you really must put it in the "HTML" field, you will need to do something like this:

ta = ta[1].split('$[AMP]');

And

Use ${AND} to insert a JavaScript and in Jelly.

For example:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 255

if (d ${AND} e) var color = d.value;

Alternately, in a Jelly test you would use &amp&amp. For example:

<j:if test="${jvar_form_name == 'sys_form_template' &amp;&amp; !RP.isDialog()}">

Less than

Similar to ampersands, less than ("<") signs can also cause problems due to Jelly being XML. This can be resolved by reversing your test such that it is not necessary or by using ${AMP}lt; in place of the less than sign.

<g2:evaluate var="jvar_text"> var days = ""; var selectedDays = '$[${ref}]'; for (var i = 1; i ${AMP}lt;= 7; i++) { if (selectedDays.indexOf(i.toString()) >= 0) { days += gs.getMessage("dow" + i); days += " "; } } days; </g2:evaluate>

Many times you can avoid the "less than" operator all together by just using "not equals" which doesn't have escaping issues. For example:

for (var i=0; i != ta.length; i++) { }

Whitespace

Normally, white space is removed by Jelly. To keep it, you must specify that it not be trimmed.

For example, the following keeps the space after the colon.

<j2:whitespace trim="false">${gs.getMessage('Did you mean')}: </j2:whitespace>

Spaces

To encode a non-breaking space (&nbsp;), you can use $[SP].

For example:

<span id="gsft_domain" style="display: inline"> ${gs.getMessage('Domain')}:$[SP] <span id="domainDD" class="drop_down_element" style="text-decoration: none; color: white"> ${gs.getMessage("Loading...")} </span> </span>

Tracing Jelly

ServiceNow has a feature that allows the evaluation of Jelly to be traced.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 256

The trace is sent to the log. This should only be turned on during debugging as this produces a lot of logging. To turn on the trace, set the property glide.ui.template.trace to true. For example, the following script can be executed to do this:

GlideProperties.set ( 'glide.ui.template.trace' , true ) ;

If you want to see your log entries on your web browser at the bottom of each page, navigate to System Diagnostics > Debug Log.

##### Debugging scripts

Debug scripts using session logs and ServiceNow AI Platform debugging tools such as a walkthrough script debugger and error messages that display in the UI.

##### Debugging server-side scripts

Use the Script Debugger and session logs to debug server-side code. For more information, see Script Debugger and Session Log.

You can also use session debug to display error messages related to a server-side script that runs as a result of a client-side change. For more information, see Session debug.

###### GSLog is a script include that simplifies script logging and debugging by implementing levels of

log output, selectable by per-caller identified sys_properties values. For more information, see GSLog API.

##### Debugging client-side scripts

Use session debug to display debugging messages in the user interface. For more information, see Session debug. Use the session log to view logging information for script includes and custom UIs, such as Agent Workspace.

You can also debug client-side scripts using browser-based developers tools.

##### Debugging applications and scopes

Use the application debugging options to understand how a script's application scope might affect your application, table, or record. You may need to update cross-scope privileges to troubleshoot scope access issues. See Debugging applications.

Script Debugger and Session Log

The Script Debugger enables users with the script_debugger role to debug server-side JavaScript. Users with the log_debugger role can use the Session Log to view and download required logs.

Users with the script_debugger role can perform these actions using Script Debugger:

**-** Have a dedicated debug transaction, which applies only to the current session.

**-** Set and remove breakpoints.

**-** Pause the current session at a breakpoint.

**-** Evaluate expressions during runtime.

**-** Step through code line-by-line.

**-** Step into and out of function and method calls.

**-** View the value of local and global variables.

**-** View the value of private variables from function closures.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 257

**-** View the call stack.

**-** View the transaction that the system is processing.

**-** Turn off the script debugger to resume running paused scripts.

Use the Session Log tab to retrieve the session log for business rules, script includes, and a custom UI such as ServiceNow ® Agent Workspace that has a GraphQL component. Users with the log_debugger role can:

**-** View session logs in a separate tab.

**-** Download a log.

**-** View logs for Agent Workspace.

**-** Specify debug options to view or download only the required logs.

By default, 100 transactions and 10,000 messages appear on the Session Log tab. If the transaction or message count exceeds the default value, the session log is cleared and the next transactions or messages appear. You can configure this transaction and

###### message count using the glide.debugger.log.transaction.count and

###### glide.debugger.log_messages_limit user preferences respectively. For

###### more information about the glide.debugger.log.transaction.count and

###### glide.debugger.log_messages_limit user preferences, see User preference

settings.

##### Note: Enable Session Log as a separate tab with Script Debugger using the

###### glide.debugger.log.ui system property.

**-** The **Page** option displays logs under forms and lists and on the **Session Log** tab.

**-** The **Session** option displays logs only on the **Session Log** tab.

###### For more information about the glide.debugger.log.ui system property, see

Available system properties.

When you execute a statement in the Console, the executed statement is stored in the browser cache. You can use the up arrow key to get the previous statement and down arrow key to get the next statement from the browser cache. The user preference setting,

###### glide.debugger.console.cached_stmt_limit, defines the number of statements

cached in a browser session. The default statement cache value is 20 and the maximum value is

100. You can configure the statement cache value from user preferences.

##### Note: The cached statements are not available when the browser cache is cleared or

when you log in from a different browser or a different computer.

The Script Debugger can pause any server-side script that runs in an interactive transaction such as business rules, script includes, script actions, or UI actions that require a response to

###### proceed. If the GlideSystem method isInteractive() returns True when running the script

in context, then the Script Debugger can pause it.

##### Note: Some script objects, such as script includes, can be called from multiple contexts.

For example:

**-** when a business rule runs a script include on a form submit that is an interactive transaction waiting on the form data to change before continuing.

**-** when a scheduled job runs the same script include that is a non-interactive background transaction that can also run other scripts simultaneously.

To debug client-side scripts, you can use browser-based developers tools.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 258

A debugger transaction remains open as long as the user session is valid. If a user logs out or their session times out, the system closes the debugger transaction.

To view debug logs, see Display debugging logs.

##### Note: When the Script Debugger is enabled, code is executed in interpreted mode. If

parts of the script are set to run in strict mode, the debugger is not able to find the correct objects and the debugger fails. The Script Debugger must run on scripts outside of strict mode.

Parts of the user interface

The Script Debugger interface displays information about breakpoints set, the call stack and line number of the currently executing script line, details about variables and transactions, and status of console.

Script Debugger Not Paused

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 259

Script Debugger Paused

Parts of the Script Debugger

User interface element Description

Breakpoints Displays a list of the breakpoints set by script type, script name, and line number. The debugger updates this list as you add and remove breakpoints.

Call stack Displays a list of script calls that preceded or invoked the current line number. This information is only visible when the debugger pauses on a breakpoint.

Transaction details Displays information about the current transaction. This information is only visible when the debugger pauses on a breakpoint.

Status Displays if the debugger is waiting for a breakpoint, paused on a breakpoint, or has encountered an exception.

User Displays the name of the user who is running the current debugger session.

Coding pane header Displays the script type and name of the script in the coding pane.

Breakpoint icon Indicates the line number where the debugger pauses when evaluating the current script.

Pause debugging button Stops any current debugging session, and disables the Script Debugger for the current user. The Script Debugger doesn't pause on breakpoints for the current user until it's restarted.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 260

Parts of the Script Debugger (continued)

User interface element Description

Console Displays a command line interface used for evaluating expressions during runtime. The console is available only when the script execution is paused.

Resume script execution button Advances from the current breakpoint to the next breakpoint. If there are no other breakpoints, the script runs to completion.

Step over next function call button Advances past the method that's about to be called, executing the method as a single step.

Step into next function call Advances to the first line of executed code within a method call. Stepping into a method updates the current position within the call stack. If the user doesn't have read access to the method call, then this control acts like step over instead.

Step out of current function Exits from current method call and returns to the calling script from the call stack. If the user isn't within a method call, then this control acts like step over instead.

Local Displays a list of local scope JavaScript variable names and their values. This information is only visible when the debugger pauses on a breakpoint.

Closures Displays a list of global scope JavaScript variable names and their values set by function closure. This information is only visible when the debugger pauses on a breakpoint.

Global Displays a list of global scope JavaScript variable names and their values. This information is only visible when the debugger pauses on a breakpoint.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 261

##### Session Log

Session log

Session Log user interface elements

User interface element Description

Transactions Transaction ID. Displays information about the current transaction.

Filter for log text Field to enter text to filter the logs that contain a specific text.

Debug Output Option to filter logs based on the dynamically loaded debug output types. For example, Security Rule.

Apps Option to filter logs based on the dynamically loaded apps. For example, Service Management Integrations.

Message Type Option to filter logs based on the dynamically log levels. For example, Info.

Clear log Clears all logs.

Download log Download the logs in HTML file format.

Settings Session debug options. For information about the debug options, see Session debug.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 262

Script Tracer and debugging scripts

The Script Tracer can help you filter your debugging search to quickly narrow down script problems. You can identify lines of scripts in the Glide record that have undergone change during execution. Finding those specific lines of scripts rather than doing a wide search helps save time and improves productivity.

##### Overview of Script Tracer

Use the Script Tracer to narrow your search so you can debug scripts and business rules more efficiently. You can find the Script Tracer by searching in the left navigation pane.

##### Note: To use the Script Tracer, your role must be admin.

Once you enable Script Tracer and execute a UI transaction, the Tracer searches through all the scripts being executed. The following filters are available:

**- File type** : Search for a specific file type

**- Table** : Look in the specific table for the script being executed

The Script Tracer searches for changes in the script during execution and presents them in a list for you to examine. When you click Start Tracer , the Tracer begins searching for changes in the Glide record. You can click the Debug Script button at any time to see the script

itself.

Use the tabs to see specific information from the Tracer.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 263

The State tab displays the differences between the old and new scripts.

**-** By default, the **Show only changed values** check box is enabled, so you can avoid fields that have not changed.

**-** To view all the fields (changed or not), you can clear that check box.

##### Note: If the file is not reflected in the trace statement, it means the changes in the Glide

record is not recognized by the system.

If there are any errors, they display at the top of the State tab, with their line numbers and error message displayed in order of

occurrence.

**- Script** : Displays the line of changed scripts that the Glide record has undergone during execution. You can view the entire line of script by clicking the **Show Script** button.

**- Transaction** : Shows all transaction records of the trace

**- Debug Script** : Opens the script in Debugger to debug the script

**- View File** : Opens the script in the ServiceNow platform for editing

**- Clear trace** : Clears the trace when you are finished.

##### Limiting the tracer

You may want to set a limit for your trace so that you don't generate too many returns. By default there will be up to 1,000 lines of script traced. Once this number is reached you must clear the trace and start tracing again. If you want to change the maximum number of lines for tracing you

###### can configure your limit using the property glide.debug.trace.trace_line_limit.

Since each trace you run is new, make sure you're finished reading the results of one trace before clearing it and beginning another one.

To learn more, see Debugging scripts.

Script Debugger step-through and console controls

After the Script Debugger pauses a script, use the step-through controls to move between script lines and move between scripts in the call stack. Use the Console controls to expand console, collapse console, clear console, and rerun expressions.

Step-through controls

Control Icon Description

Stop debugging SHIFT+F2

Stops any current debugging session, and disables the Script Debugger for the current user. The Script Debugger does not pause on breakpoints for the current user until it is restarted.

Start debugger

- F2

Enables the Script Debugger for the current user. The Script Debugger pauses on breakpoints.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 264

Step-through controls (continued)

Control Icon Description

Resume script execution

- F9

Advances from the current breakpoint to the next breakpoint. If there are no other breakpoints, the script runs to completion.

Step over next function call OPTION +F9

Advances to the next evaluated line of script based on current conditions. The Script Debugger skips any lines of code that do not need to run because their conditions are not met. For example, when the condition of an if statement is not true, the debugger skips the code block for the condition.

Step into next function call OPTION +F10

When the Script Debugger pauses on a method call, this control allows the user to advance to the first line of executed code within the method call. Stepping into a method updates the current position within the call stack. If the user does not have read access to the method call, then this control acts like step over instead.

Step out of current function OPTION +F11

When the Script Debugger pauses within a method call, this control allows the user to exit the current method call and return to the calling script from the call stack. If the user is not within a method call, then this control acts like step over instead.

Console controls

Control Icon Description

Open Console Expands the Console.

Close Console Collapses the Console.

Clear expressions Clears all the expressions in the Console.

Re-execute expression Re-executes the expression which is already executed.

Related topics

Set or remove breakpoints

Evaluate expressions in runtime using Console

Define, declare, and verify new variables and functions while you debug a script in runtime using Console. The script execution must be paused to use Console.

###### Before you begin

**-** Review Limitations with using Console

**-** Role required: script_debugger, admin

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 265

###### Procedure

**1.** Launch the Script Debugger in one of the following ways.

Application Navigation path

Application navigator

Navigate to All > System Diagnostics > Script Debugger.

Studio Navigate to File > Launch Script Debugger.

**Syntax Editor** (^) Click the Script Debugger icon. The Script Debugger modal is displayed.

**2.** Trigger the script. For example, create a record to trigger an insert business rule script. The Script Debugger pauses the script on the first line that contains a breakpoint, and then you see the ServiceNow Script Debugger confirmation window.

**3.** Click **Start Debugging**. The focus shifts to the Script Debugger window and you see the target script that paused at the first breakpoint.

##### Note: Make sure that the status of Script Debugger is EXECUTION_PAUSED. You can

use Console only when the script execution is paused during debugging.

**4.** Click the expand console ( ) to expand the Console pane. To start evaluating expressions, enter one or more expressions in the Console and press Enter. For example, enter var x = 10; and press Enter. To enter multiple lines of expressions, press Shift + Enter after each line and press Enter after the last expression. To clear all the

expressions in the Console, click the clear console icon ( ). For more information on Console controls, see Script Debugger step-through and console controls.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 266

After a statement is executed, it is stored in the browser cache. You can use the up arrow key to get the previous statement and the down arrow key to get the next statement from the browser cache. You can configure the number of cached statements for a session from user preferences. For more information about user preferences settings, see Script Debugger and Session Log.

###### Result

After a statement is executed, it is stored in the browser cache. You can use the up arrow key to get the previous statement and down arrow key to get the next statement from the browser cache. You can configure the number of cached statements for a session from user preferences. For more information about user preferences settings, see Script Debugger and Session Log.

Related topics

Limitations with using Console

Limitations with using Console

You need to be aware of a few limitations when you use Console to evaluate expressions while debugging a script in runtime.

**-** The properties and values of an object don't display in Console. When you try to display an object to Console, only the string value of the object appears.

**-** Console doesn't support GlideSystem printing methods, such as info() and print().

**-** You can't use the this keyword in Console.

**-** A script debugger timeout occurs when you evaluate expressions in Console.

**-** While executing long scripts, if you see the response Awaiting response from server, you can't resume debugging or stop debugging using the resume or stop controls.

Launch the Script Debugger

Developers can launch the Script Debugger from the application navigator, Studio, or from the syntax editor.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 267

###### Before you begin

Role required:

**-** admin

**-** script_debugger

###### Procedure

Select a path based on your starting point.

Starting point Navigation path

Application navigator

Navigate to System Diagnostics > Script De bugger.

Studio Navigate to File > Launch Script Debugger.

Syntax Editor Click the Script Debugger icon.

The system opens the Script Debugger in a new window.

Set or remove breakpoints

Set breakpoints or conditional breakpoints to pause scripts at specific lines, and remove breakpoints when you are done debugging them.

###### Before you begin

Role required:

**-** admin

**-** script_debugger

###### About this task

Breakpoints belong to the developer who sets them. Developers must set and remove their own breakpoints.

##### Note: At a specific line, you can set either a logpoint or breakpoint but not both.

###### Procedure

**1.** Navigate to the server script to debug. For example, navigate to **All** > **System Definition** > **Business Rules**.

**2.** From the Syntax Editor, click the gutter next to a script line.

Action Description

Set a breakpoint Click a blank line to set a breakpoint.

Set a conditional breakpoint

Right-click a blank line and click Add condi tional breakpoint to set a conditional break point.

Remove a breakpoint Click a breakpoint to remove it.

Remove a conditional breakpoint

Right-click a conditional breakpoint and se lect Remove breakpoint to remove it.

**3.** From the Syntax Editor toolbar, click the **Open Script Debugger** icon.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 268

The system opens a Script Debugger window.

**4.** Trigger the script. For example, create a record to trigger an insert business rule script. The Script Debugger pauses the script on the first line containing a breakpoint, and the system displays a confirmation window.

**5.** Click **Start Debugging**. The system switches focus to the Script Debugger window and displays the target script paused at the first breakpoint. Console pane is enabled.

**6.** When debugging is complete, remove breakpoints from the script.

Related topics

Script Debugger step-through and console controls

Set or remove logpoints

Set breakpoints or conditional logpoints to log messages to the console at specific lines, and remove logpoints when you are done debugging them.

###### Before you begin

**-** Set the glide.debug.log_point system property to true. See Available system properties for more information.

**-** Role required: admin or script_debugger

###### About this task

Logpoints belong to the developer who sets them. Developers must set and remove their own logpoints.

##### Note: At a specific line, you can set either a logpoint or breakpoint but not both.

###### Procedure

**1.** Navigate to the server script to debug. For example, navigate to **All** > **System Definition** > **Business Rules**.

**2.** From the Syntax Editor, click the gutter next to a script line.

Action Description

Set a logpoint

Right-click a blank line and click Add logpoint to set a logpoint.

Remove a logpoint

Right-click a logpoint and select Remove log point to remove it.

Edit a logpoint

Right-click a logpoint and select Edit logpoint to edit it.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 269

##### Note: The script entered for the logpoint must have the same format as that of the script

in GSLog and GSInfo script includes.

**3.** From the Syntax Editor toolbar, click the **Open Script Debugger** icon.

**4.** On the Script Debugger window, trigger the script. For example, create a record to trigger an insert business rule script.

##### Note: You can also add logpoints in the Script Debugger window.

**5.** In the Script Debugger window, click **Session Log** to view the logpoints.

**6.** When debugging is complete, remove logpoints from the script.

Script Debugger status

The Script Debugger status determines what debugging actions are available and what information it can display.

The Script Debugger displays its status at the bottom left of the user interface.

Sample Script Debugger status

Possible Script Debugger status values

Status Occurs when Description Actions available

WAITING_FOR_FIRST_BREAKPOINTThe user opens a Script Debugger window or tab.

The Script Debugger is ready to pause script and display debugging information.

Pause script at the first breakpoint in the call stack.

EXECUTION_PAUSED

**-** The Script Debugger pauses on a breakpoint.

**-** The user steps over, steps into, or steps out to the next line of evaluated code.

The Script Debugger has paused on a line of code, and the user can debug the script. Console is enabled.

**-** Resume processing until the Script Debugger reaches the next breakpoint.

**-** Step through a script.

**-** Display the call stack.

**-** Display transaction information.

**-** Display variable values.

**-** Evaluate expressions in Console during runtime.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 270

Possible Script Debugger status values (continued)

Status Occurs when Description Actions available

WAITING_FOR_BREAKPOINT

**-** The user resumes processing until the Script Debugger reaches the next breakpoint.

**-** The user steps through a script until the Script Debugger reaches the next line of code to evaluate or the transaction completes.

The Script Debugger is searching for the next line of code at which to pause. Users will typically never see this status because the Script Debugger changes status after it locates the next breakpoint or script line to evaluate.

**-** Pause script at the next breakpoint.

**-** Pause script at the next script line requiring evaluation.

OFF

**-** The user pauses the Script Debugger.

**-** The user closes the Script Debugger window or tab.

**-** The user session ends for any reason.

**-** The administrator resets all Script Debugger instances by navigating to the debugger_reset.do page.

The Script Debugger is inactive and does not pause scripts or display debugging information.

**-** Start the Script Debugger.

**-** Open a Script Debugger window or tab.

##### Log entries

Every time a debug transaction finishes executing, the system creates a log entry for it with a DEBUGGED prefix. For example:

2016-08-15 15:57:32 (197) Default-thread-3 900F510167112200C4098C7942415A75 \*\*\* End ,39﷯ path: /my-app.do, user: admin, DEBUGGED total transaction time: 0:00:11.010, transaction processing time: 0:00:11.010, network: 0:00:00.000, chars: 6,058, uncompressed chars: 20,731, SQL time: 50 (count: 34), business rule: 0 (count: 0), phase 1 form length 56,464, largest chunk written: 10,428, request parms size: 40, largest input read: 0

Transaction details

The Script Debugger displays transaction details for the current paused user session.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 271

Transaction details are available in a dedicated resizeable section underneath the Call Stack on the bottom left of the Script Debugger.

Example transaction details

The Script Debugger only displays transaction details when it pauses on a script. Developers can use transaction details to:

**-** Inspect the URL of the currently paused transaction.

**-** Inspect the request parameters for the currently paused transaction.

**-** Inspect network information about the current transaction.

**-** Inspect the user and session ID that initiated the debug transaction.

Related topics

Available transaction details

Available transaction details

The Script Debugger provides a standard set of transaction details for developers to debug and troubleshoot scripts.

Available transaction details

Transaction element

Description

url The URL of the currently paused transaction.

Request parameters

The list of request parameters for this transaction. Each transaction has its own list of request parameters, but record transactions typically include the field values used to insert, update, or delete a record.

instance The instance name.

address The IP address of the end-user client system.

session The user session ID.

forward The IP address of the load balancer.

query count The number of database queries the Script Debugger has made.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 272

Available transaction details (continued)

Transaction element

Description

thread The name of the thread running the Script Debugger instance.

transactionid The Sys ID of the current transaction.

token The Script Debugger token of the currently paused transaction. The system uses this token to identify different Script Debugger instances.

name The name of the currently paused transaction. You can use this name to identify transactions in the logs.

processor The name of the processor processing the current transaction, if present.

method The HTTP request method the currently paused transaction uses.

startTime The date-time stamp when the Script Debugger instance started.

page The current table or UI page associated with the transaction.

user The user who triggered the debug transaction.

nodeid The Sys ID of the node running the Script Debugger instance.

Related topics

Transaction details

Script Debugger multiple developer support

The Script Debugger allows multiple developers to debug their own transactions without affecting each other.

The Script Debugger only allows developers to see and interact with items related to their current debugging session such as:

**-** Breakpoints

**-** Call stack

**-** Console

**-** Transactions

**-** Status

The Script Debugger prevents one developer from seeing or modifying another debug session. Administrators, however, can impersonate another user, open the Script Debugger, and debug transactions generated by the impersonated user.

The Script Debugger displays the debug session user at the bottom left of the user interface.

Sample Script Debugger user

##### Concurrent Script Debugger usage

By default, the system supports debugging [(The number of semaphores on the instance) / 4] concurrent transactions. Administrators can specify the number of concurrent transactions the system can debug by setting the

###### glide.debugger.config.max_node_concurrency system property. The system can

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 273

debug up to [(The number of semaphores on the instance) 2] concurrent transactions.

##### Administration of debugging sessions

Debugging sessions can remain actively debugging (in the EXECUTION_PAUSED or WAITING_FOR_BREAKPOINT statuses) until:

**-** The user pauses the Script Debugger.

**-** The user closes the Script Debugger.

**-** The user session ends.

Administrators can view the currently running debugger sessions by navigating to the page xmlstats.do.

Administrators can stop all currently running debugging sessions by navigating to the page debugger_reset.do. Only users with the admin role can access this page.

Related topics

Script Debugger impersonation support

Script Debugger impersonation support

You can use the Script Debugger while impersonating another user, but only if the impersonated user has the script_debugger role and has read access to the target script.

While impersonating another user, you can:

**-** See and change breakpoints that belong to the impersonated user.

**-** View and pause on scripts that the impersonated user has read access to.

**-** Evaluate expressions in Console on behalf of the impersonated user.

The Script Debugger step-through controls also use the read access of the impersonated user. For example, if the impersonated user does not have read access to a function in the call stack, any Step into action instead becomes a Step over action.

The impersonated debugging session lasts until:

**-** You stop impersonating the user.

**-** You log out or the user session ends.

**-** You pause the Script Debugger.

**-** You close the Script Debugger.

Related topics

Script Debugger multiple developer support

Script Debugger Scripts Background support

The Scripts Background module does not support setting breakpoints directly in the script field. You can however, set breakpoints in the script objects called or triggered by the Scripts Background module.

While running arbitrary JavaScript code in the Scripts Background module, the Script Debugger can only pause scripts when you:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 274

**-** Call a script include containing breakpoints.

**-** Trigger a business rule containing breakpoints.

**-** Trigger a script action containing breakpoints.

Domain separation and Script Debugger

Domain separation is supported in Script Debugger. Domain separation enables you to separate data, processes, and administrative tasks into logical groupings called domains. You can control several aspects of this separation, including which users can see and access data.

##### Support level: Basic

**-** Business logic: Ensure that data goes into the proper domain for the application’s service provider use cases.

**-** The application supports domain separation at run time. The domain separation includes separation from the user interface, cache keys, reporting, rollups, and aggregations.

**-** The owner of the instance must set up the application to function across multiple tenants.

Sample use case: When a service provider (SP) uses chat to respond to a tenant-customer’s message, the customer must be able to see the SP's response.

For more information on support levels, see Application support for domain separation.

##### How domain separation works in Script Debugger

Script Debugger is not a full application but rather, a feature in the Platform suite, meaning it works alongside other features, including domain separation.

Related topics

Domain separation for service providers

Session debug

Enable session debugging to display debugging messages in the user interface.

Troubleshooting slow performance with the Session Debug feature.

You can enable all areas for abundant logging on the bottom of each page load, or you can enable each module one by one, for more specific information about what is happening during this session, and specifically, for the previous transaction. Select session debug options under System Diagnostics > Session Debug. When enabled, session debugging is active during the user session or until disabled. To view debug logs, see Display debugging logs.

The system provides the following session debugging options.

Session debug options

Debug option

Description

Debug AI Search

Displays debugging messages for AI Search.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 275

Session debug options (continued)

Debug option

Description

Debug Business Rule

Displays debugging messages for business rules. If there are business rules from multiple applications affecting a table or record, the system displays which application the business rule comes from.

Debug Business Rule (Details)

Displays debugging messages for business rules and any changes made by business rules. If there are business rules from multiple applications affecting a table or record, the system displays which application the business rule comes from.

Debug Escalations

Displays debugging messages for SLA and SLO escalations.

Debug Data Policies

Displays debugging messages for data policies.

Debug Date/Time

Displays Date/Time failures when inputs do not match required formats.

Debug Homepage Render

Displays debugging messages for homepages.

Debug Log Displays all log entries.

Debug Metric Statistics

Displays an aggregate view of performance data (slow transactions, scripts, queries, events, and mutexes). These aggregate metrics are sorted by transaction, to help identify items that affect page performance.

Debug NLQ

Displays debugging messages for Natural Language Query (NLQ) queries.

Debug Quotas

Displays debugging messages for transaction quotas.

Debug Scopes

Displays debugging messages for entering or exiting application scopes when running script objects.

Debug Security

Displays debugging messages for access controls. If there are access controls from multiple applications affecting a table or record, the system displays which application the access controls comes from.

Debug SQL Displays debugging messages for SQL queries.

Debug SQL (Detailed)

Displays debugging messages for SQL statements and any changes made by SQL statements.

Debug Text Search

Displays debugging messages for search result relevance and indexing.

Debug UI Policies

Displays debugging messages for UI policies.

Debug UI Macro

Displays the start and end of the UI Macro in the DOM as HTML comments. The comments consist of table name and UI macro name.

Debug Upgrade

Displays detailed information logged for records processed during the last familyto-family or patch version upgrade session.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 276

Session debug options (continued)

Debug option

Description

Enable All Displays all available debugging messages.

Disable All Stops displaying all debugging messages.

Disable Debug UI Macro

Stops displaying the start and end of the UI Macro in the DOM as HTML comments.

Disable UI Policies Debug

Stops displaying debugging messages for UI policies.

Display debugging logs

Display session debug logs to help diagnose script and application problems.

###### Before you begin

Role required: none

###### Procedure

**1.** Navigate to **All** > **Session Debug** and select **Enable All**.

**2.** Under **Session Debug** , select **Debug Log**. The Debug log displays.

Debugging applications

Application developers can display debug messages about configuration records to help them troubleshoot issues. The Debug Scopes module provides information about the system switching between custom applications to run server-side scripts.

The system offers the following debugging options to help application developers determine how applications affect configuration records.

Application debug options

Debugging option

Description

Debug Business Rule

Use this module to determine which application's business rules are running against tables. The system only displays application information if business rules from different application scopes run on the same table.

Debug Business Rule (Details)

Use this module to determine the results of running business rules against tables. The system only displays application information if business rules from different application scopes run on the same table.

Debug Security

Use this module to determine which application's access controls apply to a given table or record.

Debug Scopes

Use this module to determine the application scope context in which a script runs. Since one script can call another script it is possible to have multiple application scope context changes while running a series of scripts.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 277

Application debug options (continued)

Debugging option

Description

Enable Session Debug

Use this related link to enable the generation of log messages for a particular application. Application scripts that use GlideSystem logging methods will generate output to the log at the indicated verbosity level.

When multiple applications contribute to the debug output, the system adds a new section called Apps to the display a list of the applications writing to the session log. Clicking on the check box next to the application name hides or displays the application's associated debug messages.

Sample application debug output of business rules

Debugging scopes

Application developers can use the Debug Scopes module to display information about when the system switches between custom applications to run server-side scripts.

When enabled, the system displays a message whenever the system switches to a custom application to run a server-side script.

Sample debug scopes output from the incident table

Every time the system runs a server-side script object it enters the script's scope context. When the script finishes running, the script exits the scope context. The debugging messages track changes to the script scope context.

The debugging message displays a greater than character > each time the system enters a script object's context, and displays a less than character < every time the system exits a script object's context. In cases where one script calls another the debugging message adds another greater

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 278

than character to the path for each call. For example, if a business rule calls a script include, which in turn calls another script object there would three characters in the path such as:

> Entering scope [x_app_one] >> Entering scope [x_app_two] >>> Entering scope [x_app_three]

##### Note: The system does not display entering or exiting messages for script objects in the

global scope.

Application developers may want to enable other debugging options to in conjunction with this option to see information about the possible source of the server-side script such as Debug Business Rule.

Debugging business rules

Debugging business rules can be achieved with resources available in the ServiceNow product.

##### 1. Tools

The first step in the process is to identify tools which will help you figure out what's wrong.

Debugging tools

Debugging tool

Description

System Dictionary

Navigate to System Definition > Dictionary. The dictionary provides a list of all tables within your instance and can be invaluable when trying to locate information.

System Log Navigate to System Logs > System Log. You can place alert statements in your business rule which can write information to the log.

Debug Business Rule (Details)

Navigate to System Diagnostics > Session Debug > Debug Business Rule (Details). This debugging module displays the results business rules. Use this module to see if conditions are being met and values are being set as expected.

Alert Messages

There are several system functions that allow you to print messages to the page, the field or the log file. See Scripting alert, info, and error messages.

Business Rule Examples

Sometimes you can find what you're looking for in scripts others have written, including business rule error messages, or by building an OR query.

GlideRecord Information

This is the basic syntax used to query the database for information. See Querying tables in script. GlideRecord also includes aggregation support.

##### 2. Variables

The next step is to gain some insight into the behavior of your business rule. For every action except an insert, you will more than likely use a query to get your record(s).

var rec = new GlideRecord('incident'); rec.addQuery('active',true); rec.query(); while (rec.next()) { gs.print(rec.number + ' exists'); }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 279

###### To verify whether your query is actually returning records you can use gs.addInfoMessage

to display information at the top of the screen.

var rec = new GlideRecord('incident'); rec.addQuery('active',true); rec.query(); gs.addInfoMessage("This is rec.next: " + rec.next()); while (rec.next()) { gs.print(rec.number + ' exists'); }

If your query returns no records you see the following:

This is rec.next: false

Use this technique to verify every variable within your business rule contains expected values.

##### Tip: If necessary, break your script down into individual pieces and verify each piece

works separate from the whole and then put them all back together one step at a time.

##### 3. Locating information

The last step is to make sure you know where to find the information your rule is looking for.

In the ServiceNow application, one table can extend another table. This means when searching for information, you might need to query the parent table for the extended table's sys_id to find what you seek.

A good example is the sc_task table, which extends the task table. The script below queries the extended table (sc_task) for the current sys_id and then query the parent table (task) for records with the matching sys_id, and then prints out the work notes field.

var kids = new GlideRecord('sc_task'); kids.query();

gs.addInfoMessage("This is requested item number: " + current.number); gs.print("This is the requested item number: " + current.number);

while (kids.next()) { var parents = new GlideRecord('task'); parents.addQuery('sys_id', '=', kids.sys_id); parents.query();

while(parents.next()) { gs.addInfoMessage("This is task number: " + parents.number); gs.print("This is task number: " + parents.number); gs.addInfoMessage("These are the work notes: " + parents.work_notes); gs.print("These are the work notes: " + parents.work_notes); }

}

Debugging classifications

You must add a system property to enable classification debugging.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 280

##### Debugging classifications

The resulting log entries list the name of each classifier that runs, along with all the names and values that are available to the criteria in the classifier. To log debugging information about classifications, add the following system property.

System Property Description

###### glide.discovery.debug.ci_identification Enables debugging information for

process classification.

**-** Type: true | false

**-** Default Value: false

**-** Location: Add to the System Properties [sys_properties] table

Field watcher

The field watcher tool tracks and displays all actions that the system performs on a selected form field.

##### Note: Field watcher is not supported with Next Experience in Utah. For more information

about supported features in Next Experience, see Considerations for activating Next Experience.

Administrators can use the field watcher to figure out what happens to the field and how the value of the field changes when an event such as the firing of a business rule or enforcement of a data policy, takes place. Administrators can also impersonate non-admin users to debug what happens when those users make changes on an instance. Only one field can be watched at a time. Non-admin users with the impersonator role have access to the field watcher feature.

##### How the field watcher works

The Field Watcher tool logs activity when any of the following events occur on a field:

**-** The default value is set on the field.

**-** User access rights for the field change due to an ACL or dictionary setting.

**-** A data policy prevents the value from being set.

**-** A reference qualifier query of the field value executes.

**-** A UI policy changes a field to or from read-only, visible, mandatory, or editable.

**-** A dependent value in another field restricts field choices.

**-** The value of the field is set or changed based on:

◦ Assignment rules

◦ Actions from an engine, such as the workflow engine

◦ Business rules

◦ User entries

◦ Client scripts

◦ UI actions

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 281

##### Note: The field watcher works only on form fields. It cannot be used on list fields. Also,

field watcher is not available on password-protected fields or encrypted fields. Field watcher is only available within the UI frame. The option to watch a field does not appear in the context menu if you open a record outside of the UI frame, for example, in a new tab.

Use field watcher

Access field-level debugging information using the field watcher.

###### Before you begin

Role required: none

###### Procedure

**1.** Navigate to the form for which you want to view field-level debugging information.

**2.** Activate field watcher by right-clicking any field label on a form and select **Watch - '<field** **name>'**.

The debug icon ( ) appears next to the field label. From this point on, the field watcher records every action taken on the selected field. For example, if you are watching a Priority field, if the priority is changed from Moderate to Low and the record is updated, the field watcher will display information about that change.

**3.** View the field watcher log by clicking the debug icon. A new pane opens at the bottom of the screen, showing a field watcher tab. It may also show tabs for JavaScript Logging and JavaScript Debugger.

**4.** Click the **Field Watcher** tab, if needed.

**5.** Stop watching a field by right-clicking the field and selecting **Unwatch - <field name>**. To watch another field, right-click that field and select **Watch - <field name>**.

**6.** Clear the field watcher log by clicking the clear log button ( ).

**7.** Resize the field watcher pane by dragging the splitter bar up or down. Dragging the splitter bar to the bottom of the screen closes the field watcher pane. Reopen the pane by clicking the debug icon again.

Field watcher tab details

The field watcher displays field information and configuration options.

The left-side of the Field Watcher tab shows the following information for the watched field.

**- Table** : table to which the field belongs.

**- Element** : field label.

**- Type** : type of data stored in the field.

**- Dependent** : field on which the current field depends.

**- Reference** : table from which the field's value originates, if applicable.

**- Reference Qual** : reference qualifiers that may be restricting data on the field.

**- Attributes** : attributes on the field as specified in the dictionary entry for that field.

On the right-side of the Field Watcher tab, select the types of activity information you want to see for the selected field. Clear the check box for any type of information that is not needed.

Watching a hidden field

Administrators may need to watch a hidden field.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 282

###### Procedure

**1.** Use the dictionary to determine the column name of the field.

**2.** Elevate privileges to the security_admin role.

**3.** Navigate to **System Definition** > **Scripts Background**.

**4.** In _Run script (JavaScript executed on server)_ , enter the following command:

gs.getSession ( ). setWatchField ( "hidden_field" ) ;

Replace hidden_field with the column name of the hidden field.

**5.** Navigate to the form containing the missing field.

The Field Watcher tab output contains information about the hidden field.

Viewing information for the watched field

When information for a watched field is changed and the record is updated, the field watcher tab displays relevant information at the bottom.

Field watcher viewing data

Field watcher information includes:

**- Timestamp** : time the field was changed using the HH:MM:SS (ms) format.

◦ Orange text : server-side changes, such as ACLs.

◦ Blue text : client-side changes, such as client scripts.

**- Type of object that changed the field and its associated name** : The type of item that changed on the field; for example, **CLIENT SCRIPT** , **BUSINESS RULE** , or **ACL**. In the case of scripts, business rules, or other configuration-type fields, field watcher displays the name of the script or business rule that changed the field, if any. Click the name to go directly to the record for that item.

**- Old and new values** : The old and new values for the field, if the value changed0. Field watcher does not record the value if it was inserted in the form by default at the time the record was created.

**- Additional information** : Call tracing information, such as the name of the script engine or workflow that changed the field. Click the plus icon to expand the selection.

◦ Orange text : Indicates server-side activity.

◦ Blue text : Indicates client-side activity.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 283

Example: Watching the incident priority

The following example shows what happens to the Priority field on the incident form when both the Impact and Urgency fields change.

The Incident form has two client-side data lookups change the priority. Additionally, server-side ACLs and the data lookup engine fire when the record is saved. Finally, a client-side UI policy sets the Priority field back to read-only, which is the default setting.

Watching the incident priority

Original values

**-** Priority:1 - Critical

**-** Impact:1 - High

**-** Urgency:1 - High

First Change

**1.** The user changes the **Impact** value to **3 - Low**.

**2.** The priority automatically changes to **3 - Moderate** based on the **Priority Lookup** data lookup definition used by default in ServiceNow incidents.

##### Note: At this point, the record has not been saved.

Second Change

**1.** The user changes the **Urgency** value to **2 - Medium**.

**2.** The priority automatically changes to **4 - Low** based on the same **Priority Lookup** data lookup definition.

**3.** The user saves the record by right-clicking the form header and choosing **Save**.

Field watcher example

##### Note: The values that change from 1 to 3, and then from 3 to 4, refer to the numerical

values in the choice list.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 284

Writing to the debug log

To write to the debug log in your client-side JavaScript, or UI policies, make a call to the global function jslog().

An example of using jslog() in JavaScript:

function logData (r ) { lastLogDate = r. responseXML. documentElement. getAttribute ( "last_log_entry" ) ; var items = r. responseXML. getElementsByTagName ( "log" ) ; jslog ( "response=" + r. responseText ) ; }

Additionally, when o n L o a d client scripts run, the name of the client script and timing information is displayed. This can be useful in determining which o n L o a d scripts are running and whether they are impacting performance.

Debug UI policies

###### Enabling the glide.ui.ui_policy_debug property lets you monitor the processing of UI

actions.

Here are some sample log events from an incident policy that sets fields to read-only if the incident_state is closed.

GlideFieldPolicy: Evaluating condition GlideFieldPolicy: incident_state (7) = 7 -> true GlideFieldPolicy: --->>> TRUE GlideFieldPolicy: Setting opened_at disabled to true GlideFieldPolicy: Setting opened_by disabled to true GlideFieldPolicy: Setting closed_at disabled to true GlideFieldPolicy: Setting closed_by disabled to true GlideFieldPolicy: Setting company disabled to true

Access the JavaScript log

JavaScript that runs on the browser, such as client scripts, can include a call to jslog() to send information to the JavaScript Log. Users with the admin role can access this log.

###### Before you begin

Role required: admin

###### About this task

The steps to access the JavaScript debug window depend on which UI version you are using.

##### Note: The JavaScript debug window is not supported with Next Experience in Utah. For

more information about supported features in Next Experience, see Considerations for activating Next Experience.

###### Procedure

**1.** Open the JavaScript log by navigating to the appropriate location for your version of the UI.

Core UI a. Click the gear icon in the banner frame.

b. Click the Developer section.

c. Toggle the JavaScript Log and Field Watcher switch.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 285

UI15 a. Click the gear icon in the banner frame.

b. Click JavaScript Log and Field Watcher.

UI11 (^) Click the debug icon ( ) in the banner frame. A new pane opens at the bottom of the screen. It shows the JavaScript Log tab and may also show the Field Watcher tab.

**2.** If needed, select the **JavaScript Log** tab.

**3.** Click the clear icon ( ) to clear the contents of the log, as needed.

JavaScript debug window

The JavaScript debug window appears in a bottom pane of the user interface when an administrator turns on debugging.

##### Note: The JavaScript debug window is not supported with Next Experience in Utah. For

more information about supported features in Next Experience, see Considerations for activating Next Experience.

Use the debug window to access these tools.

**-** JavaScript Log: JavaScript that runs on the browser, such as client scripts, can include a call to

###### jslog() to send information to the JavaScript log.

**-** Field Watcher: a tool that tracks and displays all actions that the system performs on a selected form field.

JavaScript debug window

Using the JavaScript debug window

The JavaScript debug window enables access to the JavaScript Log and the Field Watcher tools.

###### Before you begin

Role required: admin

###### About this task

The steps to access the JavaScript debug window depend on which UI version you are using.

##### Note: The JavaScript debug window is not supported with Next Experience in Utah. For

more information about supported features in Next Experience, see Considerations for activating Next Experience.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 286

###### Procedure

**1.** Open the JavaScript debug window by navigating to the appropriate location for your version of the UI.

Core UI a. Click the gear icon in the banner frame.

b. Click the Developer section.

c. Toggle the JavaScript Log and Field Watcher switch.

UI15 a. Click the gear icon in the banner frame.

b. Click JavaScript Log and Field Watcher.

UI11 (^) Click the debug icon ( ) in the banner frame. The JavaScript debug window re-opens at the bottom of the screen. The tab that is currently active in the window is the last tab that was active when the window was closed.

**2.** Click a tab to use one of the debug window features.

◦ JavaScript Log

◦ Field Watcher

Related topics

Writing to the debug log

Field watcher

JS Code Coverage Debug

The JS Code Coverage Debug application allows administrators and application developers to log the server-side scripts triggered during a user session and then review which lines of code the system ran.

Users with the js_coverage_debugger role can debug server-side scripts without having to set breakpoints or review onscreen debug messages. Instead, the system saves script usage data in the JavaScript Code Coverage [sys_js_code_coverage] table. Each JavaScript Code Coverage record contains:

**-** The user session that called the script.

**-** The script record the system called identified by table, sys_id, and script field.

**-** The script record the system called identified by type and name.

**-** The transaction that called the script.

**-** The start time of the transaction.

**-** The contents of the script field highlighted to indicate which lines the system ran.

##### Note: The JS Code Coverage Debug application doesn't log information for client-side

scripts.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 287

Sample code coverage highlighting

JS Code Coverage highlighting

The JS Code Coverage application highlights script fields to indicate whether the system ran or skipped each line.

Sample code highlighting

The color of the highlight indicates how the system evaluated the code line.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 288

Meaning of code highlighting

Highlight color

Meaning

Green This is an executable line of code that the system ran during the session.

Red This is an executable line of code that the system skipped for some reason. The system may have skipped an executable line of code because the necessary script conditions were not met or because the script function was never called. You may want to use the Script Debugger to determine why the system skipped the line of executable code.

Gray This is a non-executable line of code such as white space, code comment, or a portion of an expression split across multiple lines that cannot run on its own.

Administrators and application developers can use this information to conduct more targeted debugging activities such as using the Script Debugger to determine why script conditions are not being met.

Activate JS Code Coverage Debug

You can activate the JS Code Coverage Debug plugin (com.glide.js.coverage) if you have the admin role.

###### Before you begin

Role required: admin

###### Procedure

**1.** Navigate to **All** > **System Applications** > **All Available Applications** > **All**.

**2.** Find the plugin using the filter criteria and search bar.

You can search for the plugin by its name or ID. If you cannot find a plugin, you might have to request it from ServiceNow personnel.

**3.** Select **Install** to start the installation process.

##### Note: When domain separation and delegated admin are enabled in an instance, the

administrative user must be in the global domain. Otherwise, the following error appears: Application installation is unavailable because another operation is running: Plugin Activation for <plugin name>.

You will see a message after installation is completed. For information about the components installed with a plugin, see Find components installed with an application.

###### What to do next

To see the components the plugin installed, refresh the plugin form and select the Plugin Files related list.

Debug with JS Code Coverage Debug

Use JS Code Coverage Debug to record a user session and then review which server-side scripts and lines of code the system ran.

###### Before you begin

Role required: js_coverage_debugger or admin

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 289

###### Procedure

**1.** Navigate to **All** > **JS Code Coverage Debug** > **Enable Coverage**. The system logs which server-side scripts and code lines the system runs as well as displays session debug messages in the JS Code Coverage namespace.

**2.** Navigate to the table or page whose logic you want to test.

Example For example, navigate to Incident > Create New.

**3.** Trigger the server-side script or scripts you want to test.

Example For example, create an incident with an associate CI item to test several business rules.

**4.** When you have completed testing, navigate to **JS Code Coverage Debug** > **Disable Coverage**. The system stops logging script and code lines run.

**5.** Navigate to **JS Code Coverage Debug** > **Coverage Data**. The system displays the list of coverage data associated with the current user session.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 290

**6.** Select the script or transaction you want to review.

JavaScript Code Coverage fields

Field Description

Script Name Displays the script run by table name, sys_id value, and script field.

Script Reference Displays the script run by script type and name.

Transaction Name Displays the transaction that called the script by thread ID and URI.

Example For example, select the Script Reference Business Rule: incident events. The system displays the JS Code Coverage Debug record.

**7.** Review the **Script** field to determine which lines of code the system ran.

Example For example, the business rule added the incident.inserted event to the event queue.

###### Result

You determine which lines of code the system ran.

###### What to do next

Use the code coverage information to do more targeted debugging activities such as set breakpoints and review variable values with the Script Debugger.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 291

##### Packages Call Removal tool

The Packages Call Removal Tool provides modules to identify fields that might contain scripts, find scripts that contain Packages calls to ServiceNow Java classes, and to examine proposed script changes that eliminate those Packages calls.

##### Note: This tool is not activated by default, and is only available to users with the admin

role.

Packages calls to ServiceNow Java classes will be prevented in a future release. The Packages Call Removal tool helps prepare your instance to use the new API and includes the following scripts and pages:

**-** The Find Packages Fields script scans scripts for Packages calls to ServiceNow Java classes.

**-** The Find Packages Calls script proposes changes that remove Packages calls or replaces them with GlideScriptable names.

**-** The Packages Call Items page lists and enables you to work on proposed changes to scripts.

The tool might generate errors as it tries to generate preferred, scriptable alternatives for Packages calls to ServiceNow Java classes.

##### Note: Create an update set before migrating the changes that result from running the

Packages Call Removal Tool. For information, see Get started with update sets.

Activate the Packages Call Removal Tool

You must activate the Packages Call Removal Tool plugin to access the tool.

###### Before you begin

Role required: admin.

###### Procedure

**1.** Navigate to **All** > **System Applications** > **All Available Applications** > **All**.

**2.** Find the Packages Call Removal Tool plugin using the filter criteria and search bar.

You can search for the plugin by its name or ID. If you cannot find a plugin, you might have to request it from ServiceNow personnel.

**3.** Select **Install** to start the installation process.

##### Note: When domain separation and delegated admin are enabled in an instance, the

administrative user must be in the global domain. Otherwise, the following error appears: Application installation is unavailable because another operation is running: Plugin Activation for <plugin name>.

You will see a message after installation is completed. For information about the components installed with a plugin, see Find components installed with an application.

Find a Packages call

After you run the Find Packages Fields script to define the list of fields to search for Packages calls, run the Find Packages Calls script to generate the list of fields with Packages calls to ServiceNow Java classes. The script also proposes changes.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 292

###### Procedure

**1.** Click **(3) Find Packages Calls (script)** to execute a script that searches the fields for packages calls and populates the Packages Call Items list with proposed changes.

Example

Find Packages Calls

**2.** Click **(4) Packages Call Items** to display the list of affected fields on the Packages Call Items page. The Packages Call Items page lists the items with Packages calls, shows each item's current state, the table that contains the field, the affected record, the number of Packages calls contained in the field's script, and the number of errors that occurred when the proposed script was generated.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 293

Example

Packages Call Items

**3.** On the Packages Call Items page, click a record for any of the listed items to open the form and revise as described in Replacing Packages Calls.

As you work through the list, the State of the items are updated and the items are grouped by State:

◦ Proposed: A proposed revision exists for the field.

◦ Error (red): One or more errors occurred when the proposed script was generated.

◦ Rejected (gray): A proposed change has been rejected.

◦ Completed (green): The field has been successfully revised to remove Packages calls to ServiceNow Java classes.

◦ Canceled (gray): Since the proposed change was generated, either the original script has been changed to no longer require modification, or the original record no longer exists.

Glide object name

The names of the new Glide objects that replace Packages calls are derived from the Java package name used in the Packages call.

###### About this task

Although the tool automatically substitutes the appropriate new scriptable name for each Packages call it encounters, in some circumstances it can be useful to know how to manually replace a Packages call with its new scriptable object equivalent. Use the steps below to determine the new script object name from the Packages call name. The replacement objects include the same methods and properties as the objects they replace.

To determine the new object name:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 294

###### Procedure

**1.** Note the third term in the Java package name. This term is usually glide, but is sometimes snc or glideapp.

**2.** Drop all of the prefix terms, leaving only the last.

###### For example, Packages.com.glide.monitor.AbstractBucketCollector

becomes AbstractBucketCollector.

**3.** Capitalize the first letter of the term noted in the first step above and add it to the front of the term defined in step 2.

###### For example, Packages.com.glide.monitor.AbstractBucketCollector

###### becomes GlideAbstractBucketCollector and Packages.com.snc.cmdb.BaselineCMDB

becomes SncBaselineCMDB.

**4.** Verify that the name is valid by executing a gs.print() command in Scripts Background, specifying only the name with no quotes. For example:

###### gs.print( SncBaselineCMDB );

\*\*\* Script: [JavaClass com.snc.cmdb.BaselineCMDB]

Note that there are exceptions to this rule, such as "Glide", which replaces "Packages.com.glide.Glide", "TestExtension", which replaces "Packages.com.glide.junit.misc.TestExtension"; and "UINotification", which replaces "Packages.com.glide.ui.UINotification".

Glide object replacement list

This table lists the Glide classes and the Packages calls they replace.

##### Note: The publication of this list does not imply that these scriptable objects are for use

by customers, consultants, and partners. The use of the Glide prefix does not imply that these scriptable objects are in the same category as or have the same status as objects such as GlideRecord. Except where documentation is provided in the API Reference, these undocumented APIs are not intended for general use, and ServiceNow, Inc., does not make any commitment to document them, answer questions about them, or maintain them indefinitely in their current form. Over time, ServiceNow, Inc., intends to migrate a subset of the functionality represented by these objects into the documented API and remove the rest.

GlideScriptable object replacement list

GlideScriptable Class Packages Call

Glide Packages.com.glide.Glide

GlideAbstractBucketCollector Packages.com.glide.monitor.AbstractBucketCollector

GlideAbstractDomainProvider Packages.com.glide.db.domain.AbstractDomainProvider

GlideAbstractExecutionPlan Packages.com.glide.execution_plan.AbstractExecutionPlan

GlideAbstractListener Packages.com.glide.listener.AbstractListener

GlideAbstractRenderer Packages.com.glide.ui.portal.AbstractRenderer

GlideAction Packages.com.glide.script.Action

GlideActionManager Packages.com.glide.ui.action.ActionManager

GlideAJAXScheduleItem Packages.com.glide.schedules.AJAXScheduleItem

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 295

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideAJAXSchedulePage Packages.com.glide.schedules.AJAXSchedulePage

GlideAlertActions Packages.com.glide.alerts.AlertActions

GlideappAbstractChoiceListQuestion Packages.com.glideapp.questionset.AbstractChoiceListQuestio

GlideappADSILoader Packages.com.glideapp.ecc.ADSILoader

GlideappAJAXMapPage Packages.com.glideapp.google_maps.AJAXMapPage

GlideappCalculationHelper Packages.com.glideapp.servicecatalog.CalculationHelper

GlideappCart Packages.com.glideapp.servicecatalog.Cart

GlideappCartItem Packages.com.glideapp.servicecatalog.CartItem

GlideappCatalogCategoryBatcher Packages.com.glideapp.servicecatalog.CatalogCategoryBatcher

GlideappCatalogItem Packages.com.glideapp.servicecatalog.CatalogItem

GlideappCategory Packages.com.glideapp.servicecatalog.Category

GlideappCategoryPopper Packages.com.glideapp.servicecatalog.CategoryPopper

GlideappCatItemPopper Packages.com.glideapp.servicecatalog.CatItemPopper

GlideappChartParameters Packages.com.glideapp.chart.ChartParameters

GlideappChatRoom Packages.com.glideapp.live.db.ChatRoom

GlideappChatRoom$Error Packages.com.glideapp.live.db.ChatRoom.Error

GlideappCheckBoxQuestion Packages.com.glideapp.questionset.CheckBoxQuestion

GlideappCMDBHelper Packages.com.glideapp.ecc.CMDBHelper

GlideappCMDBSoftwareHelper Packages.com.glideapp.ecc.CMDBSoftwareHelper

GlideappContainerAwareQuestionSet Packages.com.glideapp.questionset.ContainerAwareQuestionSe

GlideappContextDiagramProcessor Packages.com.glideapp.workflow.ui.ContextDiagramProcessor

GlideappDateQuestion Packages.com.glideapp.questionset.DateQuestion

GlideappDateTimeQuestion Packages.com.glideapp.questionset.DateTimeQuestion

GlideappDeliveryPlan Packages.com.glideapp.servicecatalog.DeliveryPlan

GlideappECCInputMessage Packages.com.glideapp.ecc.ECCInputMessage

GlideappECCOutputMessage Packages.com.glideapp.ecc.ECCOutputMessage

GlideappECCQueueConnector Packages.com.glideapp.ecc.ECCQueueConnector

GlideappECCQueueProcessor Packages.com.glideapp.ecc.ECCQueueProcessor

GlideappECCResponseMessage Packages.com.glideapp.ecc.ECCResponseMessage

GlideappExpandableText Packages.com.glideapp.live_feed.HTMLTransformers.Expandabl

GlideappExpertPanelCatalogOrder Packages.com.glideapp.servicecatalog.ExpertPanelCatalogOrde

GlideappFixes Packages.com.glideapp.servicecatalog.Fixes

GlideappHome Packages.com.glideapp.home.Home

GlideappHomePage Packages.com.glideapp.home.HomePage

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 296

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideappHomePageFactory Packages.com.glideapp.home.HomePageFactory

GlideappIECC Packages.com.glideapp.ecc.IECC

GlideappIOUpgrade Packages.com.glideapp.servicecatalog.IOUpgrade

GlideappItemOptionsQuestionSet Packages.com.glideapp.servicecatalog.ItemOptionsQuestionSe

GlideappJMSECCReceiver Packages.com.glideapp.jms.JMSECCReceiver

GlideappJMSECCSender Packages.com.glideapp.jms.JMSECCSender

GlideappKBIncludes Packages.com.glideapp.knowledge.KBIncludes

GlideApplication Packages.com.glide.sys.Application

GlideApplicationModule Packages.com.glide.processors.ApplicationModule

GlideappListCollectorQuestion Packages.com.glideapp.questionset.ListCollectorQuestion

GlideappLiveFeedEventHandler Packages.com.glideapp.live_feed.LiveFeedEventHandler

GlideappLiveFeedJournalWriter Packages.com.glideapp.live_feed.LiveFeedJournalWriter

GlideappLiveFeedUIAction Packages.com.glideapp.live_feed.LiveFeedUIAction

GlideappLiveProfile Packages.com.glideapp.live_common.LiveProfile

GlideappLiveUtils Packages.com.glideapp.live.LiveUtils

GlideappLookupSelectQuestion Packages.com.glideapp.questionset.LookupSelectQuestion

GlideappMessageTag Packages.com.glideapp.live_feed.MessageTag

GlideappOrderGuide Packages.com.glideapp.servicecatalog.OrderGuide

GlideappProcessQueue Packages.com.glideapp.ecc.ccmdb.ProcessQueue

GlideappQuestion Packages.com.glideapp.questionset.Question

GlideappQuestionChoice Packages.com.glideapp.questionset.QuestionChoice

GlideappQueueHelper Packages.com.glideapp.ecc.QueueHelper

GlideappQueueReader Packages.com.glideapp.ecc.QueueReader

GlideappReferenceQuestion Packages.com.glideapp.questionset.ReferenceQuestion

GlideappRequestItemWorkflow Packages.com.glideapp.servicecatalog.RequestItemWorkflow

GlideappRequestNew Packages.com.glideapp.servicecatalog.RequestNew

GlideappScriptHelper Packages.com.glideapp.servicecatalog.ScriptHelper

GlideappSecurityMask Packages.com.glideapp.servicecatalog.SecurityMask

GlideappSequencedQuestionSet Packages.com.glideapp.questionset.SequencedQuestionSet

GlideappTaskApprovalHelper Packages.com.glideapp.servicecatalog.TaskApprovalHelper

GlideappTimeAgo Packages.com.glideapp.live_feed.TimeAgo

GlideappUpdateVersion Packages.com.glideapp.version.UpdateVersion

GlideappUpgradeQuestions Packages.com.glideapp.survey.UpgradeQuestions

GlideappValveProcessor Packages.com.glideapp.servicecatalog.valve.ValveProcessor

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 297

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideappVariable Packages.com.glideapp.servicecatalog.variables.Variable

GlideappVariablePoolQuestionSet Packages.com.glideapp.servicecatalog.variables.VariablePoolQu

GlideappWizardIntercept Packages.com.glideapp.wizard.WizardIntercept

GlideappWMILoader Packages.com.glideapp.ecc.WMILoader

GlideappWorkflow Packages.com.glideapp.workflow.Workflow

GlideappWorkflowHelper Packages.com.glideapp.workflow.WorkflowHelper

GlideappYesNoQuestion Packages.com.glideapp.questionset.YesNoQuestion

GlideAQueryExplanation Packages.com.glide.db.explain.AQueryExplanation

GlideArchiver Packages.com.glide.db.auxiliary.Archiver

GlideArchiveRecord Packages.com.glide.db.auxiliary.ArchiveRecord

GlideArchiveRestore Packages.com.glide.db.auxiliary.ArchiveRestore

GlideArchiveStatus Packages.com.glide.db.auxiliary.ArchiveStatus

GlideArchiveTable Packages.com.glide.db.auxiliary.ArchiveTable

GlideARecurrence Packages.com.glide.schedule.recurrence.ARecurrence

GlideAttachmentIndexDocument Packages.com.glide.lucene.attachments.AttachmentIndexDocum

GlideAttachmentIndexTypes Packages.com.glide.lucene.attachments.AttachmentIndexTypes

GlideAttributes Packages.com.glide.util.GlideAttributes

GlideAuditDelete Packages.com.glide.audit.AuditDelete

GlideAuditor Packages.com.glide.script.Auditor

GlideAutomationEncrypter Packages.com.glide.util.AutomationEncrypter

GlideBaseTag Packages.com.glide.ui.jelly.tags.BaseTag

GlideBootstrap Packages.com.glide.db.impex.Bootstrap

GlideBoundedIntProperty Packages.com.glide.util.BoundedIntProperty

GlideCacheManager Packages.com.glide.sys.cache.CacheManager

GlideCalendar Packages.com.glide.schedule.GlideCalendar

GlideCalendarWeekEntry Packages.com.glide.calendar.GlideCalendarWeekEntry

GlideCanceledUITransaction Packages.com.glide.ui.CanceledUITransaction

GlideCascadeFromDelete Packages.com.glide.db.CascadeFromDelete

GlideCatalogCloneWorker Packages.com.glide.catalog.cloner.CatalogCloneWorker

GlideChannel Packages.com.glide.channel.Channel

GlideChannelManager Packages.com.glide.channel.ChannelManager

GlideChannelMessage Packages.com.glide.channel.ChannelMessage

GlideChartFieldColors Packages.com.glide.ui.chart.dataset.ChartFieldColors

GlideChartGeneratorFactory Packages.com.glide.ui.chart.ChartGeneratorFactory

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 298

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideChartUtil Packages.com.glide.ui.chart.dataset.ChartUtil

GlideChartValue Packages.com.glide.ui.chart.dataset.ChartValue

GlideChecksum Packages.com.glide.util.Checksum

GlideChoice Packages.com.glide.choice.Choice

GlideChoiceList Packages.com.glide.choice.ChoiceList

GlideChoiceListGenerator Packages.com.glide.choice.ChoiceListGenerator

GlideChoiceListSet Packages.com.glide.choice.ChoiceListSet

GlideChoiceListUpdateSaver Packages.com.glide.update.saver.ChoiceListUpdateSaver

GlideClientBrowserTimes Packages.com.glide.client_transaction.ClientBrowserTimes

GlideClientNetworkTimes Packages.com.glide.client_transaction.ClientNetworkTimes

GlideClusterMessage Packages.com.glide.cluster.ClusterMessage

GlideClusterState Packages.com.glide.cluster.ClusterState

GlideClusterSynchronizer Packages.com.glide.cluster.ClusterSynchronizer

GlideCMSLinkHelper Packages.com.glide.cms.CMSLinkHelper

GlideCMSPageLink Packages.com.glide.cms.CMSPageLink

GlideCollectionEnumerator Packages.com.glide.util.CollectionEnumerator

GlideCollectionQueryCalculator Packages.com.glide.ui.CollectionQueryCalculator

GlideCollisionDetector Packages.com.glide.update.collisions.CollisionDetector

GlideColumnAttributes Packages.com.glide.db.impex.ColumnAttributes

GlideCompanyResolver Packages.com.glide.misc.CompanyResolver

GlideCompiler Packages.com.glide.script.Compiler

GlideCompositeElement Packages.com.glide.db.CompositeElement

GlideConfiguration Packages.com.glide.notification.Configuration

GlideContentConfig Packages.com.glide.cms.ContentConfig

GlideContentPage Packages.com.glide.cms.ContentPage

GlideContentSite Packages.com.glide.cms.ContentSite

GlideContentType Packages.com.glide.cms.ContentType

GlideContextMenu Packages.com.glide.db_context_menu.ContextMenu

GlideContextMenuItem Packages.com.glide.db_context_menu.ContextMenuItem

GlideContextualSecurityManager Packages.com.glide.sys.security.ContextualSecurityManager

GlideController Packages.com.glide.script.GlideController

GlideConverter Packages.com.glide.currency.Converter

GlideCookieMan Packages.com.glide.ui.CookieMan

GlideCounter Packages.com.glide.util.Counter

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 299

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideCredentials Packages.com.glide.communications.crypto.Credentials

GlideCryptoService Packages.com.glide.security.CryptoService

GlideCSVExporter Packages.com.glide.generators.CSVExporter

GlideCustomerScriptFixer Packages.com.glide.script.api.CustomerScriptFixer

GlideDatabaseVerifier Packages.com.glide.db.DatabaseVerifier

GlideDatabaseViewLink Packages.com.glide.database_views.DatabaseViewLink

GlideDataSource Packages.com.glide.db.impex.datasource.DataSource

GlideDate Packages.com.glide.glideobject.GlideDate

GlideDateTime Packages.com.glide.glideobject.GlideDateTime

GlideDateUtil Packages.com.glide.util.DateUtil

GlideDBAction Packages.com.glide.db.DBAction

GlideDBAggregateQuery Packages.com.glide.db.DBAggregateQuery

GlideDBAggregateUtil Packages.com.glide.db.DBAggregateUtil

GlideDBCategoryDebug Packages.com.glide.secondary_db_pools.DBCategoryDebug

GlideDBChangeManager Packages.com.glide.db.change.DBChangeManager

GlideDBCompositeAction Packages.com.glide.db.DBCompositeAction

GlideDBConfiguration Packages.com.glide.db.DBConfiguration

GlideDBConfigurationManager Packages.com.glide.db.DBConfigurationManager

GlideDBConfigurationManagerEventHandler Packages.com.glide.db.DBConfigurationManagerEventHandler

GlideDBConfigurationParms Packages.com.glide.db.DBConfigurationParms

GlideDBConfigurationV2Migrator Packages.com.glide.db.DBConfigurationV2Migrator

GlideDBConnection Packages.com.glide.db.pool.DBConnection

GlideDBConnectionPool Packages.com.glide.db.pool.DBConnectionPool

GlideDBConnectionPooler Packages.com.glide.db.pool.DBConnectionPooler

GlideDBDelete Packages.com.glide.db.DBDelete

GlideDBI Packages.com.glide.db.DBI

GlideDBImageProvider Packages.com.glide.db_image.DBImageProvider

GlideDBIMySQL Packages.com.glide.db.rdbms.mysql.DBIMySQL

GlideDBIndex Packages.com.glide.db.DBIndex

GlideDBKeyStoreFactory Packages.com.glide.certificates.DBKeyStoreFactory

GlideDBMacro Packages.com.glide.ui.jelly.tags.form.DBMacro

GlideDBMicroStats Packages.com.glide.db.DBMicroStats

GlideDBMultiTargetAction Packages.com.glide.db.DBMultiTargetAction

GlideDBObjectManager Packages.com.glide.db.DBObjectManager

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 300

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideDBObjectToken Packages.com.glide.db.DBObjectToken

GlideDBPoolTest Packages.com.glide.secondary_db_pools.DBPoolTest

GlideDBPropertiesConfig Packages.com.glide.db.DBPropertiesConfig

GlideDBQuery Packages.com.glide.db.DBQuery

GlideDBTypes Packages.com.glide.db.DBTypes

GlideDBUpdate Packages.com.glide.db.DBUpdate

GlideDBUtil Packages.com.glide.db.DBUtil

GlideDBView Packages.com.glide.db.DBView

GlideDebugEvaluator Packages.com.glide.jsdebug.DebugEvaluator

GlideDefaultUpdateSaver Packages.com.glide.update.saver.DefaultUpdateSaver

GlideDiagram Packages.com.glide.diagrammer.Diagram

GlideDiagramAction Packages.com.glide.diagrammer.DiagramAction

GlideDiagramEdge Packages.com.glide.diagrammer.DiagramEdge

GlideDiagramElement Packages.com.glide.diagrammer.DiagramElement

GlideDiagramNode Packages.com.glide.diagrammer.DiagramNode

GlideDistUpgradeRunner Packages.com.glide.dist.upgrade.runner.DistUpgradeRunner

GlideDocument Packages.com.glide.util.GlideDocument

GlideDomain Packages.com.glide.db.domain.Domain

GlideDomainDisplay Packages.com.glide.db.domain.DomainDisplay

GlideDomainHierarchy Packages.com.glide.db.domain.DomainHierarchy

GlideDomainNumberProvider Packages.com.glide.db.domain.DomainNumberProvider

GlideDomainPathDisplay Packages.com.glide.db.domain.DomainPathDisplay

GlideDomainPathProvider Packages.com.glide.db.domain.DomainPathProvider

GlideDomainSpoolProvider Packages.com.glide.db.domain.DomainSpoolProvider

GlideDomainSupport Packages.com.glide.db.domain.DomainSupport

GlideDomainTree Packages.com.glide.db.domain.DomainTree

GlideDomainUtil Packages.com.glide.db.domain.DomainUtil

GlideDomainValidator Packages.com.glide.db.domain.DomainValidator

GlideDuration Packages.com.glide.glideobject.GlideDuration

GlideECBDownloader Packages.com.glide.currency.ECBDownloader

GlideECCQueueTransformer Packages.com.glide.db.impex.ECCQueueTransformer

GlideElement Packages.com.glide.script.GlideElement

GlideElementDescriptor Packages.com.glide.db.ElementDescriptor

GlideElementIterator Packages.com.glide.util.ElementIterator

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 301

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideElementUserImage Packages.com.glide.script.glide_elements.GlideElementUserIma

GlideElementXMLSerializer Packages.com.glide.script.GlideElementXMLSerializer

GlideEmail Packages.com.glide.notification.Email

GlideEmailAction Packages.com.glide.notification.outbound.EmailAction

GlideEmailFormatter Packages.com.glide.notification.outbound.EmailFormatter

GlideEmailInbound Packages.com.glide.notification.inbound.EmailInbound

GlideEmailOutbound Packages.com.glide.notification.outbound.EmailOutbound

GlideEmailReader Packages.com.glide.notification.inbound.EmailReader

GlideEmailSender Packages.com.glide.notification.outbound.EmailSender

GlideEmailWatermark Packages.com.glide.notification.EmailWatermark

GlideEmitter Packages.com.glide.ui.jelly.Emitter

GlideEncrypter Packages.com.glide.util.Encrypter

GlideEncryptionContext Packages.com.glide.sys.EncryptionContext

GlideEncryptionContextCipher Packages.com.glide.sys.security.EncryptionContextCipher

GlideEncryptionWrapperDB Packages.com.glide.sys.security.EncryptionWrapperDB

GlideEncryptionWrapperDBAdmin Packages.com.glide.sys.security.EncryptionWrapperDBAdmin

GlideEncryptionWrapperNAE Packages.com.glide.sys.security.EncryptionWrapperNAE

GlideEncryptionWrapperNAEAdmin Packages.com.glide.sys.security.EncryptionWrapperNAEAdmin

GlideEscalationManager Packages.com.glide.escalation.EscalationManager

GlideEscalationTimerJobMarkII Packages.com.glide.job.EscalationTimerJobMarkII

GlideEvaluator Packages.com.glide.script.Evaluator

GlideEvent Packages.com.glide.policy.Event

GlideEventManager Packages.com.glide.policy.EventManager

GlideExcelExporter Packages.com.glide.generators.ExcelExporter

GlideExcelLoader2 Packages.com.glide.db.impex.ExcelLoader2

GlideExecutionPlan Packages.com.glide.execution_plan.ExecutionPlan

GlideExpressionWrapper Packages.com.glide.ui.jelly.GlideExpressionWrapper

GlideExtensionPoint Packages.com.glide.sys.ExtensionPoint

GlideFieldList Packages.com.glide.processors.FieldList

GlideFile Packages.com.glide.script.proxy.File

GlideFileUtil Packages.com.glide.util.FileUtil

GlideFilter Packages.com.glide.script.Filter

GlideFilterList Packages.com.glide.script.FilterList

GlideFixCatalogPlans Packages.com.glide.fixes.FixCatalogPlans

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 302

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideFixDeliveryPlans Packages.com.glide.fixes.FixDeliveryPlans

GlideFixGroups Packages.com.glide.fixes.FixGroups

GlideFixItemOptionsAgain Packages.com.glide.fixes.FixItemOptionsAgain

GlideFixRules Packages.com.glide.fixes.FixRules

GlideFixSpellCheck Packages.com.glide.fixes.FixSpellCheck

GlideFixStuff Packages.com.glide.fixes.FixStuff

GlideFixUsers Packages.com.glide.fixes.FixUsers

GlideForm Packages.com.glide.ui.GlideForm

GlideFormCommon Packages.com.glide.ui.GlideFormCommon

GlideFormulator Packages.com.glide.ui.GlideFormulator

GlideGauge Packages.com.glide.report.Gauge

GlideGovernor Packages.com.glide.sys.util.Governor

GlideGregorianCalendar Packages.com.glide.util.GlideGregorianCalendar

GlideGroup Packages.com.glide.sys.Group

GlideGroupByListTag Packages.com.glide.ui.jelly.tags.form.GroupByListTag

GlideGuid Packages.com.glide.util.Guid

GlideHierarchicalReference Packages.com.glide.glideobject.HierarchicalReference

GlideHistorySet Packages.com.glide.audit.HistorySet

GlideHistoryTag2 Packages.com.glide.ui.jelly.tags.mergedata.HistoryTag2

GlideHostUtil Packages.com.glide.util.HostUtil

GlideHTTPClient https://www.youtube.com/watch?feature=player_detailpage&v=9

GlideHTTPRequest Packages.com.glide.communications.HTTPRequest

GlideHTTPResponse Packages.com.glide.communications.HTTPResponse

GlideI18NStyle Packages.com.glide.ui.I18NStyle

GlideICALUtil Packages.com.glide.policy.ICALUtil

GlideIConstants Packages.com.glide.util.IConstants

GlideIGlideRecord Packages.com.glide.util.IGlideRecord

GlideImageLoader Packages.com.glide.script.ImageLoader

GlideImpersonate Packages.com.glide.sys.Impersonate

GlideImportLog Packages.com.glide.db.impex.ImportLog

GlideImportMap Packages.com.glide.db.impex.ImportMap

GlideImportMapField Packages.com.glide.db.impex.ImportMapField

GlideImportSet Packages.com.glide.system_import_set.ImportSet

GlideImportSetLoader Packages.com.glide.system_import_set.ImportSetLoader

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 303

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideImportSetRun Packages.com.glide.system_import_set.ImportSetRun

GlideImportSetTransformer Packages.com.glide.system_import_set.ImportSetTransformer

GlideImportSetTransformerWorker Packages.com.glide.system_import_set.ImportSetTransformerW

GlideIndexDescriptor Packages.com.glide.db.IndexDescriptor

GlideIndexUtils Packages.com.glide.db.IndexUtils

GlideIntegerTime Packages.com.glide.glideobject.IntegerTime

GlideInternalElementTypeChoiceList Packages.com.glide.script.InternalElementTypeChoiceList

GlideInternalMonitor Packages.com.glide.ui.monitor.InternalMonitor

GlideIOMonitor Packages.com.glide.ui.monitor.IOMonitor

GlideIOStats Packages.com.glide.db.IOStats

GlideIPAddressUtil Packages.com.glide.util.IPAddressUtil

GlideIQueryCondition Packages.com.glide.util.IQueryCondition

GlideIRow Packages.com.glide.db.meta.IRow

GlideIRQuerySummary Packages.com.glide.db.ir.IRQuerySummary

GlideIRQuerySummarySimple Packages.com.glide.db.ir.IRQuerySummarySimple

GlideISecurityManager Packages.com.glide.sys.security.ISecurityManager

GlideITableIterator Packages.com.glide.db.access.ITableIterator

GlideJDBCLoader Packages.com.glide.db.impex.JDBCLoader

GlideJDBCProbeTestWorker Packages.com.glide.db.impex.JDBCProbeTestWorker

GlideJellyContext Packages.com.glide.ui.jelly.GlideJellyContext

GlideJellyRunner Packages.com.glide.ui.jelly.JellyRunner

GlideJID Packages.com.glide.xmpp.JID

GlideJSTestUtil Packages.com.glide.autotester.JSTestUtil

GlideJSUtil Packages.com.glide.script.JSUtil

GlideLabelEventHandler Packages.com.glide.labels.LabelEventHandler

GlideLabelGenerator Packages.com.glide.db.LabelGenerator

GlideLabelUtil Packages.com.glide.labels.LabelUtil

GlideLDAP Packages.com.glide.sys.ldap.LDAP

GlideLDAPConfig Packages.com.glide.sys.ldap.LDAPConfig

GlideLDAPConfigurations Packages.com.glide.sys.ldap.LDAPConfigurations

GlideLDAPErrorAnalyzer Packages.com.glide.sys.ldap.LDAPErrorAnalyzer

GlideLDAPGroups Packages.com.glide.sys.ldap.LDAPGroups

GlideLDAPRefresh Packages.com.glide.sys.ldap.LDAPRefresh

GlideLDAPResult Packages.com.glide.sys.ldap.LDAPResult

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 304

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideLDAPTarget Packages.com.glide.sys.ldap.LDAPTarget

GlideLDAPTransformQueue Packages.com.glide.sys.ldap.LDAPTransformQueue

GlideLDAPUsers Packages.com.glide.sys.ldap.LDAPUsers

GlideLDAPUserUpdate Packages.com.glide.sys.ldap.LDAPUserUpdate

GlideList Packages.com.glide.glideobject.GlideList

GlideListGroupProperties Packages.com.glide.list_v2.ListGroupProperties

GlideListLabel Packages.com.glide.ui.ListLabel

GlideListM2MBacking Packages.com.glide.glideobject.GlideListM2MBacking

GlideListProperties Packages.com.glide.list_v2.ListProperties

GlideListSearchQuery Packages.com.glide.ui.ListSearchQuery

GlideLoader Packages.com.glide.db.impex.Loader

GlideLoadTestDirector Packages.com.glide.load_test.LoadTestDirector

GlideLocale Packages.com.glide.sys.GlideLocale

GlideLocaleLoader Packages.com.glide.currency.LocaleLoader

GlideLock Packages.com.glide.script.Lock

GlideLog Packages.com.glide.util.Log

GlideLogCleanup Packages.com.glide.util.LogCleanup

GlideLogFileReader Packages.com.glide.log_file.LogFileReader

GlideLRUCache Packages.com.glide.sys.cache.LRUCache

GlideLuceneTextIndexEvent Packages.com.glide.lucene.TextIndexEvent

GlideMarkupWriter Packages.com.glide.util.MarkupWriter

GlideMemoryActive Packages.com.glide.ui.monitor.MemoryActive

GlideMemoryCache Packages.com.glide.ui.monitor.MemoryCache

GlideMemoryRecord Packages.com.glide.script.GlideMemoryRecord

GlideMemorySwap Packages.com.glide.ui.monitor.MemorySwap

GlideMemoryTable Packages.com.glide.util.MemoryTable

GlideMemoryTotal Packages.com.glide.ui.monitor.MemoryTotal

GlideMetaData Packages.com.glide.script.MetaData

GlideMIDServerInfoAccessor Packages.com.glide.script.MIDServerInfoAccessor

GlideMobileExtensions Packages.com.glide.ui.MobileExtensions

GlideModule Packages.com.glide.sys.Module

GlideMultipleAction Packages.com.glide.db.MultipleAction

GlideMultipleDelete Packages.com.glide.db.MultipleDelete

GlideMultipleInsert Packages.com.glide.db.MultipleInsert

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 305

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideMultipleUpdate Packages.com.glide.db.MultipleUpdate

GlideMutex Packages.com.glide.sys.lock.Mutex

GlideMySQLWatch Packages.com.glide.sys.stats.MySQLWatch

GlideNumber Packages.com.glide.script.glide_elements.GlideNumber

GlideNumberManager Packages.com.glide.db.NumberManager

GlideObjectManager Packages.com.glide.glideobject.GlideObjectManager

GlideObjectUtil Packages.com.glide.util.ObjectUtil

GlideOrderingDefinitionCreator Packages.com.glide.sorting.OrderingDefinitionCreator

GlideOrderingManager Packages.com.glide.sorting.OrderingManager

GlideOutputWriter Packages.com.glide.ui.io.GlideOutputWriter

GlideOutputWriterFactory Packages.com.glide.ui.io.GlideOutputWriterFactory

GlideOverLoadedChoices Packages.com.glide.script.OverLoadedChoices

GlidePartitionMonitor Packages.com.glide.ui.monitor.PartitionMonitor

GlidePivotTableSummaryTableWriter Packages.com.glide.ui.chart.dataset.PivotTableSummaryTableWr

GlidePlugin Packages.com.glide.sys.Plugin

GlidePluginManager Packages.com.glide.sys.PluginManager

GlidePluginManagerWorker Packages.com.glide.sys.PluginManagerWorker

GlidePluginUtils Packages.com.glide.sys.PluginUtils

GlidePOP3Reader Packages.com.glide.notification.inbound.POP3Reader

GlidePOP3ReaderJob Packages.com.glide.job.POP3ReaderJob

GlidePopup Packages.com.glide.ui.Popup

GlidePriceGenerator Packages.com.glide.currency.PriceGenerator

GlidePriceLoader Packages.com.glide.currency.PriceLoader

GlideProcessor Packages.com.glide.processors.Processor

GlideProcessRunner Packages.com.glide.util.ProcessRunner

GlideProgressMonitor Packages.com.glide.worker.ProgressMonitor

GlideProgressWorker Packages.com.glide.worker.ProgressWorker

GlideProperties Packages.com.glide.util.GlideProperties

GlidePropertiesDB Packages.com.glide.util.GlidePropertiesDB

GlideProperty Packages.com.glide.util.GlideProperty

GlidePublicPage Packages.com.glide.ui.PublicPage

GlideQueryBreadcrumbs Packages.com.glide.misc.QueryBreadcrumbs

GlideQueryCondition Packages.com.glide.db.conditions.QueryCondition

GlideQueryFormatter Packages.com.glide.ui.jelly.tags.form.QueryFormatter

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 306

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideQueryString Packages.com.glide.db.QueryString

GlideQueryTerm Packages.com.glide.db.QueryTerm

GlideRecord Packages.com.glide.script.GlideRecord

GlideRecordCache Packages.com.glide.sys.RecordCache

GlideRecordEnsurer Packages.com.glide.misc.RecordEnsurer

GlideRecordFactory Packages.com.glide.script.GlideRecordFactory

GlideRecordKeySetLoader Packages.com.glide.script.GlideRecordKeySetLoader

GlideRecordLock Packages.com.glide.script.RecordLock

GlideRecordPopupGenerator Packages.com.glide.calendar.RecordPopupGenerator

GlideRecordRollback Packages.com.glide.script.GlideRecordRollback

GlideRecordSet Packages.com.glide.script.GlideRecordSet

GlideRecordSimpleSerializer Packages.com.glide.script.GlideRecordSimpleSerializer

GlideRecordXMLSerializer Packages.com.glide.script.GlideRecordXMLSerializer

GlideReferenceField Packages.com.glide.script.ReferenceField

GlideRegexUtil Packages.com.glide.util.RegexUtil

GlideRegisterEscalationEvents Packages.com.glide.fixes.RegisterEscalationEvents

GlideRelatedListReconciler Packages.com.glide.misc.RelatedListReconciler

GlideRelationship Packages.com.glide.sys.Relationship

GlideRelationships Packages.com.glide.db.Relationships

GlideRelationshipUtil Packages.com.glide.sys.RelationshipUtil

GlideRemoteGlideRecord Packages.com.glide.communications.RemoteGlideRecord

GlideRenderProperties Packages.com.glide.ui.RenderProperties

GlideReplaceUpdateFiles Packages.com.glide.util.ReplaceUpdateFiles

GlideReplicationEngine Packages.com.glide.replicator.ReplicationEngine

GlideReport Packages.com.glide.report.Report

GlideReportChoiceList Packages.com.glide.script.ReportChoiceList

GlideReportViewManagement Packages.com.glide.report.ReportViewManagement

GlideRequestMap Packages.com.glide.util.RequestMap

GlideRevertToOutOfBox Packages.com.glide.update.RevertToOutOfBox

GlideRhinoEnvironment Packages.com.glide.script.GlideRhinoEnvironment

GlideRhinoHelper Packages.com.glide.script.GlideRhinoHelper

GlideRhinoScope Packages.com.glide.script.RhinoScope

GlideRhinoScopeHandler Packages.com.glide.script.GlideRhinoScopeHandler

GlideRhinoTestCase Packages.com.glide.autotester.RhinoTestCase

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 307

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideRRDBAlertProcessor Packages.com.glide.rrdb.alerts.RRDBAlertProcessor

GlideRRDBDefinition Packages.com.glide.rrdb.RRDBDefinition

GlideRunScriptJob Packages.com.glide.job.RunScriptJob

GlideSchedule

**-** Packages.com.glide.schedules.Schedule

**-** Packages.java.util.TimeZone

GlideScheduleDateTime Packages.com.glide.glideobject.ScheduleDateTime

GlideScheduleDateTimeSpan Packages.com.glide.schedules.ScheduleDateTimeSpan

GlideScheduleItem Packages.com.glide.schedules.ScheduleItem

GlideScheduler Packages.com.glide.schedule.GlideScheduler

GlideScheduleTimeMap Packages.com.glide.schedules.ScheduleTimeMap

GlideScheduleTimeSpan Packages.com.glide.schedules.ScheduleTimeSpan

GlideScriptChoiceList Packages.com.glide.script.ChoiceList

GlideScriptedProgressWorker Packages.com.glide.worker.ScriptedProgressWorker

GlideScriptEvaluator Packages.com.glide.script.ScriptEvaluator

GlideScriptGlobals Packages.com.glide.script.GlideScriptGlobals

GlideScriptListener Packages.com.glide.listener.ScriptListener

GlideScriptProcessor Packages.com.glide.processors.ScriptProcessor

GlideScriptRecordUtil Packages.com.glide.script.GlideRecordUtil

GlideScriptSystemUtilDB Packages.com.glide.script.GlideSystemUtilDB

GlideScriptViewManager Packages.com.glide.ui.ViewManager

GlideScriptWriter Packages.com.glide.script.ScriptWriter

GlideSearchQueryFormatter Packages.com.glide.text_search.SearchQueryFormatter

GlideSecondaryDatabaseBehindnessChecker Packages.com.glide.secondary_db_pools.SecondaryDatabaseB

GlideSecondaryDatabaseConfiguration Packages.com.glide.secondary_db_pools.SecondaryDatabaseC

GlideSecurityManager Packages.com.glide.sys.security.GlideSecurityManager

GlideSecurityQueryCalculator Packages.com.glide.sys.security.SecurityQueryCalculator

GlideSecurityUtils Packages.com.glide.util.SecurityUtils

GlideSelfCleaningMutex Packages.com.glide.sys.lock.SelfCleaningMutex

GlideServiceAPIWrapper Packages.com.glide.service_api.ServiceAPIWrapper

GlideServlet Packages.com.glide.ui.GlideServlet

GlideServletRequest Packages.com.glide.ui.GlideServletRequest

GlideServletResponse Packages.com.glide.ui.GlideServletResponse

GlideServletStatus Packages.com.glide.ui.ServletStatus

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 308

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideSession Packages.com.glide.sys.GlideSession

GlideSessionDebug Packages.com.glide.sys.SessionDebug

GlideSessions Packages.com.glide.ui.Sessions

GlideSessionSandbox Packages.com.glide.script.GlideSessionSandbox

GlideShellCommand Packages.com.glide.util.ShellCommand

GlideSimmerDown Packages.com.glide.db.change.command.SimmerDown

GlideSimmerUp Packages.com.glide.db.change.command.SimmerUp

GlideSimpleDateFormatEx

**-** Packages.com.glide.util.SimpleDateFormatEx

**-** Packages.com.glide.util.SimpleDateFormat

##### Note: The Packages.com.glide.util.SimpleDateFormatEx pa

the Packages.com.glide.util.SimpleDateFormat package.

GlideSimpleHTTPClient Packages.com.glide.communications.SimpleHTTPClient

GlideSimpleScriptListener Packages.com.glide.listener.SimpleScriptListener

GlideSMTPConnection Packages.com.glide.notification.outbound.SMTPConnection

GlideSMTPSender Packages.com.glide.notification.outbound.SMTPSender

GlideSMTPSenderJob Packages.com.glide.job.SMTPSenderJob

GlideSOAPDocument Packages.com.glide.communications.soap.SOAPDocument

GlideSOAPRequest Packages.com.glide.communications.soap.SOAPRequest

GlideSOAPResponse Packages.com.glide.communications.soap.SOAPResponse

GlideSOAPSecurity Packages.com.glide.processors.soap.SOAPSecurity

GlideSOAPSigner Packages.com.glide.communications.soap.SOAPSigner

GlideSocket Packages.com.glide.script.proxy.Socket

GlidesoftGlideAttributesImpl Packages.com.glidesoft.util.xml.GlideAttributesImpl

GlidesoftXMLMemoryTable Packages.com.glidesoft.util.xml.XMLMemoryTable

GlideSQLChildMonitor Packages.com.glide.monitor.sql.SQLChildMonitor

GlideSQLDebug Packages.com.glide.ui.diagnostics.SQLDebug

GlideSQLDeleteMonitor Packages.com.glide.monitor.sql.SQLDeleteMonitor

GlideSQLInsertMonitor Packages.com.glide.monitor.sql.SQLInsertMonitor

GlideSQLResponseMonitor Packages.com.glide.monitor.sql.SQLResponseMonitor

GlideSQLSelectMonitor Packages.com.glide.monitor.sql.SQLSelectMonitor

GlideSQLUpdateMonitor Packages.com.glide.monitor.sql.SQLUpdateMonitor

GlideSSHClient Packages.com.glide.communications.SSHClient

GlideStack Packages.com.glide.sys.GlideStack

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 309

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideStatistician Packages.com.glide.sys.stats.Statistician

GlideStatsInfo Packages.com.glide.monitor.StatsInfo

GlideStatus Packages.com.glide.util.GlideStatus

GlideStopWatch Packages.com.glide.util.StopWatch

GlideStorageUtils Packages.com.glide.db.meta.StorageUtils

GlideStringCache Packages.com.glide.sys.cache.StringCache

GlideStringInputStream Packages.com.glide.util.StringInputStream

GlideStringList Packages.com.glide.collections.StringList

GlideStringUtil Packages.com.glide.util.StringUtil

GlideSubQuery Packages.com.glide.db.conditions.SubQuery

GlideSubstituteURL Packages.com.glide.notification.substitution.SubstituteURL

GlideSummaryTableGroupReader Packages.com.glide.ui.chart.dataset.SummaryTableGroupReade

GlideSummaryTableOrderedReader Packages.com.glide.ui.chart.dataset.SummaryTableOrderedRead

GlideSummaryTableReader Packages.com.glide.ui.chart.dataset.SummaryTableReader

GlideSummaryTableWriter Packages.com.glide.ui.chart.dataset.SummaryTableWriter

GlideSynchronizedLRUCache Packages.com.glide.sys.cache.SynchronizedLRUCache

GlideSysAttachment Packages.com.glide.ui.SysAttachment

GlideSysAttachmentInputStream Packages.com.glide.ui.SysAttachmentInputStream

GlideSysBRThreadMonitor Packages.com.glide.monitor.threads.SysBRThreadMonitor

GlideSysChoice Packages.com.glide.script.SysChoice

GlideSysConcurrencyMonitor Packages.com.glide.monitor.threads.SysConcurrencyMonitor

GlideSysCPUThreadMonitor Packages.com.glide.monitor.threads.SysCPUThreadMonitor

GlideSysDateUtil Packages.com.glide.sys.util.SysDateUtil

GlideSysDBThreadMonitor Packages.com.glide.monitor.threads.SysDBThreadMonitor

GlideSysField Packages.com.glide.db.SysField

GlideSysFileUtil Packages.com.glide.sys.util.SysFileUtil

GlideSysForm Packages.com.glide.ui.SysForm

GlideSysForms Packages.com.glide.ui.SysForms

GlideSysList Packages.com.glide.ui.SysList

GlideSysListControl Packages.com.glide.ui.SysListControl

GlideSysLog Packages.com.glide.sys.SysLog

GlideSYSMany2Many Packages.com.glide.db.SYSMany2Many

GlideSysMessage Packages.com.glide.ui.SysMessage

GlideSysNetThreadMonitor Packages.com.glide.monitor.threads.SysNetThreadMonitor

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 310

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideSysRelatedList Packages.com.glide.ui.SysRelatedList

GlideSysSection Packages.com.glide.ui.SysSection

GlideSysSemaphore Packages.com.glide.sys.util.SysSemaphore

GlideSystem Packages.com.glide.script.GlideSystem

GlideSystemDateUtil Packages.com.glide.script.system.GlideSystemDateUtil

GlideSystemUtil Packages.com.glide.util.SystemUtil

GlideSystemUtilDB Packages.com.glide.script.system.GlideSystemUtilDB

GlideSystemUtilScript Packages.com.glide.script.system.GlideSystemUtilScript

GlideSysThreadMonitor Packages.com.glide.monitor.threads.SysThreadMonitor

GlideSysUserList Packages.com.glide.ui.SysUserList

GlideTable Packages.com.glide.db.meta.Table

GlideTableChoiceList Packages.com.glide.script.TableChoiceList

GlideTableCleaner Packages.com.glide.misc.TableCleaner

GlideTableCleanerJob Packages.com.glide.job.TableCleanerJob

GlideTableCreator Packages.com.glide.db.impex.TableCreator

GlideTableDescriptor Packages.com.glide.db.TableDescriptor

GlideTableGroupMover Packages.com.glide.db.auxiliary.TableGroupMover

GlideTableManager Packages.com.glide.db.TableManager

GlideTableMover Packages.com.glide.db.auxiliary.TableMover

GlideTableParentChange Packages.com.glide.db.table.TableParentChange

GlideTableParentColumnChange Packages.com.glide.db.table.TableParentColumnChange

GlideTaskToken Packages.com.glide.execution_plan.TaskToken

GlideTemplate Packages.com.glide.script.Template

GlideTestAgent Packages.com.glide.autotester.GlideTestAgent

GlideTextIndexEvent Packages.com.glide.ts.event.TextIndexEvent

GlideThreadAttributes Packages.com.glide.ui.GlideThreadAttributes

GlideThreadUtil Packages.com.glide.util.ThreadUtil

GlideTime Packages.com.glide.glideobject.GlideTime

GlideTimelineFrameSeparator Packages.com.glide.schedules.TimelineFrameSeparator

GlideTimelineItem Packages.com.glide.schedules.TimelineItem

GlideTimelineSpan Packages.com.glide.schedules.TimelineSpan

GlideTomcatHelper Packages.com.glide.startup.TomcatHelper

GlideTransaction Packages.com.glide.sys.Transaction

GlideTransactionManager Packages.com.glide.sys.TransactionManager

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 311

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideTransferAuditDataHelper Packages.com.glide.audit.TransferAuditDataHelper

GlideTransformer Packages.com.glide.db.impex.transformer.Transformer

GlideTreePicker Packages.com.glide.ui.TreePicker

GlideTSAnalysisViewer Packages.com.glide.ts.cluster.TSAnalysisViewer

GlideTSAnalyticsProcessor Packages.com.glide.ts.cluster.TSAnalyticsProcessor

GlideTSChainsHandler Packages.com.glide.ts.trends.TSChainsHandler

GlideTSChainsLoader Packages.com.glide.ts.trends.TSChainsLoader

GlideTSChainsPusher Packages.com.glide.ts.trends.TSChainsPusher

GlideTSChainsSummarizer Packages.com.glide.ts.trends.TSChainsSummarizer

GlideTSClusterDefinitions Packages.com.glide.ts.cluster.TSClusterDefinitions

GlideTSDebug Packages.com.glide.ts.util.TSDebug

GlideTSDidYouMean Packages.com.glide.ts.util.TSDidYouMean

GlideTSGlobalKeywordSummarizer Packages.com.glide.ts.trends.TSGlobalKeywordSummarizer

GlideTSIndexStatistician Packages.com.glide.ts.stats.TSIndexStatistician

GlideTSIndexStopGenerator Packages.com.glide.ts.stats.TSIndexStopGenerator

GlideTSIndexTables Packages.com.glide.ts.indexer.TSIndexTables

GlideTSKeywordHandler Packages.com.glide.ts.trends.TSKeywordHandler

GlideTSKeywordLoader Packages.com.glide.ts.trends.TSKeywordLoader

GlideTSKeywordPusher Packages.com.glide.ts.trends.TSKeywordPusher

GlideTSMoversViewer Packages.com.glide.ts.cluster.TSMoversViewer

GlideTSSearchStatistician Packages.com.glide.ts.stats.TSSearchStatistician

GlideTSSearchSummary Packages.com.glide.ts.trends.TSSearchSummary

GlideTSTopSearches Packages.com.glide.ts.util.TSTopSearches

GlideTSUtil Packages.com.glide.ts.util.TSUtil

GlideTSVersion Packages.com.glide.ts.TSVersion

GlideUIAction Packages.com.glide.ui.action.UIAction

GlideUISession Packages.com.glide.ui.Session

GlideUnloader Packages.com.glide.db.impex.Unloader

GlideUpdateManager2 Packages.com.glide.update.UpdateManager2

GlideUpdateSet Packages.com.glide.update.UpdateSet

GlideUpdateSetController Packages.com.glide.system_update_set.UpdateSetController

GlideUpdateSetPreviewer Packages.com.glide.update.UpdateSetPreviewer

GlideUpdateSetWorker Packages.com.glide.update.UpdateSetWorker

GlideUpdateSyncher Packages.com.glide.policy.UpdateSyncher

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 312

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

GlideUpdateTableChoiceList Packages.com.glide.script.UpdateTableChoiceList

GlideUpgrade Packages.com.glide.sys.Upgrade

GlideUpgradeArtifactManager Packages.com.glide.misc.UpgradeArtifactManager

GlideUpgradeLog Packages.com.glide.update.UpgradeLog

GlideUpgradeMonitor Packages.com.glide.update.UpgradeMonitor

GlideURI Packages.com.glide.ui.GlideURI

GlideURL Packages.com.glide.util.GlideURL

GlideURLUTF8Encoder Packages.com.glide.util.URLUTF8Encoder

GlideURLUtil Packages.com.glide.util.URLUtil

GlideUser Packages.com.glide.sys.User

GlideUserAuthenticator Packages.com.glide.sys.UserAuthenticator

GlideUserGroup Packages.com.glide.sys.UserGroup

GlideUtil Packages.com.glide.util.GlideUtil

GlideViewRuleNavigator Packages.com.glide.ui.ViewRuleNavigator

GlideWarDeleter Packages.com.glide.misc.WarDeleter

GlideWarDownloader Packages.com.glide.misc.WarDownloader

GlideWhiteListManager Packages.com.glide.script.api.GlideWhiteListManager

GlideWikiModel Packages.com.glide.wiki.GlideWikiModel

GlideWorkerThread Packages.com.glide.worker.WorkerThread

GlideWorkerThreadManager Packages.com.glide.sys.WorkerThreadManager

GlideWSClient Packages.com.glide.util.WSClient

GlideWSDefinition Packages.com.glide.wsdlreader.WSDefinition

GlideWSDLReader Packages.com.glide.wsdlreader.GlideWSDLReader

GlideXMLChoiceListSerializer Packages.com.glide.choice.XMLChoiceListSerializer

GlideXMLDocument Packages.com.glide.util.XMLDocument

GlideXMLElementIterator Packages.com.glide.util.XMLElementIterator

GlideXMLGlideRecordSerializer Packages.com.glide.processors.xmlhttp.XMLGlideRecordSerializ

GlideXMLParameters Packages.com.glide.util.XMLParameters

GlideXMLStats Packages.com.glide.ui.XMLStats

GlideXMLSysMetaSerializer Packages.com.glide.processors.xmlhttp.XMLSysMetaSerializer

GlideXMLUtil Packages.com.glide.util.XMLUtil

GlideZipUtil Packages.com.glide.util.ZipUtil

RhinoEnvironment Packages.com.glide.script.RhinoEnvironment

RhinoHelper Packages.com.glide.script.RhinoHelper

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 313

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

SecurelyAccess Packages.com.glide.sys.util.SecurelyAccess

ServiceAPI Packages.com.glide.service_api.ServiceAPI

SncAddress32Bit Packages.com.snc.commons.networks.Address32Bit

SncAliasApplier Packages.com.snc.field_normalization.AliasApplier

SncAppFiles Packages.com.snc.apps.api.AppFiles

SncApplicationFileListener Packages.com.snc.apps.db.ApplicationFileListener

SncAppsAccess Packages.com.snc.apps.api.AppsAccess

SncAppsUI Packages.com.snc.apps.api.AppsUI

SncASensor Packages.com.snc.discovery.sensor.ASensor

SncAuthentication Packages.com.snc.authentication.digest.Authentication

SncBaselineCMDB Packages.com.snc.cmdb.BaselineCMDB

SncBulkCopy Packages.com.snc.ha.clone.BulkCopy

SncClassifiedProcess Packages.com.snc.discovery.sensor.ClassifiedProcess

SncClassify Packages.com.snc.discovery.sensor.snmp.Classify

SncCloneController Packages.com.snc.ha.clone.CloneController

SncCloneInstance Packages.com.snc.ha.clone.instance.Instance

SncCloneLogger Packages.com.snc.ha.clone.CloneLogger

SncCloneTask Packages.com.snc.ha.clone.CloneTask

SncCloneUtils Packages.com.snc.ha.clone.CloneUtils

SncConfiguration Packages.com.snc.field_normalization.db.Configuration

SncConfigurations Packages.com.snc.field_normalization.Configurations

SncConnectionTest Packages.com.snc.ha.connectivity.ConnectionTest

SncDBChangeManagerFactoryHA Packages.com.snc.db.clone.change.DBChangeManagerFactory

SncDeviceHistory Packages.com.snc.discovery.logging.DeviceHistory

SncDiscoveryCancel Packages.com.snc.discovery.DiscoveryCancel

SncDiscoveryClassification Packages.com.snc.discovery.DiscoveryClassification

SncDiscoveryLog Packages.com.snc.discovery.logging.DiscoveryLog

SncDiscoveryRanges Packages.com.snc.commons.networks.DiscoveryRanges

SncDiscoveryRangesDB Packages.com.snc.discovery.DiscoveryRangesDB

SncDiscoveryReconciler Packages.com.snc.discovery.database.DiscoveryReconciler

SncDiscoverySNMPClassification Packages.com.snc.discovery.sensor.snmp.DiscoverySNMPClass

SncDiscoveryUtils Packages.com.snc.discovery.DiscoveryUtils

SncDropBackupTablesTask Packages.com.snc.ha.clone.instance.DropBackupTablesTask

SncDropTablesTask Packages.com.snc.ha.clone.DropTablesTask

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 314

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

SncEC2Properties Packages.com.snc.ec2.EC2Properties

SncECMDBUtil Packages.com.snc.cmdb.ECMDBUtil

SncElrondClient Packages.com.snc.customer_logon.ElrondClient

SncExpert Packages.com.snc.expert.Expert

SncExpertInstance Packages.com.snc.expert.ExpertInstance

SncExpertPanel Packages.com.snc.expert.ExpertPanel

SncExtantDataJob Packages.com.snc.field_normalization.db.ExtantDataJob

SncExtantDataJobState Packages.com.snc.field_normalization.ExtantDataJobState

SncFailoverController Packages.com.snc.da.gateway.replication.FailoverController

SncFileTree Packages.com.snc.apps.file.FileTree

SncGatewayCache Packages.com.snc.da.gateway.GatewayCache

SncGatewayClone Packages.com.snc.da.gateway.clone.GatewayClone

SncGatewayConnectivity Packages.com.snc.da.gateway.GatewayConnectivity

SncGatewayPluginStartup Packages.com.snc.da.gateway.replication.GatewayPluginStartup

SncGatewayTruncateHierarchy Packages.com.snc.da.gateway.clone.GatewayTruncateHierarchy

SncGlideGateways Packages.com.snc.da.gateway.GlideGateways

SncHAClone Packages.com.snc.ha.clone.HAClone

SncHAConnectionTest Packages.com.snc.ha.connectivity.HAConnectionTest

SncHADatabaseCheck Packages.com.snc.ha.tablecheck.HADatabaseCheck

SncHAPairingUtils Packages.com.snc.ha.HAPairingUtils

SncHAReplicationController Packages.com.snc.ha.HAReplicationController

SncHAReplicationQueueSnapshotBuilder Packages.com.snc.ha.tablecheck.HAReplicationQueueSnapsho

SncHATableCheck Packages.com.snc.ha.tablecheck.HATableCheck

SncHATableCheckThread Packages.com.snc.ha.tablecheck.HATableCheckThread

SncHATableQuickCheck Packages.com.snc.ha.tablecheck.HATableQuickCheck

SncHATableRepair Packages.com.snc.ha.tablecheck.HATableRepair

SncHAUtils Packages.com.snc.ha.HAUtils

SncHostname Packages.com.snc.discovery.utils.Hostname

SncInstanceClone Packages.com.snc.ha.clone.instance.InstanceClone

SncInstanceConnectionTest Packages.com.snc.ha.connectivity.InstanceConnectionTest

SncInstanceRollback Packages.com.snc.ha.clone.instance.InstanceRollback

SncIPAddressV4 Packages.com.snc.commons.networks.IPAddressV4

SncIPAddressV6 Packages.com.snc.commons.networks.IPAddressV6

SncIPAuthenticator Packages.com.snc.ipauthenticator.IPAuthenticator

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 315

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

SncIPIterator Packages.com.snc.commons.networks.IPIterator

SncIPList Packages.com.snc.commons.networks.IPList

SncIPMetaCollection Packages.com.snc.commons.networks.IPMetaCollection

SncIPNetmaskV4 Packages.com.snc.commons.networks.IPNetmaskV4

SncIPNetworkV4 Packages.com.snc.commons.networks.IPNetworkV4

SncIPRangeV4 Packages.com.snc.commons.networks.IPRangeV4

SncJRobinGraphDef Packages.com.snc.jrobin.JRobinGraphDef

SncLayer7Connections Packages.com.snc.discovery.Layer7Connections

SncMACAddress Packages.com.snc.commons.networks.MACAddress

SncMACAddressMfr Packages.com.snc.commons.networks.MACAddressMfr

SncMakeAndModel Packages.com.snc.cmdb.MakeAndModel

SncMIDConfigParameter Packages.com.snc.commons.MIDConfigParameter

SncMIDServerRangesDB Packages.com.snc.discovery.MIDServerRangesDB

SncNormalCoalescer Packages.com.snc.field_normalization.NormalCoalescer

SncNormalizer Packages.com.snc.field_normalization.Normalizer

SncNormalValueChanger Packages.com.snc.field_normalization.NormalValueChanger

SncNotifySNC Packages.com.snc.system.NotifySNC

SncOnCallRotation Packages.com.snc.on_call_rotation.OnCallRotation

SncPendingValueCollector Packages.com.snc.field_normalization.PendingValueCollector

SncPreferences Packages.com.snc.field_normalization.Preferences

SncPrintServerHelper Packages.com.snc.discovery.database.PrintServerHelper

SncProbe Packages.com.snc.discovery.Probe

SncProbeRunTime Packages.com.snc.discovery.perfmon.ProbeRunTime

SncRBSensorProcessor Packages.com.snc.discovery_automation.RBSensorProcessor

SncReadTest Packages.com.snc.ha.ReadTest

SncReclassifyCI Packages.com.snc.cmdb.ReclassifyCI

SncRelationships Packages.com.snc.cmdb.Relationships

SncReplicationAdvisor Packages.com.snc.db.replicate.ReplicationAdvisor

SncReplicationEngine Packages.com.snc.db.replicate.ReplicationEngine

SncReplicationQueue Packages.com.snc.db.replicate.ReplicationQueue

SncRequestCredentials Packages.com.snc.customer_logon.RequestCredentials

SncRrdGlideBackendFactory Packages.com.snc.jrobin.RrdGlideBackendFactory

SncRuleApplier Packages.com.snc.field_normalization.RuleApplier

SncRuleToPending Packages.com.snc.field_normalization.RuleToPending

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 316

GlideScriptable object replacement list (continued)

GlideScriptable Class Packages Call

SncSAMCounter Packages.com.snc.software_asset_management.SAMCounter

SncScheduleDropBackupTablesTask Packages.com.snc.ha.clone.instance.ScheduleDropBackupTable

SncScrapeIANAEnterpriseNumbers Packages.com.snc.discovery.database.ScrapeIANAEnterpriseNu

SncScrapeIEEENICCodes Packages.com.snc.discovery.database.ScrapeIEEENICCodes

SncSendNotificationTask Packages.com.snc.ha.clone.instance.SendNotificationTask

SncSensorProcessor Packages.com.snc.discovery.SensorProcessor

SncSerialNumber Packages.com.snc.discovery.SerialNumber

SncSerialNumberList Packages.com.snc.discovery.SerialNumberList

SncSessionMate Packages.com.snc.discovery.SessionMate

SncSimmerControl Packages.com.snc.ha.clone.instance.SimmerControl

SncTableEditor Packages.com.snc.apps.api.TableEditor

SncTableRotation Packages.com.snc.db.replicate.TableRotation

SncTableRotationExtension Packages.com.snc.db.replicate.TableRotationExtension

SncTableRotationExtensions Packages.com.snc.db.replicate.TableRotationExtensions

SncTableRotationWatcher Packages.com.snc.db.replicate.TableRotationWatcher

SncTransformApplier Packages.com.snc.field_normalization.TransformApplier

SncTreeBuilder Packages.com.snc.apps.tree.TreeBuilder

SncTriggerSynchronizer Packages.com.snc.automation.TriggerSynchronizer

SncValue Packages.com.snc.field_normalization.db.Value

TestExtension Packages.com.glide.junit.misc.TestExtension

UINotification Packages.com.glide.ui.UINotification

Packages Call Removal Tool error types

Possible error types generated by the Packages Call Removal Tool.

Error types

Error message

Description Solution

Class Name Could Not Be Parsed

A line of script has what appears to be a Packages call (for example, the line contains Packages.com.glide) but on examination there is insufficient text to parse out a class name that corresponds to a scriptable object name.

This error type generally does not pre nevertheless flagged as an error in ca a valid class that the parser, for whate parse.

Class Does Not Exist

A line of script has an identifiable Packages call to a Java class that does not exist. This may be because it was incorrectly typed, or because the Java class no longer exists. Either way, the line of script is currently not doing anything and is potentially generating errors whenever it is run.

This error type usually identifies a scr what its author intended, if it ever did should be revisited, and the invalid P

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 317

Error types (continued)

Error message

Description Solution

Class Is Not a Scriptable Class

A line of script has an identifiable Packages call to an existing ServiceNow Java class that is not currently marked as scriptable. The call cannot be replaced, because there is currently no corresponding scriptable name.

To convert this script, either rewrite th not use the Java class or wait until Se a scriptable name for the class.

Class Does Not Have a Scriptable Name

A line of script has an identifiable Packages call to an existing ServiceNow Java class that does not currently have a scriptable name.

This error is less likely to occur than a Scriptable Class error; however, as w this script, either rewrite the script so Java class or wait until ServiceNow, In name for the class.

Variable Name Being Assigned Conflicts With a Scriptable Name

A variable name has the same name as a scriptable name. For example, var GlideSession = Packages.com.glide.sys.GlideSession.get(); would generate this error because the variable name GlideSession is the same as the scriptable name for the GlideSession Java class.

Before this script can be converted, t must be changed wherever it occurs example, the line could be changed t Packages.com.glide.sys.Gl to remove the conflict. Also, be sure t name elsewhere in the script wherev

Internal Error Unable To Find String To Be Replaced

The tool is unable to find the script text it is currently evaluating for Packages call replacement.

This error type is very unlikely. If it do code and correct any errors. If the err open an incident with Technical Supp

#### Web services

HTTP-based web services allow diverse applications to talk to each other. ServiceNow supports both inbound (provider) and outbound (consumer) web services.

##### Inbound web services

Inbound web services allow you to access and modify ServiceNow data using a client application.

**-** REST APIs

**-** Scripted REST APIs

**-** Query record data using the GraphQL API framework

**-** SOAP web service

**-** JSONv2 web service

**-** RSS web service

**-** Scripted SOAP web services

##### Outbound web services

Outbound web services allow you to send SOAP and REST messages to external web service providers.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 318

**-** Outbound SOAP web service

**-** Outbound REST web service

##### Note:

ServiceNow has partnered with Boomi to deliver Boomi API Management, a cloud-based platform that enables customers to discover, manage, secure, and monetize their APIs. Boomi supports full lifecycle API management, including governance, analytics, and API security.

Boomi provides documentation though their own portal, and customers requesting support with Boomi API Management will contact the Boomi support through their standard channels.

To get started, see the Boomi API Management listing on the ServiceNow

® Store , which includes information about entitlements and required plugins, as well as a link to the Boomi API Management documentation.

##### Inbound web services

You can use any of several web services to integrate with ServiceNow applications, including REST, SOAP, JSONv2, and RSS.

SOAP web service

Simple Object Access Protocol (SOAP) is an XML-based protocol for accessing web services over HTTP.

You can use SOAP to access data on your instance. Available SOAP web services are WS-I compliant, as outlined in the WS-I Basic Profile 1.0.

##### Web service provider

ServiceNow publishes its underlying table structures and associated data using the following web service methods:

**-** Direct web services: Use a URL query to request a table's WSDL.

**-** SOAP web service import sets: Use import tables and transform maps to automate web service requests for tables.

**-** Scripted SOAP web services: Use custom JavaScript to execute SOAP web services requests.

##### Note: SOAP messages are sent with the assumption that the recipient is XML compliant.

No encoding is applied to a SOAP message. SOAP always decodes responses as UTF-8, the XML encoding header is not used.

##### WSDL

All tables and import sets dynamically generate Web Service Definition Language (WSDL) XML documents that describe its table schema and available operations.

You can obtain a table's WSDL by issuing a URL call to your instance that contains the name of the table and the WSDL parameter. For example:

https://myinstance.service-now.com/incident.do?WSDL

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 319

All dynamically generated and served ServiceNow WSDLs accessible via HTTP are available for use under the terms defined in the Open Source Initiative OSI Apache License, Version 2.0 license agreement.

##### Long-running SOAP request support

The ServiceNow AI Platform supports long-running SOAP requests by preventing socket timeouts due to inactivity of the network connection while the requests are in process.

This functionality improves the efficiency of the ODBC driver when requesting large numbers of records, doing aggregate queries, or using order by expressions that require sorting.

By default, the system provides timeout protection for web services clients provided by ServiceNow such as the ODBC driver and the MID Server. You can add timeout protection to your custom web services with system properties.

##### Timeout protection

Web services clients receive a 307-Temporary Redirect to keep long sessions alive and prevent a timeout due to socket inactivity. A 307-Temporary Redirect causes web services clients which support the status code to repeat their last request to the location specified in the HTTP location header. The value of the location header is the same URL that the web services client originally specified. The use of 307-Temporary Redirects is WS-I compliant.

A web service request that exceeds the timeout limit specified in

###### glide.soap.request_processing_timeout can only receive a 307-Temporary

Redirect when all of these conditions are met:

**-** The value of glide.soapprocessor.allow_long_running_threads is true.

**-** The request includes a redirectSupported=true URL parameter.

**-** The request is session-aware (supports HTTP cookies).

**-** The number of redirects has not exceeded the value set by

###### glide.soap.max_redirects.

If any of these conditions is not met, the web service client receives a 408 Request Timeout error.

##### Note: To ensure that applications experience a socket timeout rather than a 408 Request

###### Timeout, set the glide.soap.request_processing_timeout property to a value

larger than the shortest socket timeout setting in effect for the connection between the application and the instance (300 seconds for hosted instances).

##### SOAP web services security

An instance enforces web service security using a combination of basic authentication challenge/response over the HTTPS protocol and system-level access control lists (ACLs) using contextual security. Administrators can control what system resources web services users can access by granting them one of the SOAP roles.

##### SOAP roles

To use SOAP web services, you must have the appropriate role for the operation you want to perform. Also, you must have any other roles required to access the target tables.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 320

SOAP Roles

Role Description

soap Can perform all SOAP operations.

soap_create Can insert new records.

soap_delete Can delete existing records.

soap_ecc Can query, insert, and delete records on the Queues [ecc_queue] table.

soap_query Can query record information.

soap_query_update Can query record information and update records.

soap_script Can run scripts that specify a .do endpoint. This role is required for running scripted web services.

soap_update Can update records.

import_admin Can manage all aspects of import sets and imports. Required for access to the Import Set Row [sys_import_set_row] table.

import_transformer Can manage import set transform maps and run transforms. Required for access to the Import Set Row [sys_import_set_row] table.

##### Default web services role requirements

By default, a set of processor ACL rules require users to have the soap_query role to make WSDL, XSD, and XML schema requests.

If you want to change these role requirements, you can deactivate the ACL rules.

Web service processor ACLs

##### Basic authentication

To enforce basic authentication for the user associated with the instance for each WSDL or SOAP message request, administrators can set the property glide.basicauth.required to true.

When enabled, each WSDL and SOAP request must contain an "Authorization" header as specified in the Basic Authentication protocol.

Because web services requests are non-interactive, the Authorization header is always required during a request.

##### Note: If configured, basic authentication refers to local credentials or LDAP

authentication.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 321

Supplying basic authentication information with every request (whether or not it is required) has the added advantage that the user supplied in the basic authentication credentials can be associated web service invocation. For example, when creating an Incident record, the journal field lists the user ID contained in the basic authentication header instead of the default guest user.

##### SOAP security policies

The Enhanced Web Service Provider Common plugin adds the SOAP Security Policies module to the System Web Services application. This module allows administrators to set the following security policies:

**-** Enable or disable signing SOAP requests when consuming an external web service

**-** Specify the authentication requirements SOAP requests must meet when communicating over WS-Security.

To know more about SOAP access policy, see SOAP API access policies.

SOAP security policies

##### Certificates required for signed SOAP requests

To sign SOAP requests for WS-Security communications, the following certificates are required:

**-** X.509 certificate from the requester

**-** X.509 CA certificate of the certificate authority who signed the requester's certificate

##### SOAP default security policy

Administrators can specify the SOAP security policy an instance uses with the system property glide.soap.default_security_policy. The glide.soap.default_security_policy system property specifies the name of the SOAP security policy the instance uses when enforcing Web Services-Security (WSS) for inbound requests.

SOAP default security policy settings

Field Description

Type String

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 322

SOAP default security policy settings (continued)

Field Description

Default value Default Security Policy

Location Add a system property to the System Properties [sys_properties] table

##### WS-Security

You can validate signed web services requests using WS-security. Enable WS-Security to:

**-** Verify that SOAP messages originate from a known sender

**-** Verify that SOAP messages have not been altered in transit

ServiceNow supports WS-Security 1.1 to validate signed web services requests.

##### Note: WS-Security is not used as an encryption mechanism, HTTPS protocol is used to

encrypt all communications.

WS-Security is intended to work with basic authentication. When an instance receives a SOAP message, it reviews the basic authentication header to determine if the SOAP user has rights to the instance. It reviews the WS-Security header to determine the validity of the incoming message. Requests affected by attacks, such as a man-in-the-middle attack, have an invalid WSSecurity header and are blocked.

##### WS-Security profiles

A WS-security profile determines how a web services message is authenticated when WSsecurity is enabled. The following mechanisms can be used to authenticate web services requests:

Web service authentication mechanisms

Authentication mechanism

Description

Certificate verification

Verifies the certificate associated with the request. Verifying the request's certificate requires uploading the requester's certificate and certificate authority.

User credentials

Authenticates the web services request by verifying the user credentials associated with the request. This type of authentication can either verify that the request's credentials match an existing user's credentials or that the request's credentials match a user name and password provided in the profile record.

Specify the authentication mechanism you want to use when you create a new WS-security profile.

The WS-Security Profiles module lists the WS-Security profiles that are currently in effect.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 323

WS-Security Profiles module

##### WS-Security error logging

The glide.processor.debug.SOAPProcessor system property allows error messages about WS-security to be displayed in the transaction log.

The system property glide.processor.debug.SOAPProcessor enables (true) or disables (false) debugging messages for SOAP processing such as certificate and keystore checks.

glide.processor.debug.SOAPProcessor fields

Field Description

Type true | false

Default value false

Location (^) Add a system property to the System Properties [sys_properties] table

##### WSS X.509 Token Profile

Use the X.509 framework for a WSS X.509 security profile. An X.509 certificate is used to validate a public key that is then used to sign the incoming SOAP message. It specifies a binding between a public key and a set of attributes that includes at least the following:

**-** subject name

**-** issuer name

**-** serial number

**-** validity interval

Use the X.509 authentication framework as defined by the Web Services Security: SOAP Message Security specification.

Upload the certificate and reference it in the X509 Certificate field. If a bound session, select the user to impersonate when the WS-Security authentication succeeds.

WSS X.509 Security Profile

##### WSS UsernameToken Profile

When specifying the X.509 Token Profile, you can also supply a UsernameToken in the SOAP request.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 324

A UsernameToken is used as a means of identifying the requester by "user name", and optionally using a password, shared secret, or password equivalent, to authenticate that identity.

There are two ways to authenticate a UsernameToken.

**1.** Authenticate with existing user credentials.

Authenticate with existing user credentials

Use the user name of the incoming SOAP request to look up a user by the specified User field to match the UserName value. The system uses the password value in the incoming UsernameToken to authenticate the request. When the Bind session option is selected, the user that authenticates successfully is used for the session.

**2.** Authenticate with specified user credentials.

Authenticate with specified user credentials

Authenticate using login credentials unrelated to users in the User table. When the Bind session option is selected, the user that is specified in the Run as user field is used for the session.

##### Note: The UsernameToken Profile cannot be used independent of the X.509 Token

Profile.

##### Strict security for web services

By default, basic authentication for web services only determines whether a user is authorized to access the instance with a SOAP connection. Once authorized, any user can access any table published as a web service.

The system property Enforce strict security on incoming SOAP requests changes this behavior and requires that users meet Contextual Security Manager requirements to access instance resources from web services.

With this property enabled, only users that have the proper SOAP role and also meet the ACL conditions the table and operation can perform that operation from a SOAP connection.

##### Mutual authentication for web services

Mutual authentication is supported for outbound web services.

##### SOAP session management and reporting

A SOAP session is a Glide session established with an instance by any external SOAP client, such as a web services client application, a ServiceNow MID Server, or the ServiceNow ODBC

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 325

driver. SOAP sessions are included in the list of user sessions at User Administration > Logged in users. The ?SOAP URLs identify SOAP sessions.

##### SOAP session properties

Certain properties control how SOAP sessions are maintained.

SOAP session properties

Property Description

glide.soap.invalidate_session_timeout Duration, in seconds, that an active session remains open. After this duration is reached, the instance deactivates the session and reclaims any system resources. If the client sends another request after the timeout duration is reached, the instance establishes a new session.

This property accepts values from 5 to 1200 seconds (20 minutes).

**-** Type: integer

**-** Default value: 60

**-** Location: Add to the System Properties [sys_properties] table

##### Note: To learn more about properties that affect SOAP web services processing, see the

following topics in Instance Security Hardening Settings:

**-** Access control (instance security hardening)

**-** Basic auth: SOAP requests

Scripted SOAP web services

Scripted SOAP web services allow a ServiceNow administrator to create custom SOAP web services.

You can define input and output parameters for the SOAP web service and use JavaScript to perform operations. Though this feature is very powerful, use direct web services or SOAP web service import sets whenever possible since they are simpler to implement and maintain.

##### Security

Scripted SOAP web services have the same base security options as all SOAP web services. For details on SOAP web services security, see SOAP web services security.

When strict security is enforced on a system, the HTTP authenticated user must have the soap_script role to execute the scripted web service.

##### WSDL

All ServiceNow tables and import sets dynamically generate Web Service Definition Language (WSDL) XML documents that describe its table schema and available operations.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 326

##### Enforcing WSDL compliance

You can force the response to list output values in the same order as defined in the WSDL.

When you create a scripted SOAP web service, the generated WSDL is based on the Input Parameters and Output Parameters related lists. The actual SOAP response sent by the scripted service is determined by the Script. This behavior can cause the script to return output values in a different order than defined in the WSDL.

To enforce the order of output parameters as defined in the related list, select the WSDL Compliance check box. When this check box is selected, the web service reorders the parameters returned by the script to match the order in the WSDL.

##### Note: If additional response parameters are returned by the script, but are not defined in

the Response Parameters related list, those parameters are excluded from the response when WSDL Compliance is selected.

Output Parameters related list

Parameter Order

Param 1 200

Param 2 300

Param 3 100

The following is the script that sets values for the defined output parameters. Note that in this example script the parameters are set in a different order than defined in the Output Parameters

###### related list. Also note the additional parameter param4 that is not defined in the related list.

Response.param1 = 1; Response.param4 = 4; Response.param3 = 3;

When the WSDL Compliance check box is false , the SOAP response generated by the script is the following:

<response> <param1>1</param1> <param4>4</param1> <param3>3</param1> </response>

When the WSDL Compliance check box is true , the SOAP response generated by the script is the following:

<response> <param3>3</param1> <param1>1</param1> </response>

##### Static WSDL

Some web service clients require SOAP access to your instance through a specific WSDL format. This required format may differ from the standard ServiceNow WSDL format. In these cases you can create a static WSDL that matches the required format.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 327

##### Global variables

To facilitate custom processing of incoming SOAP requests, the following global variables are available in the script context:

**-** _soapRequestDocument_ : Java org.w3c.dom.Document object representing the incoming SOAP envelope.

**-** _soapRequestXML_ : String object representing the incoming SOAP envelope XML.

**-** _request_ : Javascript object that contains mapped values (mapped to input parameter names) of the incoming SOAP envelope.

**-** _response_ : Javascript object that allows you to customize the response values. See Customize Response

Create a new scripted SOAP web service

Follow these examples to create a new scripted SOAP web service.

When the Web Services Provider Scripted plugin is activated, a new module Scripted Web Services is available under the System Web Services application.

Scripted SOAP web services

##### Example 1: Retrieving a system property

The first step is to define the incoming and return parameters. This is done by adding an entry to the Input Parameters and Output Parameters. These parameters are used to construct and present a meaningful WSDL, and they do not add to the functionality of processing the actual Web Service itself.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 328

GetProperty Input & Output Parameters

The parameters are referenced in the script of the Web Service. Any of the input parameters are retrieved using the following syntax:

var a= request.property;

The output parameters are set by using the following syntax:

response.property="ABC";

The following example demonstrates how to retrieve a system property and return it as part of the SOAP response. The example shows how to create a custom scripted web service to do something specific that the base ServiceNow system direct Web Services cannot.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 329

GetProperty web service

##### Example 2: Ordering a Blackberry

Direct web services operate on tables and their data. The following example shows how to initiate a business solution, such as ordering a Blackberry, by invoking a scripted web service. The following input and output parameters support the Blackberry example:

Input output Blackberry

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 330

This script shows how to use the above parameters to add a Blackberry to the service catalog shopping cart and order it. The request number is returned in the request_number field of the SOAP response.

var cart = new Cart(); var item = cart.addItem('e2132865c0a8016500108d9cee411699'); cart.setVariable(item,'original', request.phone_number);

// set the requested for var gr = new GlideRecord("sys_user"); gr.addQuery("user_name", request.requested_for); gr.query();

if(gr.next()){ var cartGR = cart.getCart(); cartGR.requested_for = gr.getUniqueValue(); cartGR.update(); }

var rc = cart.placeOrder(); response.request_number= rc.getValue('number');

Customize response

Follow this example to customize and control the XML payload of a SOAP response.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Create a customized XML document using the XMLDocument script include object.

##### Note: When creating a scripted web service in a scoped application you must use the

XMLDocument2 API.

###### 2. Set its document element to the variable response.soapResponseElement in a

scripted web service.

For example, the following scripted web service script:

var xmldoc = new XMLDocument2(); xmldoc.parseXML("<myResponse></myResponse>"); xmldoc.createElementWithTextValue("element_one", "test"); xmldoc.createElementWithTextValue("element_two", "new2 value");

var el = xmldoc.createElement("element_three"); xmldoc.setCurrentElement(el); xmldoc.createElementWithTextValue("newChild", "test child element");

response.soapResponseElement = xmldoc.getDocumentElement();

Is used to accept the following request:

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tes="http://www.service-now.com/TestCustomResponse">

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 331

<soapenv:Header/> <soapenv:Body> <tes:execute/> </soapenv:Body> </soapenv:Envelope>

Which will respond with the following SOAP response:

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tes="http://www.service-now.com/TestCustomResponse"> <soapenv:Header/> <soapenv:Body> <myResponse> <element_one>test</element_one> <element_two>new2 value</element_two> <element_three> <newChild>test child element</newChild> </element_three> </myResponse> </soapenv:Body> </soapenv:Envelope>

WSDL support will need to be created externally. The SOAP endpoint will need to be referred back to the scripted web service in question.

Create a scripted SOAP web service using a static WSDL

Follow these examples to create a scripted SOAP web service using a static WSDL.

Create a scripted web service using a static WSDL

To use a static WSDL, create a scripted web service.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Navigate to **All** > **System Web Service** > **Scripted Web Services**.

**2.** Click **New**.

**3.** Enter a **Name** for the scripted SOAP web service such as FakeStockValue.

**4.** Enter a **Script** for the web service to run.

**5.** Click **Submit**.

Scripted web service example

This example demonstrates the processing script for the FakeStockValue web service.

var vProcessor = new FakeStockValue (soapRequestXML ) ;

var responseElement = vProcessor. process ( ) ; if (responseElement != null ) { response. soapResponseElement = responseElement ; } else { response. soapResponseElement = vProcessor. generateSoapFault ( "unknown error" ) ; }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 332

Create a static WSDL

Create a static WSDL with the required format to override the standard WSDL for your scripted web service.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Navigate to **All** > **System Web Services** > **Static WSDL**.

**2.** Create a static WSDL record using the same name as the scripted web service, such as FakeStockValue.

**3.** Enter the custom WSDL into the **WSDL** field.

**4.** Click **Submit**.

Static WSDL example

This example demonstrates the FakeStockValue WSDL.

 <?xml version= "1.0" ?><definitions name = "StockQuote"targetNamespace = "http://example.com/stockquote.wsdl"xmlns:tns = "http://example.com/stockquote.wsdl"xmlns:xsd1 = "http://example.com/stockquote.xsd"xmlns:soap = "http://schemas.xmlsoap.org/wsdl/soap/"xmlns = "http://schemas.xmlsoap.org/wsdl/" >

<types><schema targetNamespace = "http://example.com/stockquote.xsd"xmlns = "http://www.w3.org/2000/10/XMLSchema" ><element name = "TradePriceRequest" ><complexType><all><element name = "tickerSymbol" type = "string" /></all></complexType></element><element name = "TradePrice" ><complexType><all><element name = "price" type = "float" /></all></complexType></element></schema></types>

<message name = "GetLastTradePriceInput" ><part name = "body" element = "xsd1:TradePriceRequest" /></message>

<message name = "GetLastTradePriceOutput" ><part name = "body" element = "xsd1:TradePrice" /></message>

<portType name = "StockQuotePortType" ><operation name = "GetLastTradePrice" ><input message = "tns:GetLastTradePriceInput" /><output message = "tns:GetLastTradePriceOutput" /></operation></portType>

<binding name = "StockQuoteSoapBinding" type = "tns:StockQuotePortType" ><soap:binding style = "document" transport = "http://schemas.xmlsoap.org/soap/http" /><operation name = "GetLastTradePrice" ><soap:operation soapAction = "" /><input><soap:body use = "literal" /></input><output><soap:body use = "literal" /></output></operation></binding>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 333

<service name = "StockQuoteService" ><documentation>My first service</documentation><port name = "StockQuotePort" binding = "tns:StockQuoteSoapBinding" ><soap:address location = "https://myinstance.service-now.com/FakeStockValue.do?SOAP" / ></port></service>

 </definitions>

Create a static WSDL script include

Create a script include to define the majority of the code used to process static WSDL requests.

###### Before you begin

Role required: script_include_admin or admin

###### About this task

By implementing the majority of the custom functionality in a script include, you can reuse the script include in multiple areas.

###### Procedure

**1.** Navigate to **All** > **System UI** > **Script Includes**.

**2.** Click **New**.

**3.** Enter a **Name** for the script include that matches the name of the static WSDL, such as FakeStockValue.

**4.** Enter the script include code in the **Script** field.

**5.** Click **Submit**.

Static WSDL script include example

This example demonstrates the FakeStockValue script include that implements much of the static WSDL behavior.

var FakeStockValue = Class.create();

FakeStockValue.prototype = { initialize : function(requestXML) { //Use some backend XML utilities...you could use string tools if you wish this.xmlutil = Packages.com.glide.util.XMLUtil; //converting the string to an XML Document this.fSoapDoc = new XMLDocument(requestXML); },

process : function() { var soapBody = this.fSoapDoc.getNode("/Envelope/Body"); //Our WSDL was formatted to have the only first child element be the function var funcNode = this.xmlutil.getFirstChildElement(soapBody); var nodeName = this.xmlutil.getNodeNameNS(funcNode);

//If the function for this SOAP request is TradePriceRequest, perform the necessary actions if (nodeName == "TradePriceRequest") { return this.fakeOutTradePriceRequest(funcNode); }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 334

//Couldn't find any supported functions in this SOAP request return this.generateSoapFault("un-supported API call: " + nodeName); },

fakeOutTradePriceRequest : function (funcNode) { //Create the beginnings of our XML response var r = new XMLDocument("<GetLastTradePriceOutput xmlns='https://www.service-now.com/vws/FakeStockValue'/>");

//Do the necessary actions here...we're going to get the USER ID of the user //used to make this SOAP call. Then we will return the //stock symbol they were asking about var usersysid = gs.getUserID(); var now_GR = new GlideRecord("sys_user"); gr.get(usersysid); var username = gr.user_name; var quoteSymbol = this.xmlutil.getText(funcNode); //Create a "message" element to store our response message r.createElement("message", username + ", You were looking for a quote on "+quoteSymbol); return r.getDocumentElement(); },

generateSoapFault : function (str) { var f = "<SOAP-ENV:Fault>" + "<faultcode xsi:type='xsd:string'>SOAP-ENV:FakeStockValue</faultcode>" + "<faultstring xsi:type='xsd:string'>" + str + "</faultstring>" + "</SOAP-ENV:Fault>" var s = new XMLDocument(f); return s.getDocumentElement(); } }

##### initialize function

The initialize function takes the XML request string and converts it to an XML Document object that you can navigate and manipulate using libraries. Alternatively, you can leave the XML request as a string and navigate it using regular expressions.

##### process function

The process function is called by the scripted web service. This function grabs the first child element in the XML after the body element. The WSDL uses this child element to determine which function to use. In this WSDL there is only one possible function but most WSDLs provide many functions. If more functions were available, there would be more "if" statements that tested the first child element for the various function names.

##### fakeOutTradePriceRequest function

The fakeOutTradePriceRequest function is the implementation of the only available function in the WSDL. This function looks up the user that the SOAP request authenticated as and retrieves

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 335

the user_name then returns it to the SOAP client. The fakeOutTradePriceRequest function could be expanded to perform useful activities, such as looking up a stock symbol and returning the last traded price.

##### generateSoapFault function

The generateSoapFault function returns a SOAP error that can be called if there are problems.

Use the static WSDL

Load the static WSDL into a SOAP client to make requests to the SOAP web service.

The web service client provides

**-** The FakeStockValue project.

**-** The StockQuoteBinding web service.

**-** The GetLastTradePrice SOAP function. This function generates request records when run.

Loaded WSDL

You can change the default request XML in the static WSDL to include a stock symbol.

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:stoc="http://example.com/stockquote.xsd"> <soapenv:Header/> <soapenv:Body> <stoc:TradePriceRequest>IBM</stoc:TradePriceRequest> </soapenv:Body> </soapenv:Envelope>

Submitting a SOAP request to this web service endpoint returns the following to the requesting SOAP client.

<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> <SOAP-ENV:Body> <GetLastTradePriceOutput xmlns="https://www.service-now.com/vws/FakeStockValue"> <message>admin2, You were looking for a quote on IBM</message> </GetLastTradePriceOutput> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

Direct web services

A direct web service is available for any table in the system if the correct access control list is configured.

The supported format of the incoming message is document style literal XML SOAP documents (Document/Literal). To retrieve a direct web service WSDL description and XML schema, point to the relative URL <tablename>.do?WSDL. For example, to retrieve the WSDL for the

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 336

Incident table on the online demo system, use the following URL: https://<instance name>.service-now.com/incident.do?WSDL.

##### Extended query parameters

Extended query parameters enable you to filter and modify the return results of a SOAP query

###### when using the get, getKeys, and getRecords functions.

##### Note: Extended query element names are preceded by two underscore characters.

Available extended query parameters

Parameter Description Example

\_\_encoded_query Specify an encoded query string to be used in filtering the returned results. The encoded query string format is similar to the value that may be specified in a sysparm_query URL parameter. See the encoded query building example in the RSS feed generator examples.

<\_\_encoded_query>active=true^category='hardware'

\_\_order_by Instruct the returned results to be ordered by the specified field.

<**order_by>priority</**order_by>

\_\_order_by_desc Instruct the returned results to be ordered by the specified field, in descending order.

<**order_by_desc>opened_date</**order_by_desc>

\_\_exclude_columns Specify a list of comma delimited field names to exclude from the result set.

<**exclude_columns>sys_created_on,sys_created_by **exclude_columns>

\_\_limit Limit the number of records that are returned.

<**limit>100</**limit>

\_\_first_row Instruct the results to be offset by this number of records from the beginning of the set.

<**first_row>250</**first_row>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 337

Available extended query parameters (continued)

Parameter Description Example

When used with \_\_last_row has the effect of querying for a window of results. The results are inclusive of the first row number.

**last_row Instruct the results to be limited by this number of records from the beginning of the set, or the **start_row value when specified. When used with \_\_first_row has the effect of querying for a window of results. The results are less than the last row number, and does not include the last row.

<**last_row>500</**last_row>

\_\_use_view Specify a Form view by name, to be used for limiting and expanding the results returned. When the form view contains deep referenced fields such as caller_id.email , this field will be returned in the result as well.

<**use_view>soap_view</**use_view>

##### Direct web services namespace

##### Specifying a unique namespace for each table

###### The glide.wsdl.definition.use_unique_namespace property ensures that each

###### table's direct web service WSDL has a unique targetNamespace attribute. This property is

###### true by default, which requires a table's direct web service WSDL to use a targetNamespace

value of http://www.service-now.com/<table name>. When false (or when the

###### property is not present), all tables use the same targetNamespace value of http://

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 338

http://www.service-now.com. Since all tables also share the same operation names, a web service client attempting to consume more than one ServiceNow web service would be unable

###### to differentiate between requests between multiple tables. Using a unique targetNamespace

value allows web service clients to distinguish requests between multiple tables.

###### For example, the direct web service WSDL for the incident table uses this targetNamepsace

value:

<wsdl:definitions xmlns:soapenc= "http://schemas.xmlsoap.org/soap/encoding/"xmlns:wsdl = "http://schemas.xmlsoap.org/wsdl/"xmlns:http = "http://schemas.xmlsoap.org/wsdl/http/"xmlns:tns = "http://www.service-now.com/incident"xmlns:xsd = "http://www.w3.org/2001/XMLSchema"xmlns:mime = "http://schemas.xmlsoap.org/wsdl/mime/"xmlns:soap = "http://schemas.xmlsoap.org/wsdl/soap/"targetNamespace = "http://www.service-now.com/incident" ><wsdl:types><xsd:schema elementFormDefault = "unqualified"targetNamespace = "http://www.service-now.com/incident" >

##### Setting namespace requirements

ServiceNow's WSDL schema by default declares an attribute of

###### elementFormDefault="unqualified". This attribute indicates whether or not locally

###### declared elements must be qualified by the targetNamepsace in an instance document. If

the value of this attribute is unqualified , then locally declared elements should not be qualified

###### by the targetNamepsace. If the value of this attribute is qualified , then locally declared

###### elements must be qualified by the targetNamepsace.

However, this is incompatible with the way clients generated from WSDL (for example, .NET, Axis2, webMethods) process the embedded schema. It removes the schema namespace as a result, making the web service response unparseable.

To overcome this compatibility issue, a boolean property called

###### glide.wsdl.schema.UnqualifiedElementFormDefault is introduced. This

property has the value of true by default. Setting it to false enables clients generated from WSDL to parse the return value of the web service invocation. You can modify this property using the Web Services properties page at System Properties > Web Services.

##### Allowing duplicate service names

By default, service names from dynamically generated WSDL are unique and have the following format:

ServiceNow\_<table name>

To allow duplicate service names, administrators can set the

###### glide.wsdl.unique_service_name property to false. Create the property if it does not

exist.

Related topics

SOAP web service

Use forms to limit or extend the query response

On occasion, there is a need to limit the number of field values that a SOAP query returns.

You can use a form view to limit the number of field values returned by a SOAP query. Specifying a form view has the effects of:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 339

**1.** Limiting the response elements to contain only the fields on the view.

**2.** Specifying reference record field values from referenced fields such as **caller_id.email**. This causes the value of the caller's email to be returned in the SOAP response.

###### To enable form views for SOAP queries, configure the com.glide.soap.view property

to contain the name of the view that you want to use for all SOAP query responses. The

###### default is soap_response. You can also specify the view name as a URL parameter,

###### sysparm_view=<view name>, when making the SOAP call. For example:

https://<instance name>.service-now.com/incident.do?SOAP&sysparm_view=ess

By default, if a specified view name does not exist, the response contains all fields.

Return the display value for reference variables

###### When you query a record using a get or getRecords function, the instance returns all fields

associated with that record. The fields are often reference fields that contain a sys_id for a record on another table.

Use one of these options if you want the display value for the field to be returned instead of the sys_id:

###### 1. Add the glide.soap.return_displayValue property to your system properties, and

every SOAP request will return a display value for a reference field.

###### 2. Add the displayvalue=true parameter to your SOAP request URL, and SOAP requests

with that parameter will return a display value for a reference field as a string, instead of the sys_id. The SOAP URL would look as follows: https://<instance name>.servicenow.com/incident.do?displayvalue=true&SOAP.

###### 3. Add the displayvalue=all parameter to your SOAP request URL, and SOAP requests

with that parameter will return a display value for a reference field, in addition to the sys_id. The response element name for the display value field will be prefixed with dv, such as dv_caller_id.

Clear values from a target instance

You can pass an empty value through a SOAP parameter to clear the respective value in the target instance.

###### You can also pass an empty (null) value through the &allow_empty_value=true SOAP

query parameter to clear the respective value in the target instance.

For example, https://<instance name>.service-now.com/incident.do? SOAP&allow_empty_value=true lets you pass an empty value to the incident record in an instance.

You can then enter lines like the following in the SOAP request:

<assigned_to>value</assigned_to> <assignment_group>value</assignment_group> <category></category>

In the above example,

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 340

**-** <assigned_to>value</assigned_to> changes the value in the **Assigned to** field to the value specified in the SOAP request.

**-** <assignment_group>value</assignment_group> changes the value in the **Assignment group** field to the value specified in the SOAP request.

**-** <category></category> clears the value in the **Category** field.

Retrieve journal entries using direct web services

To get the contents of a journal field, make a second soap request against the sys_journal_field table to pull the appropriate journal records back for the record in question.

The URL for the WSDL would be in the following format.

https://instance-name.service-now.com/sys_journal_field.do?WSDL

To retrieve the journal entries, you will first need to query the incident for its sys_id value, and

###### then supply it as the element_id value in a getRecords call. To specify records only for

the comments field, specify the value comments for the element field. For example, a SOAP request would look like the following:

<soapenv:Envelope xmlns:soapenv= "http://schemas.xmlsoap.org/soap/envelope/" xmlns:sys= "http://www.service-now.com/sys_journal_field" ><soapenv:Header / ><soapenv:Body><sys:getRecords><element>comments</element><eleme nt_id>9d385017c611228701d22104cc95c371</element_id></sys:getReco rds></soapenv:Body></soapenv:Envelope>

Retrieve choice fields using direct web services

To retrieve or set choice fields, use the choice Value , not the Label.

For example, if you want to retrieve a list of all closed incidents, use the numerical value for Closed , which is 7 by default.

<state>7</state>

To see a list of choice values:

**1.** Navigate to the form containing the choice field. For example, navigate to **Incident > Open** and select an incident.

**2.** Right-click the choice value field and select **Configure Dictionary**. For example, configure the dictionary for the **State** field.

**3.** From the Choices related list, note the value for the label you want to query. For example, note that the **Closed** choice has a value of **7**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 341

Persist an HTTP session across all SOAP calls

In circumstances when a SOAP client makes many calls in a short amount of time, you may want to re-use a single HTTP session for all SOAP calls.

Each SOAP call creates a new user session that persists until it expires. To create a single user session and re-use it for all inbound SOAP calls, develop your SOAP client following these guidelines:

**-** Use a module like HTTP::Cookies to create a "cookie jar."

**-** Save the cookies returned by ServiceNow after each request (handled automatically by HTTP::Cookies).

**-** Re-send the cookies in the cookie jar with each subsequent request.

##### Note: If you have enabled the session rotation high security setting, it will immediately

invalidate the JSESSIONID returned from the server with the first response header. The second response includes a new JSESSIONID.

In perl, you can automatically save and send cookies with the following code:

use HTTP::Cookies;

we﷯ want to store and re-send cookies my $cookies = HTTP::Cookies->new(ignore_discard => 1);

my $soap = SOAP::Lite -> proxy('http://localhost:8080/glide/ecc_queue.do?SOAP');

Set﷯ the cookie jar $soap->transport->cookie_jar($cookies);

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 342

SOAP direct web service API functions

The standard SOAP API is a set of small, globally defined functions that can be performed on a targeted resource.

The targeted resource (or table) is defined in the URL by the format https://<instance name>.service-now.com/<table name>.do.

Data Modification API

Method Summary

Description

insert Creates a new record for the table targeted in the URL.

insertMultiple Creates multiple new records for the table targeted in the URL. To enable multiple inserts, activate the Web service import sets.

update Updates a existing record in the targeted table in the URL, identified by the mandatory sys_id field.

deleteRecord Deletes a record from the targeted table by supplying its sys_id.

deleteMultiple Delete multiple records from the targeted table by example values.

Data Retrieval API

Method Summary

Description

getKeys Query the targeted table by example values and return a comma delimited sys_id list.

getRecords Query the targeted table by example values and return all matching records and their fields.

get Query a single record from the targeted table by sys_id and return the record and its fields.

aggregate Query using and aggregate functions SUM, COUNT MIN, MAX, LAST, and AVG. To enable the aggregate functions, activate the Aggregate Web Service Plugin.

Data Retrieval API

Data Retrieval API method summaries and descriptions.

Data Retrieval API

Method Summary

Description

getKeys Query the targeted table by example values and return a comma delimited sys_id list.

getRecords Query the targeted table by example values and return all matching records and their fields.

get Query a single record from the targeted table by sys_id and return the record and its fields.

aggregate Query using and aggregate functions SUM, COUNT MIN, MAX, LAST, and AVG. To enable the aggregate functions, activate the Aggregate Web Service Plugin.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 343

Related topics

Data Modification API

getKeys

Query the targeted table by example values and return a comma delimited sys_id list.

##### Input fields

Any field value in the targeted table.

##### Output fields

###### A SOAP response element sys_id that contains a comma delimited list of Unique record

identifier (sys_id) values.

##### Sample SOAP messages

Sample SOAP request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:getKeys> <category>hardware</category> </inc:getKeys> </soapenv:Body> </soapenv:Envelope>

Sample SOAP response

<soapenv:Envelope xmlns:inc="http://www.service-now.com/incident" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"> <soapenv:Header/> <soapenv:Body> <getKeysResponse>

<sys_id>46e18c0fa9fe19810066a0083f76bd56,46e57642a9fe1981000b96 a5dca501ff,46f1784ba9fe19810018aa27fbb23482</sys_id> <count>7</count> </getKeysResponse> </soapenv:Body> </soapenv:Envelope>

##### Language-specific sample messages

###### For language-specific getKeys samples, refer to the following topics:

Perl SOAP::Lite

Java Apache Axis2

Python

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 344

getRecords

Query the targeted table by example values and return all matching records and their fields.

##### Input fields

Any field value in the targeted table.

##### Output fields

The getRecordResponse element may contain one or more getRecordsResult elements that encapsulate elements representing the field values of records matching the query.

##### Sample SOAP messages

Sample SOAP request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:getRecords> <number>INC0000002</number> </inc:getRecords> </soapenv:Body> </soapenv:Envelope>

Sample SOAP request using an encoded query to filter where incident number is INC0000001 or INC0000002

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:getRecords>

<**encoded_query>number=INC0000001^ORnumber=INC0000002</**encod ed_query> </inc:getRecords> </soapenv:Body> </soapenv:Envelope>

Sample SOAP response that contains 1 record

<soapenv:Envelope xmlns:inc="http://www.service-now.com/incident" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"> <soapenv:Header/> <soapenv:Body> <getRecordsResponse> <getRecordsResult>

<caller_id>5137153cc611227c000bbd1bd8cd2007</caller_id>

<caller_id.email>david.loo@service-now.com</caller_id.email>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 345

<closed_at/> <number>INC0000002</number> <opened_at>2009-12-14 23:07:12</opened_at> <short_description>Can't get to network file shares</short_description> </getRecordsResult> </getRecordsResponse> </soapenv:Body> </soapenv:Envelope>

Sample SOAP response that contains more than 1 record

<soapenv:Envelope xmlns:inc="http://www.service-now.com/incident" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"> <soapenv:Header/> <soapenv:Body> <getRecordsResponse> <getRecordsResult>

<caller_id>5137153cc611227c000bbd1bd8cd2006</caller_id>

<caller_id.email>rick.berzle@yourcompany.com</caller_id.email> <closed_at>2009-12-17 22:55:16</closed_at> <number>INC0000009</number> <opened_at>2009-12-16 22:50:23</opened_at> <short_description>Reset my password</short_description> </getRecordsResult> <getRecordsResult>

<caller_id>5137153cc611227c000bbd1bd8cd2005</caller_id>

<caller_id.email>fred.luddy@yourcompany.com</caller_id.email> <closed_at>2009-12-15 22:54:55</closed_at> <number>INC0000010</number> <opened_at>2009-12-10 22:53:02</opened_at> <short_description>Need Oracle 10GR2 installed</short_description> </getRecordsResult> </getRecordsResponse> </soapenv:Body> </soapenv:Envelope>

##### Language-specific sample messages

###### For language-specific getRecords samples, refer to the following topics:

Perl SOAP::Lite

Java Apache Axis2

Microsoft .NET web services client examples

Python

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 346

get

Query a single record from the targeted table by sys_id and return the record and its fields.

##### Input fields

An element <sys_id> identifying the sys_id of the record to be retrieved.

##### Output fields

A getResponse element encapsulating all field values for the record retrieved.

##### Sample SOAP messages

Sample SOAP request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:get> <sys_id>46e18c0fa9fe19810066a0083f76bd56</sys_id> </inc:get> </soapenv:Body> </soapenv:Envelope>

The resulting response of a get function call looks like this:

 <?xml version="1.0" encoding="UTF-8"?> <soap:Envelope xmlns:soap="http://schemaap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> <soap:Body> <getResponse xmlns="http://www.service-now.com/incident"> <active>1</active> <approval>not requested</approval>

<assigned_to>46c6f9efa9fe198101ddf5eed9adf6e7</assigned_to> <caller_id>46b673a6a9fe19810007ab03cbd5849d</caller_id> <category>network</category> <cmdb_ci>0c43f35dc61122750182c132a29e3243</cmdb_ci> <comments>Testing</comments> <contact_type>phone</contact_type> <due_date>2007-10-28 13:29:45</due_date> <escalation>0</escalation> <impact>3</impact> <incident_state>1</incident_state> <knowledge>0</knowledge> <location>1081761cc611227501d063fd3475a2de</location> <made_sla>1</made_sla> <notify>1</notify> <number>INC10055</number> <opened_at>2007-09-18 00:32:09</opened_at> <opened_by>46bac3d6a9fe1981005f299d979b8869</opened_by> <priority>0</priority>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 347

<reassignment_count>0</reassignment_count> <severity>0</severity> </getResponse> </soap:Body> </soap:Envelope>

aggregate

###### Query a table using an aggregate function including SUM, COUNT, MIN, MAX, LAST, and AVG.

##### Note: Functionality described here requires the Aggregate Web Service plugin.

##### Input fields

###### Any element of the target table. In addition, one or more of the aggregate functions (SUM,

COUNT, MIN, MAX, LAST, and AVG).

A GROUP BY and a HAVING clause may also be added.

##### Output fields

###### An aggregateResponse element encapsulating all field values for the record retrieved.

##### Sample SOAP messages

Sample SOAP request using COUNT aggregate function.

 <?xml version="1.0" encoding="UTF-8"?> <SOAP-ENV:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/encoding/"

xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:m="http://www.service-now.com" xmlns:tns="http://www.service-now.com/map" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <aggregate> <COUNT>number</COUNT> <active>true</active> </aggregate> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

The resulting response of a COUNT aggregate function call looks like this:

 <?xml version="1.0" encoding="UTF-8"?> <SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"

xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" xmlns:m="http://www.service-now.com" xmlns:tns="http://www.service-now.com/map" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 348

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <aggregateResponse> <aggregateResult> <avg>2.7200</avg> </aggregateResult> </aggregateResponse> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

Sample SOAP request using AVG aggregate function with a GROUP BY clause.

 <?xml version="1.0" encoding="UTF-8"?> <?xml version="1.0" encoding="UTF-8"?> <SOAP-ENV:Envelope xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"

xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:m="http://www.service-now.com" xmlns:tns="http://www.service-now.com/map" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <aggregate xmlns="http://www.service-now.com"> <GROUP_BY>category</GROUP_BY> <active>true</active> <AVG>severity</AVG> </aggregate> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

The resulting response of a AVG aggregate function call with a GROUP BY clause looks like this:

 <?xml version="1.0" encoding="UTF-8"?> <SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"

xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" xmlns:m="http://www.service-now.com" xmlns:tns="http://www.service-now.com/map" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <aggregateResponse> <aggregateResult>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 349

<avg>1.0000</avg> <category>database</category> </aggregateResult> <aggregateResult> <avg>3.0000</avg> <category>hardware</category> </aggregateResult> <aggregateResult> <avg>3.0000</avg> <category>inquiry</category> </aggregateResult> <aggregateResult> <avg>2.0000</avg> <category>network</category> </aggregateResult> <aggregateResult> <avg>2.6923</avg> <category>software</category> </aggregateResult> </aggregateResponse> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

Sample SOAP request using an encoded query to filter the aggregate:

 <?xml version="1.0" encoding="UTF-8"?> <SOAP-ENV:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/encoding/"

xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:m="http://www.service-now.com" xmlns:tns="http://www.service-now.com/map" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <aggregate> <COUNT>number</COUNT> <active>true</active>

<**encoded_query>number=INC0000001^ORnumber=INC0000002</**encod ed_query> </aggregate> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

Sample aggregate request using HAVING to narrow the results.

HAVING takes four fields. Each field is delimited by "^": the aggregate type, the field of the aggregate, the operation type, and the value to compare.

More than one HAVING can be added to the request, so you can use HAVING expressions, but there is no support for OR.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 350

 <?xml version="1.0" encoding="UTF-8"?> <SOAP-ENV:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/encoding/"

xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:m="http://www.service-now.com" xmlns:tns="http://www.service-now.com/map" xmlns:xsd="http://www.w3.org/2001/XMLSchema"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <aggregate> <COUNT>sys_id</COUNT> <GROUP_BY>internal_type</GROUP_BY> <HAVING>COUNT^_^>^10</HAVING> <HAVING>COUNT^_^<^20</HAVING> <COUNT>sys_id</COUNT> <active>true</active> </aggregate> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

Data Modification API

Data Modification API method summaries and descriptions.

Data Modification API

Method Summary

Description

insert Creates a new record for the table targeted in the URL.

insertMultiple Creates multiple new records for the table targeted in the URL. To enable multiple inserts, activate the Web service import sets.

update Updates a existing record in the targeted table in the URL, identified by the mandatory sys_id field.

deleteRecord Deletes a record from the targeted table by supplying its sys_id.

deleteMultiple Delete multiple records from the targeted table by example values.

Related topics

Data Retrieval API

insert

Creates a new record for the table targeted in the URL.

##### Input fields

All fields from the targeted table, excluding system fields. Fields configured as mandatory in the System Dictionary are reflected in the WSDL with the attribute minOccurs=1.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 351

##### Output fields

Insert method output fields

Table type Output fields

Regular The sys_id field and the display value of the target table (table) are returned.

Import set The sys_id of the import set row, the name of the transformed target table (table), the display_name for the transformed target table, the display_value of the transformed target row, and a status field, which can contain inserted , updated , or error.

There can be an optional status_message field or an error_message field value when status=error.

When an insert did not cause a target row to be transformed (skipped because a key value is not specified), the sys_id field will contain the sys_id of the import set row, rather than the targeted transform table.

Import set with multiple transforms

The response from this type of insert will contain multiple sets of fields from the regular import set table insert wrapped in a multiInsertResponse parent element. Each set will contain a map field, showing which transform map created the response.

##### Sample SOAP messages for a regular table

The following example shows an insert that specifies the short description only:

 <?xml version="1.0" encoding="ISO-8859-1"?> <SOAP-ENV:Envelope xmlns:tns="http://www.service-now.com/incident" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" xmlns:m="http://www.service-now.com" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/"> <SOAP-ENV:Body> <insert xmlns="http://www.service-now.com"> <short_description xsi:type="xsd:string">This is a test</short_description> </insert> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

The resulting response looks like this:

 <?xml version="1.0" encoding="ISO-8859-1"?> <SOAP-ENV:Envelope SOAP-ENV:encodingStyle="http:// schemas.xmlsoap.org/soap/encoding/" xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:m="http://www.service-now.com"

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 352

xmlns:tns="http://www.service-now.com/incident" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> <SOAP-ENV:Body> <insertResponse xmlns="http://www.service-now.com"> <sys_id>6b06494fc611227d00b5f87caf618831</sys_id> </insertResponse> </SOAP-ENV:Body> </SOAP-ENV:Envelope>

##### Language-specific sample messages

###### For language-specific insert samples, refer to the following topics:

Perl SOAP::Lite

Java Apache Axis2

Python

insertMultiple

Creates multiple new records for the table targeted in the URL.

##### Input fields

###### The insertMultiple element may contain 1 or more record tags that contains all fields

from the targeted table, excluding system fields. Limit the number of records inserted in a single operation to no more than 200. You can gradually increase this number with subsequent exports if the increase does not negatively impact instance performance.

##### Output fields

The insertMultipleResponse tag is followed by 1 or more record tags that contains:

Insert method output fields

Table type Output fields

Regular The sys_id field and the display value of the target table (table) are returned.

Import set The sys_id of the import set row, the name of the transformed target table (table), the display_name for the transformed target table, the display_value of the transformed target row, and a status field, which can contain inserted , updated , or error.

There can be an optional status_message field or an error_message field value when status=error.

When an insert did not cause a target row to be transformed (skipped because a key value is not specified), the sys_id field will contain the sys_id of the import set row, rather than the targeted transform table.

Import set with multiple transforms

The response from this type of insert will contain multiple sets of fields from the regular import set table insert wrapped in a multiInsertResponse parent element. Each set will contain a map field, showing which transform map created the response.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 353

##### Sample SOAP messages for a regular table

The following example shows an insert that specifies the short description only:

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:insertMultiple> <record> <short_description>this is test 1</short_description> </record> <record> <short_description>this is test 2</short_description> </record> <record> <short_description>this is test 3</short_description> </record> </inc:insertMultiple> </soapenv:Body> </soapenv:Envelope>

The resulting response looks like this:

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <insertMultipleResponse> <insertResponse> <sys_id>168160ad4a36231200a89091281dc803</sys_id> <number>INC0055180</number> </insertResponse> <insertResponse> <sys_id>1681622e4a36231200a8909115e5c388</sys_id> <number>INC0055181</number> </insertResponse> <insertResponse> <sys_id>1681626e4a36231200a89091fa3c0aa8</sys_id> <number>INC0055182</number> </insertResponse> </insertMultipleResponse> </soapenv:Body> </soapenv:Envelope>

##### Sample SOAP messages for an import set table

The following example shows an insert that specifies the short description only:

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:imp="http://www.service-now.com/imp_notification">

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 354

<soapenv:Header/> <soapenv:Body> <imp:insertMultiple>:--> <imp:record> <imp:message>one</imp:message> <imp:uuid>a</imp:uuid> </imp:record> <imp:record> <imp:message>two</imp:message> <imp:uuid>b</imp:uuid> </imp:record> <imp:record> <imp:message>three</imp:message> <imp:uuid>c</imp:uuid> </imp:record> </imp:insertMultiple> </soapenv:Body> </soapenv:Envelope>

The resulting response looks like this:

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:imp="http://www.service-now.com/imp_notification"> <soapenv:Header/> <soapenv:Body> <insertMultipleResponse> <insertResponse> <sys_id>1296b3ab0a0a0b5b73e966fbfab7acde</sys_id> <table>incident</table> <display_name>number</display_name> <display_value>INC0010033</display_value> <status>ignored</status> <status_message>No field values changed</status_message> </insertResponse> <insertResponse> <sys_id>1296b48e0a0a0b5b62513bb5974a7d96</sys_id> <table>incident</table> <display_name>number</display_name> <display_value>INC0010034</display_value> <status>ignored</status> <status_message>No field values changed</status_message> </insertResponse> <insertResponse> <sys_id>1296b58b0a0a0b5b468f534659538b9a</sys_id> <table>incident</table> <display_name>number</display_name> <display_value>INC0010035</display_value> <status>ignored</status> <status_message>No field values changed</status_message> </insertResponse> </insertMultipleResponse>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 355

</soapenv:Body> </soapenv:Envelope>

update

Updates an existing record in the targeted table in the URL, identified by the mandatory sys_id field.

##### Input fields

All fields from the targeted table, excluding system fields, which will be used for updating the existing record. The sys_id field is used to locate the existing record.

##### Output fields

Returns the sys_id of the record that was updated.

##### Sample SOAP messages

Sample SOAP request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:update> <sys_id>46e18c0fa9fe19810066a0083f76bd56</sys_id> <short_description>this is updated</short_description> </inc:update> </soapenv:Body> </soapenv:Envelope>

Sample SOAP response

<soapenv:Envelope xmlns:inc="http://www.service-now.com/incident" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"> <soapenv:Header/> <soapenv:Body> <updateResponse> <sys_id>46e18c0fa9fe19810066a0083f76bd56</sys_id> </updateResponse> </soapenv:Body> </soapenv:Envelope>

##### Language-specific sample messages

###### For language-specific update samples, refer to the following topics:

Perl SOAP::Lite

Java Apache Axis2

Microsoft .NET

Python

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 356

deleteRecord

Delete a record from the targeted table by supplying its sys_id.

##### Input fields

An element <sys_id> identifying the sys_id of the record to be retrieved.

##### Output fields

###### A <count> element within the deleteRecordResponse parent element indicating the

number of records deleted, this will always equal to "1" for deleteRecord.

##### Sample SOAP messages

Sample SOAP request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:deleteRecord> <sys_id>46e18c0fa9fe19810066a0083f76bd56</sys_id> </inc:deleteRecord> </soapenv:Body> </soapenv:Envelope>

Sample SOAP response

<soapenv:Envelope xmlns:inc="http://www.service-now.com/incident" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"> <soapenv:Header/> <soapenv:Body> <deleteRecordResponse> <count>1</count> </deleteRecordResponse> </soapenv:Body> </soapenv:Envelope>

##### Language-specific sample messages

###### For language-specific deleteRecord samples, refer to the following topics:

Perl SOAP::Lite

Java Apache Axis2

Microsoft .NET

Python

deleteMultiple

Delete multiple records from the targeted table by example values.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 357

##### Input fields

All fields from the targeted table, including system fields, are used in query-by-example (QBE) fashion to locate records to be deleted. Query example fields can have special prefixes to constrain the search function.

##### Output fields

###### A <count> element within the deleteRecordResponse parent element indicating the

number of records deleted.

##### Sample SOAP messages

Sample SOAP request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:deleteMultiple> <category>hardware</category> </inc:deleteMultiple> </soapenv:Body> </soapenv:Envelope>

Sample SOAP response

<soapenv:Envelope xmlns:inc="http://www.service-now.com/incident" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"> <soapenv:Header/> <soapenv:Body> <deleteMultipleResponse> <count>6</count> </deleteMultipleResponse> </soapenv:Body> </soapenv:Envelope>

##### Language-specific sample messages

###### For language-specific deleteRecord samples, refer to the following topics:

Perl SOAP::Lite

Java Apache Axis2

Microsoft .NET

Python

SOAP web service import sets

Web service import sets complement direct web services and scripted SOAP web services by providing a web service interface to import sets tables.

By default, this type of web service synchronously transforms the incoming data based on the associated transform maps. If the associated import set mode is set to Asynchronous , the

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 358

behavior is to save the data for transformation at a later time. Web service import sets tables publish all default web service functions in the WSDL.

You can access a web service import set WSDL by specifying the import set table name + ".do? WSDL" on the URL.

For example:

http://<instance name>.service-now.com/imp_notification.do?WSDL.

Related topics

Web service import sets

Import sets key concepts

AttachmentCreator SOAP web service

Attach documents to records in ServiceNow by sending a SOAP message targeting the ecc_queue table.

##### Important: The AttachmentCreator SOAP web service is not recommended. Instead, use

the REST Attachment API to manage attachments with web services.

Using the AttachmentCreator SOAP web service, you can attach a single document to a message that is a maximum of 5 MB. The following is an example of a URL or target end point: https:// instance_name.service-now.com/ecc_queue.do?WSDL

ecc_queue Fields for Attachment Creation

Field Name

Description Value

agent The name of the agent sending in the request, this can be any value since it is not used for processing.

AttachmentCreator

topic The topic of the queue record, this value must be set to "AttachmentCreator" to trigger the attachment creation

AttachmentCreator

name This field must contain a ":" delimited value of the file name, and its content-type

file_name.xls:application/vnd.ms-excel

source This field must contain a ":" delimited value of the target table and its sys_id

incident:dd90c5d70a0a0b39000aac5aee704ae8

payload This field must contain the Base 64 encoded string representing the object to be attached

the base 64 encoded string

Sending in the values described in the table above will attach an Excel file to the incident table for the record located by the sys_id dd90c5d70a0a0b39000aac5aee704ae8

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 359

##### Security

Like all other HTTP based web services available on the platform, the AttachementCreator SOAP web service is required to authenticate using basic authentication by default. The user ID that is used for authentication will be subjected to access control in the same way as an interactive user.

To create attachments, the SOAP user must have any roles required to create Attachment [sys_attachment] records, as well as the soap_create role, and any roles required to read and write records on the target table, such as the itil role to add attachments to incident records. By default there is no single role allowing you to add attachments. You can create a role to explicitly allow adding attachments, then assign this role to the SOAP user.

##### File type security

You can control what file types users can attach by setting the

###### glide.attachment.extensions and

###### glide.security.file.mime_type.validation properties.

For these properties to apply to the AttachmentCreator web service, the property

###### glide.attachment.enforce_security_validation must be set to true. This

property is true by default.

##### Example SOAP Message

The following is an example of a SOAP message that would take a text file "john1.txt" of mime-type: text/plain and attach it to an Incident with a GUID of: e6eed6950a0a3c59006f32c8e3ff3cf9. Note the payload is the base64 encoding of the file itself.

 <?xml version="1.0" encoding="UTF-8"?> <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ecc="http://www.service-now.com/ecc_queue"> <soapenv:Header /> <soapenv:Body> <ecc:insert> <agent>AttachmentCreator</agent> <topic>AttachmentCreator</topic> <name>john1.txt:text/plain</name>

 <source>incident:e6eed6950a0a3c59006f32c8e3ff3cf9</source>

<payload>SSB3b25kZXIgaWYgc2hlIGtub3ducyB3aGF0IHNoZSdzIGRvaW5nIG 5vdy4K</payload> </ecc:insert> </soapenv:Body> </soapenv:Envelope>

##### Example Node.js Script

The following example Node.js script adds an attachment to an incident record. Run this script from a client computer, not an instance.

/\*\* \* _ Node.js to ServiceNow attachment upload via SOAP _ \* Andrew Venables andrew.venables@servicenow.com

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 360

- July 2014 \* _ Version 1.0 _ \*/

var soap = require('soap'), // https://github.com/vpulim/node-soap mime = require('mime'), // https://github.com/broofa/node-mime fs = require("fs");

var WSDL_FILENAME = 'ecc_queue.xml'; // Goto https://instancename.service-now.com/ecc_queue.do?WSDL and save a copy of the WSDL locally for simplicity var DIRECTORY_CONTAINING_FILES = '/Users/andrew.venables/Documents/Uploads'; // Local path to the directory containing all the files we want to upload var USERNAME = 'andy.venables'; // An admin user account on the instance var PASSWORD = 'MY_PASSWORD'; // Password for above account var TARGET_TABLE = 'incident'; // Target table to attach the files to var TARGET_SYS_ID = '9d385017c611228701d22104cc95c371'; // Target record / sys_id to attach the files to. OOTB INC0000002

var files_to_upload; // Global that will contain our list of files to be uploaded var pos = 0; // Global pointer for our position in the files_to_upload list

// Create a SOAP client to use to post to the instance soap.createClient(WSDL_FILENAME, function(err, client) { // Node uses callbacks if (err) console.error(err);

// Set the username and password client.setSecurity(new soap.BasicAuthSecurity(USERNAME, PASSWORD));

// Read all the files in our source directory, will include. and .. files_to_upload = fs.readdirSync(DIRECTORY_CONTAINING_FILES);

console.log('Files to upload: ' + files_to_upload.length + '\n');

// Start iterating through the list of files to upload next(client);

});

// Process the next file in the files_to_upload array // This is a neat way of dealing with Node and its expectation of callbacks function next(client) {

// Check we haven't reached the end

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 361

if (pos >= files_to_upload.length) return;

// Get the next file to upload var file_name = files_to_upload[pos];

// Increment the pointer to the next file pos++;

console.log(pos + '/'+ files_to_upload.length+ ' Uploading file: ' + file_name);

// A blank file is the end of the list if (file_name == '') return;

// Skip to the next file as this one is invalid if (file_name == '.' || file_name == '..' || file_name.indexOf('.') == 0) next(client);

// Get the file type using an module called mime var file_type = mime.lookup(file_name); console.log(' of type: ' + file_type);

var file_payload; // Load the file into a buffer fs.readFile(DIRECTORY_CONTAINING_FILES + '/' + file_name, function(err, the_data) { if (err) console.error(err);

// Encode the buffer to base64 file_payload = new Buffer(the_data, 'binary').toString('base64');

// Set the parameters before we call the Web Service var parameters = { 'agent': 'AttachmentCreator', 'topic': 'AttachmentCreator', 'name': file_name+':'+file_type, 'source': TARGET_TABLE+':'+TARGET_SYS_ID, 'payload': file_payload };

console.log(' sending...') // Make the Web Service call, remember node likes callbacks client.insert(parameters, function(err, result) { if (err) console.error(err);

console.log(result);

// This file is done, next! next(client); }); }); }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 362

##### Example Perl Script

The following example Perl script will create an attachment to an incident record.

use MIME::Base64; use strict; use SOAP::Lite;

﷯ the ServiceNow instance my $SNC_HOST = "https://instance_name.service-now.com"; my $base64; my $buf;

﷯ upload and attach a file on the local disk, base 64 encode it into a string first open(FILE, "/Users/davidloo/Desktop/test_files/number_test.xls") or die "$!"; binmode FILE; ﷯preserves file formatting on Windows while (read(FILE, $buf, 60*57)) { $base64 .= encode_base64($buf); }

﷯ call the sub routine to attach attach_incident();

sub attach_incident { ﷯ target the ecc_queue table my $soap = SOAP::Lite->proxy("$SNC_HOST/ecc_queue.do?SOAP"); $soap->{\_transport}->{\_proxy}->{ssl_opts}->{verify_hostname} = 0; my $method = SOAP::Data->name('insert')->attr({xmlns => 'http://www.service-now.com/'});

﷯ set the ecc_queue parameters my @params = (SOAP::Data->name(agent => 'AttachmentCreator')); push(@params, SOAP::Data->name(topic => 'AttachmentCreator') );

﷯ identify the file name and its mime type push(@params, SOAP::Data->name(name => 'number_test.xls:application/vnd.ms-excel') );

﷯ attach to the incident, specifying its sys_id push(@params, SOAP::Data->name(source => 'incident:dd90c5d70a0a0b39000aac5aee704ae8') );

﷯ set the payload to be the base 64 encoded string representation of the file push(@params, SOAP::Data->name(payload => $base64) );

﷯ invoke the web service my $result = $soap->call($method => @params);

print_fault($result);

print_result($result); }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 363

sub print*result { my ($result) = @*;

if ($result->body && $result->body->{'insertResponse'}) { my %keyHash = %{ $result->body->{'insertResponse'} }; foreach my $k (keys %keyHash) { print "name=$k value=$keyHash{$k}\n"; } } }

sub print*fault { my ($result) = @*;

if ($result->fault) { print "faultcode=". $result->fault->{'faultcode'}. "\n"; print "faultstring=". $result->fault->{'faultstring'}. "\n"; print "detail=". $result->fault->{'detail'}. "\n"; } }

﷯ use the itil user for basic auth credentials sub SOAP::Transport::HTTP::Client::get_basic_credentials { return 'itil' => 'itil'; }

Override a SOAP endpoint

The SOAP endpoint address where the SOAP message is posted is consistent with the endpoint of the WSDL.

In some cases, however, the WSDL may reference an incorrect endpoint URL. If this happens, it is necessary to over-ride the generated URL by creating the property

###### com.glide.soap_address_base_url to contain the new URL. You may have to add the

property manually as this is not an base system property.

For instance, a generated SOAP endpoint may look like this:

https://instance.service-now.com/incident.do?SOAP

You can specify a property to define the endpoint such that it goes through a proxy by setting the property:

com.glide.soap_address_base_url = "https://myproxy.mycompany.com/service-now/"

This will result in the endpoint being generated to appear as:

https://myproxy.mycompany.com/service-now/incident.do?SOAP

Enable HTTP compression

By default, the SOAP request is accepted un-compressed and the result of the request is returned un-compressed.

To enable HTTP compression using [gzip] when sending in your SOAP request, set the following HTTP header:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 364

Content-Encoding: gzip

To receive the SOAP response compressed using [gzip] send in your SOAP request with the following HTTP header:

Accept-Encoding: gzip

Prevent empty elements in SOAP messages

By default, an instance does not omit empty elements, elements with NULL or NIL values, from SOAP messages.

To prevent SOAP responses from containing empty elements, an administrator can create a

###### system property called glide.soap.omit_null_values and set the value to true. This

behavior is compliant with the WSDL as all elements in a SOAP message have a minOccurs=0 attribute and are therefore optional. In addition, this behavior prevents the instance from creating inefficient SOAP messages containing a large number of empty elements.

Set this property to false to allow SOAP messages to search for existing fields with empty values. For example, if an administrator wants to search for incidents with an empty Assigned to field from a SOAP message, then the SOAP message must be able to send an empty value for this field.

##### Note: Changing the value of this property may cause unintended actions in existing

web service integrations. Administrators are strongly encouraged to carefully test the new behavior to ensure that existing integrations process empty elements as expected.

Insert related records using SOAP

Support is available for inserting hierarchical data into tables or web service import set tables. The hierarchical data in the Insert API is automatically mapped to related records of the targeted table.

###### Before you begin

Role required: admin

###### Procedure

###### Create and set the property glide.web_service.hierarchical to true.

The client of the API can also override this value by invoking the SOAP web service with the URL

###### parameter hierarchical=true.

###### Example:

For example, when a related list is created for the incident table called u_custom_comments:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 365

Hierarchical Incident

And u_comment_items is created as a related list for u_custom_comments:

Hierarchical Custom Comments

Related topics

WSDL Schema with related records

Hierarchical SOAP Message

WSDL Schema with related records

When a WSDL for the target Incident table is requested with an additional parameter of

###### hierarchical=true, the WSDL schema for the Insert function will reflect available

related records that may participate in the hierarchical data payload.

For example, the insert portion of the schema of the incident table, when requested with

###### hierarchical=true displays its hierarchy as follows:

https://instance.service-now.com/incident.do? WSDL&hierarchical=true

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 366

WSDL Schema

...

WSDL Schema Continued

The WSDL above shows the incident table having a related table u_custom_comments that itself has a related table u_comment_items.

Hierarchical SOAP Message

When the SOAP message is constructed from the hierarchical web service described by the WSDL and invoked, it will create the incident, u_custom_comments, and u_comment_items records.

##### Endpoint URL

https://instance.service-now.com/incident.do? SOAP&hierarchical=true

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 367

##### Request

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <inc:insert> <short_description>test hierarchical</short_description> <u_custom_comments> <u_comment>comment 1</u_comment> <u_comment_type>travel</u_comment_type> <u_comment_items> <u_name>name 1</u_name> <u_value>value 1</u_value> </u_comment_items> </u_custom_comments> </inc:insert> </soapenv:Body> </soapenv:Envelope>

##### Reponse

<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:inc="http://www.service-now.com/incident"> <soapenv:Header/> <soapenv:Body> <insertResponse> <sys_id>8422ebe7c0a8006e7d23848c2dc8ba47</sys_id> <number>INC0010001</number> </insertResponse> </soapenv:Body> </soapenv:Envelope>

Specify requirement for signed SOAP requests

Use a SOAP security policy to specify whether the instance requires signed SOAP requests for all inbound SOAP traffic.

###### Before you begin

Role required: web_service_admin or admin

###### About this task

By default, all inbound SOAP traffic must be signed. Administrators may want to disable this policy and allow unsigned SOAP requests to ServiceNow web services.

###### Procedure

**1.** Navigate to **All** > **System Web Services** > **SOAP Security Policies**.

**2.** Select the **Default Policy**.

**3.** Clear the **Required to Sign SOAP Request** check box (selected by default) to disable the requirement.

**4.** Click **Update**.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 368

Activate the Enhanced Web Service Provider Common plugin

Administrators can activate the Enhanced Web Service Provider Common plugin to enable unsigned WS-Security requests and specify what authentication requirements SOAP requests have.

###### Before you begin

Role required: admin.

###### Procedure

**1.** Navigate to **All** > **System Applications** > **All Available Applications** > **All**.

**2.** Find the Enhanced Web Service Provider - Common plugin (com.glide.web_service_provider_v2) using the filter criteria and search bar.

You can search for the plugin by its name or ID. If you cannot find a plugin, you might have to request it from ServiceNow personnel.

**3.** Select **Install** to start the installation process.

##### Note: When domain separation and delegated admin are enabled in an instance, the

administrative user must be in the global domain. Otherwise, the following error appears: Application installation is unavailable because another operation is running: Plugin Activation for <plugin name>.

You will see a message after installation is completed. For information about the components installed with a plugin, see Find components installed with an application.

Installed with the Enhanced Web Service Provider Common plugin

The following components installed with the Enhanced Web Service Provider Common plugin.

The Enhanced Web Service Provider Common plugin installs the following components:

Components installed with the Enhanced Web Service Provider Common plugin

Component Type

Component Installed Description

Module Web Services Security Profiles The plugin adds this module to the System Web Services application.

System Property

glide.soap.default_security_policy Specifies the default security policy to use when enforcing Web Services-Security (WSS) for inbound requests.

Configure SOAP security

Administrators can configure web service security for inbound SOAP requests made to the ServiceNow instance.

###### Before you begin

Role required: admin

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 369

###### About this task

You can also set up web service security to use different certificates for different web service clients. By enabling web service security, you can prevent man-in-the-middle attacks.

##### Note: After you configure a WS-security profile or a security policy, validation is performed

on all incoming SOAP requests, including from the MID Server or ODBC driver. Disable validation for these types of requests by marking the service accounts as internal integration users.

###### Procedure

**1.** Upload a certificate to an instance.

**2.** Create a WS-security profile.

**3.** Create a security policy. Security policies define which WS-security profiles are used to evaluate a particular web service request. If no policy is defined, all WS-security profiles are used to evaluate all requests.

**4.** Set the value of the property glide.soap.default_security_policy to the name of the new security policy.

Set the SOAP default security policy

Set the SOAP default security policy.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Navigate to **All** > **System Web Services** > **Properties**.

**2.** In the **Security Policy to enforce if WS-Security is enabled** field, enter the default security policy to use when enforcing WS-security.

**3.** Click **Save**.

Create a new security policy

Administrators can specify which security profiles WS-Security communications must meet by creating a new security policy.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Navigate to **All** > **System Web Services** > **SOAP Security Policies**.

**2.** Click **New**.

**3.** Fill out the SOAP Security Policy form (see table).

SOAP Security Policy form fields

Field Description

Name Enter a unique name for the security policy. Use this name to set the default security policy with the glide.soap.default_security_policy property.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 370

Field Description

Type Select whether the SOAP security policy applies to inbound or outbound traffic.

Required to Sign SOAP Request

Select this checkbox to require signed SOAP requests. Clear the checkbox to allow unsigned SOAP requests. When enabled, the instance will produce an error for any SOAP request that does not include a valid signature. When disabled, the instance still verifies any signature included with a SOAP request.

Authenticate Select if a SOAP request must authenticate against all security profiles or at least one security profile.

Security Profiles

Select the security profiles you want to apply to this SOAP security policy. You must select at least one security profile.

**4.** Click **Submit**.

Create a new WS-Security profile

Create a new WS Security profile to define how to authenticate a web services message when WS-Security is enabled.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Navigate to **All** > **System Web Services** > **WS Security Profiles**.

**2.** Click **New**.

**3.** Fill in the WS-Security Profile form (see table).

WS-Security Profile form fields

Field Description

Name Enter a unique name for the security profile.

Type Select X509 to verify the request's certificate. Select Username to verify the request's user credentials.

Run as user

Select the ServiceNow user the instance will impersonate if authentication succeeds and the Bind Session field is selected. All web services requests will be attributed to this user. For example, if you select the System Administrator user then the instance treats all web services operations as being done by the system administrator. Make sure the user you select has appropriate SOAP privileges if you are using the glide.soap.strict_security high security setting. This field is only visible when the type is X509.

Order Enter the order in which the instance checks security profiles. The instance checks all security profiles when processing an incoming SOAP request. If a request fails any security profile authentication requirement, the instance stops processing additional security profiles and fails the request.

Bind Session

Select this check box to have the instance impersonate the user listed in the Run as user field. You should only set this field for one profile at a time. If multiple profiles have this field selected, ServiceNow impersonates the user from the last successfully authenticated WS-Security profile. If no profile has

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 371

Field Description

this field selected, ServiceNow impersonates the user provided with the basic authentication headers or impersonates the default user (Guest).

X509 Certificate

Select the certificate record containing the certificate for web service requests. ServiceNow only validates the request signature. It automatically trusts the certificate's certificate authority (CA). This field is only visible when the type is X509.

Profile action

Select how you want the instance to authenticate the user credentials. Select Authenticate with user if you want the instance to authenticate the request based on an existing user record. The request's credentials must match values in an existing user record. Select Specify user to authenticate if you want to list a user name and password combination that all web services requests must meet. The request's credentials must match the user name and password you list. This field is only visible when the type is Username.

User field to match UserName

Select the column from the User [sys_user] table containing the value you want match against the request's UserName. For example, if you select Email then the request UserName header must contain an email address matching an existing ServiceNow user. This field is only visible when the profile action is Authenticate with user.

User name

Enter the user name that all web services requests must contain. This field is only visible when the profile action is Username.

User password

Enter the password that all web services requests must contain. This field is only visible when the profile action is Username

**4.** Click **Submit**.

Related topics

SOAP web services security

WS-Security

WS-Security profiles

Enforce strict security for inbound SOAP

Strict security for web services requires that users meet Contextual Security requirements to access instance resources.

###### Before you begin

Role required: admin

###### About this task

##### Note: ServiceNow does not support digital certificates, digital signatures, or other

digested token methods in SOAP web service calls.

To enforce strict security for web services connections:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 372

###### Procedure

**1.** Navigate to **All** > **System Properties** > **Web Services**.

**2.** Select **Yes** for **Enforce strict security on incoming SOAP requests**.

##### Note: To learn more about this property, see SOAP request strict security (instance

security hardening) in Instance Security Hardening Settings.

Enable WS-Security verification

Administrators can enable Web Services Security (WSS) verification from the Web Services system properties.

###### Before you begin

Role required: web_service_admin or admin

###### Procedure

**1.** Navigate to **All** > **System Web Services** > **Properties**.

**2.** For **Require WS-Security header verification for all incoming SOAP requests** , select **Yes**.

##### Note: Selecting this option enables WS-Security for all inbound SOAP requests. It is not

possible to enable WS-Security for only some requests.

**3.** Click **Save**.

**4.** Create a WS-security profile.

**5.** Update the user record for the Mid Server and ODBC driver to mark these users as internal integration users.

**6.** Download and install the latest MID Server and ODBC driver.

**7.** To validate SOAP request signatures, upload the remote web service's certificate as a JKS and create the web service's WSS Username Token Profile.

##### Note: Because ServiceNow WSS implementation does not verify the CA certificate, you

do not need to upload the web service's CA certificate.

Related topics

Basic authentication

Mark service accounts as internal integration users

Allow internal integration communications to bypass the WSS authentication requirement by marking their user accounts as internal integration users.

###### Before you begin

Role required: admin

###### About this task

When WS-Security is enabled, authentication is required for all SOAP requests including internal integration communications such as the MID Server, ODBC Driver, Remote Update Sets, and high availability cloning. SOAP requests for these internal integration communications cannot implement WS-Security due to technical implications. If your instance uses these SOAP

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 373

interfaces, you can allow them to bypass the WS-Security authentication requirement by marking their user accounts as internal integration users.

##### Note: Any web services other than ODBC, MID Server, Remote Update Sets, or high

availability cloning must implement WS-Security headers when WS-Security is enabled.

###### Procedure

**1.** Navigate to **All** > **User Administration** > **Users**.

**2.** Select the user account for the MID Server or ODBC Driver.

**3.** Configure the form to add the **Internal Integration User** field.

**4.** Select the **Internal Integration User** check box.

**5.** Click **Update**.

Related topics

Enable WS-Security verification

WS-Security

Debug incoming SOAP envelope

To capture incoming SOAP envelope XML in the system log, add the property

###### glide.processor.debug.SOAPProcessor with a value of true.

When enabled, this property adds the incoming SOAP envelope in the Message field of the system log ( System Logs > All ). Disable this debugging feature as soon as you are finished so that the log is not overwhelmed with excessive and unnecessary debugging information.

View a SOAP session log

You can view a user's log from a SOAP session.

###### Before you begin

Role required: admin

###### Procedure

**1.** Navigate to **All** > **User Administration** > **Logged in users**.

**2.** Open an active SOAP session to see the transactions log.

The SOAP session is marked as inactive within 60 seconds of the last transaction.

Basic authentication code samples

Samples of basic authentication code for several programming languages and versions.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 374

##### Perl and the SOAP::Lite libraries

To supply basic authentication when using Perl and the SOAP::Lite libraries, you can implement the following function:

sub SOAP::Transport::HTTP::Client::get_basic_credentials { return 'user_name' => 'password'; }

##### C# .NET VS 2005 or older

When using C⌘ .NET VS 2005 or older, you can take advantage of the Credentials object. For example:

System.Net.ICredentials cred = new System.Net.NetworkCredential("user_name", "password");

service.ServiceNow proxy = new service.ServiceNow(); service.get getService = newservice.get(); service.getResponse getServiceResponse = new service.getResponse();

try { proxy.Credentials = cred; getService.sys_id = "bf522c350a0a140701972dbf876f1610"; getServiceResponse = proxy.get(getService); catch (Exception ex) { }

##### C# .NET VS 2008

When using C⌘ .NET VS 2008, you can take advantage of the ClientCredentials object. For example:

Demo_Incident.ServiceNowSoapClient client = new Test08WebService.Demo_Incident.ServiceNowSoapClient(); client.ClientCredentials.UserName.UserName = "admin"; client.ClientCredentials.UserName.Password = "admin";

Then in your app.config file look for the following and change "None" to "Basic":

 <transport clientCredentialType="None" proxyCredentialType="None" realm="" />

##### VB .NET

When using VB .NET taking advantage of the Credentials object would look like the following:

Sub Main() Dim cred As New System.Net.NetworkCredential("user_name", "password")

Dim proxy As New VB_Democm.incident.ServiceNow Dim getIncident As New VB_Democm.incident.get Dim getResponse As New VB_Democm.incident.getResponse

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 375

proxy.Credentials = cred

getIncident.sys_id = "[your sysID here]"

getResponse = proxy.get(getIncident)

End Sub

The resulting response when Basic Authentication is turned on and no credentials are supplied looks like this:

 <html> <head> <title>Apache Tomcat/5.0.28 Error report</title> <style> <!--H1 {font-family:Tahoma,Arial,sans-serif;color:white;background-col or:525﷯D76;font-size:22px;} H2 {font-family:Tahoma,Arial,sans-serif;color:white;background-col or:525﷯D76;font-size:16px;} H3 {font-family:Tahoma,Arial,sans-serif;color:white;background-col or:525﷯D76;font-size:14px;} BODY {font-family:Tahoma,Arial,sans-serif;color:black;background-col or:white;} B {font-family:Tahoma,Arial,sans-serif;color:white;background-col or:525﷯D76;} P {font-family:Tahoma,Arial,sans-serif;background:white;color:bla ck;font-size:12px;} A {color: black;} A.name {color: black;} HR {color: 525﷯D76;}-</style> </head> <body> <h1>HTTP Status 401 -\</h1> <HR size="1" noshade="noshade"> <p><b>type</b> Status report</p> <p><b>message</b> <u></u></p> <p><b>description</b> <u>This request requires HTTP authentication ().</u></p> <HR size="1" noshade="noshade"> <h3>Apache Tomcat/5.0.28</h3> </body> </html>

Example: WS-Security SOAP envelope header

An example of a valid WS-Security SOAP envelope header.

<SOAP-ENV:Header> <wsse:Security

xmlns:wsse="http://

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 376

docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-sece xt-1.0.xsd" SOAP-ENV:mustUnderstand="1"> <wsse:BinarySecurityToken

xmlns:wsu="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-util ity-1.0.xsd"

EncodingType="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-se curity-1.0﷯Base64Binary"

ValueType="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-prof ile-1.0﷯X509v3" wsu:Id="CertId-2D914AB929A6719E7F13068829874641"

xmlns:wsse="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-sece xt-1.0.xsd"> MIIEgzCCA2ugAwIBAgILAQAAAAABLOZQMtEwDQYJKoZIhvcNAQ EFBQAwQDEXMBUGA1UEChMOQ3liZXJ0cnVzdCBJbmMxJTAjBg NVBAMTHEN5YmVydHJ1c3QgU3VyZWNyZWRlbnRpYWwgQ0Ew HhcNMTAxMjE0MTgyMjU1WhcNMTECMjE0MTgyMjU1WjB3MQsw CQYDVQQGEwJVUzEUMBIGA1UEChMLU2VydmljZS1Ob3cxKDA mBgkqhkiG9w0BCQEWGWRhdmlkLmxvb0BzZXJ2aWNlLW5vdy5jb 20xKDAmBgNVBAMTH1NlcnZpY2UtTm93IFBhcn3uZXIgRGV2ZWx vcG1lbnQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIB AQCvtcRIb6zkGnN9uyhtcSDNSIuCW6FgnTbTDUvw2nGlNA9y9iEV wTp5TG3eELOOFBCuRLeY5x28lN+cJ72v+zCwi/rZcbEPj8oWyLVA OqJThgrzhDabj0vDM/zU8bvAXcw6FoCUDFKkc64WC7Y4HpBdfW4 JT7FBgDQ3LEudq80Up+TfETiGwrEA3jRgy9fF92TKD7MN3Vkyhz2 xZLOFiN5HJixl9juNJmLWugqqIG04yZSuCutc1gjCy0U+f0NXKgh0Q rRheNpwcqWbbJvLbR9Ybso6l3UAYCQ09hrRnI7VaPvfiueUvuLopap o4Kel6iL8aMUAfEUDtkf1AbqRIIQ5AgMBAAGjggFFMIIBQTAfBgNVH SMEGDAWgBRJTJILzUojts557p5VM2taRMAClTA7BgNVHR8ENDA yMDCgLqAshipodHRwOi8vY3JsLm9tbmlyb290LmNvbS9TdXJlQ3JlZ GVudGlhbC5jcmwwHQYDVR0OBBYEFB+OqlvcdiYmq0enW6mgaV wZp9eaMA8GA1UdEwEB/wQFMAMCAQAwDgYDVR0PAQH/BAQD AgTwMBEGCWCGSAGG+EIBAQQEAwIFoDBJBg3rBgEFBQcBA1Q 9MDswOQYIKwYBBQUHMAKGLWh0dHA6Ly9jYWNlcnQub21uaXJv b3QuY29tL3N1cmVjcmVkZW50aWFsLmNydDAkBgNVHREEHTAbg RlkYXZpZC5sb29Ac2VydmljZS1ub3cuY29tMB0GA1UdJQQWMBQG CCsGAQUFBwMCBggrBgEFBQcDBDANBgkqhkiG9w0BAQUFAAO CAQEAmeoP0Bgtx2JN1ldLnnK6WLEqDk25zaHP5wTxqVlFxzJy1zi6 A0lk5U0T5LKYjjGWRIOoSeK8iBU0p7Mq4PE8QCETkjYNyuWJd9zm 7GPCHdOoL18rQHQRsU8pTDHA10zG+i3zdxAMrHl/H673E4myzvU DkJnxNAZdw4h4Ba/Y1+VFCWhOm2GwZdXtzklyZaKtMp+31qmf3bG OSU34M/dW40pXgfLDqdGD+6YDQPg25aYeCqcNhwg6VlAWG566g aWXYxRaVj0qotSDMdaK8b+7Vlo7KhGGaE62v7f44OSekJeBvTfZCR 7zRSK8N+0qUpqP/n8vgDkmYIE5IQrRE0rEWA== </wsse:BinarySecurityToken> <ds:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" Id="Signature-2"> <ds:SignedInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" <ds:CanonicalizationMethod

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 377

Algorithm="http://www.w3.org/2001/10/xml-exc-c14n﷯" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" /> <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig﷯rsa-sha1" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" /> <ds:Reference URI="﷯Timestamp-1" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" <ds:Transforms xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n﷯" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" /> </ds:Transforms> <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig﷯sha1" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" /> <ds:DigestValue xmlns:ds="http:// http://www.w3.org/2000/09/xmldsig﷯"NIS5sizg8wttGL+aWFQ4003TpPg=/ds:Di gestValue> </ds:Reference> <ds:Reference URI="﷯id-3" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" <ds:Transforms xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n﷯" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" /> </ds:Transforms> <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig﷯sha1" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" /> <ds:DigestValue xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯"/rXB +nhBT5BXtDErIUIBOyhoh8Y=</ds:DigestValue> </ds:Reference> </ds:SignedInfo> <ds:SignatureValue xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯"

fwjxJRiDNrNxbVsKoHZflsmKlYADldJf0BoN3R2Fx9rjpszFXI2Gp92eXsP+Sl6 rmbPXIdKb8lLl

+dv8upl8WYPrKJP61KeJ0ZsKNDX474NYC2XEzdJcXbZNktmqY0dSmKwJZzi8rJt mGrbOUAaH51GK

oXV2FLJ0AqILoZMyP/SPWKbOUNUCpssY7vRA+tX8ZmrjTwMUvpOZbo+KInPmwfp Z6n/uarOh5zjL

NaYJylTCjuuqXDKPZLvDqy48yrsGAWczB901KwLLrE8C+6aPucFrTBytX91vIha WiLZuba8Nouaz vUkjUk7LM5o87MGrSFx3OwxbaOD7/cMtdg2bxA== </ds:SignatureValue> <ds:KeyInfo Id="KeyId-2D914AB929A6719E7F13068829875022" xmlns:ds="http://www.w3.org/2000/09/xmldsig﷯" <wsse:SecurityTokenReference

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 378

xmlns:wsu="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-util ity-1.0.xsd" wsu:Id="STRId-2D914AB929A6719E7F13068829875053"

xmlns:wsse="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-sece xt-1.0.xsd"> <wsse:Reference URI="﷯CertId-2D914AB929A6719E7F13068829874641"

ValueType="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-prof ile-1.0﷯X509v3"

xmlns:wsse="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-sece xt-1.0.xsd" /> </wsse:SecurityTokenReference> </ds:KeyInfo> </ds:Signature> <wsu:Timestamp

xmlns:wsu="http:// docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-util ity-1.0.xsd" wsu:Id="Timestamp-1"> <wsu:Created>2011-05-31T23:03:07.454Z</wsu:Created> <wsu:Expires>2011-05-31T23:08:07.454Z</wsu:Expires> </wsu:Timestamp> <wsse:UsernameToken> <wsse:Username>test_user</wsse:Username> <wsse:Password>xxxxxx</wsse:Password> </wsse:UsernameToken> </wsse:Security> </SOAP-ENV:Header>

WS-Security properties

These properties control the behavior of WS-Security X.509 tokens.

Properties

Property Description

glide.soap.msg_digest.algorithm Specifies the method digest algorithm. Possible values are SHA-1, SHA-256, and SHA-512.

**-** Type: String

**-** Default value: SHA-1

**-** Location: Add to the System Property [sys_properties] table

glide.soap.signature.algorithm Specifies the signature algorithm. Possible values are RSASHA-1, RSA-SHA-256, and RSA-SHA-512.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 379

Properties (continued)

Property Description

**-** Type: String

**-** Default value: RSA-SHA-1

**-** Location: Add to the System Property [sys_properties] table

glide.soap.canonical.algorithm Specifies the cannonicalization algorithm. Possible values are Canonical xml 1.0, Canonical xml 1.0 with Comments, Exclusive Canonical xml 1.0, and Exclusive Canonical xml 1.0 with Comments.

**-** Type: String

**-** Default value: Exclusive Canonical xml 1.0

**-** Location: Add to the System Property [sys_properties] table

Each possible value for these properties represents a standard WS-Security algorithm.

Property value URLs

Value Algorithm

Method digest algorithms

SHA-1 http://www.w3.org/2000/09/xmldsig⌘sha1

SHA-256 http://www.w3.org/2001/04/xmlenc⌘sha256

SHA-512 http://www.w3.org/2001/04/xmlenc⌘sha512

Signature algorithms

RSA-SHA-1 http://www.w3.org/2000/09/xmldsig⌘rsa-sha1

RSA-SHA-256 http://www.w3.org/2001/04/xmldsig-more⌘rsa-sha256

RSA-SHA-512 http://www.w3.org/2001/04/xmldsig-more⌘rsa-sha512

Cannonicalization algorithms

Canonical xml 1.0 http://www.w3.org/TR/2001/REC-xml-c14n-20010315

Canonical xml 1.0 with Comments http://www.w3.org/TR/2001/REC-xmlc14n-20010315⌘WithComments

Exclusive Canonical xml 1.0 http://www.w3.org/2001/10/xml-exc-c14n⌘

Exclusive Canonical xml 1.0 with comments

http://www.w3.org/2001/10/xml-excc14n⌘WithComments

WS-Security error messages

An instances produces one of the following error messages when it encounters an issue with a WS-security SOAP message.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 380

WS-security error messages

Error Description

Invalid Security Policy Selected. Select an Inbound policy for Inbound Requests.

The default policy name is set to an outbound policy. Set the default policy name to an inbound security policy.

SOAP request not Signed. Policy requires signing.

The SOAP security policy requires signing and the inbound SOAP request is not signed. Either specify a different SOAP security policy or provide the SOAP request with a proper signature.

No profiles to authenticate. The selected Security policy either does not have any security profiles (X509 or UserNameToken) or the security profiles are inactive. Verify at least one security profile is active.

Unable to verify signed request.

The inbound SOAP request contains an invalid signature. The SOAP request changed after being signed.

Failed to extract principal(s) from request.

The SOAP request has either been tampered or was not well formed. ServiceNow cannot extract credentials to authenticate the request.

Failed to authenticate WSsecurity, unknown type.

The SOAP request contains an unsupported security profile. Resend the request with a supported security profile type: X509 or UsernameToken.

Failed to authenticate WSsecurity.

ServiceNow failed to authenticate against the provided profile credentials. Verify that the SOAP request is using the proper credentials.

WS-Security reference

Support for WS-Security 1.1 in the form of WSS X.509 Token Profile and WSS Username Token Profile is available for incoming SOAP requests.

The configuration to use WS-Security is separate from the requirement to enforce Basic Authentication, and is enforced when the SOAP envelope contains the WS-Security headers.

##### WS Security Profiles

The WS Security Profile module lists the WS-Security profiles that are currently in effect. The Order of the profiles indicates the order of authentication that is checked, all profiles are checked during the incoming SOAP request, when a profile fails authentication, it does not execute the next one in order. The Bind session check box indicates which profile to use to assume the session's identity, there can only be one "bound" session.

##### WSS X.509 Token Profile

Use the X.509 authentication framework as defined by the Web Services Security: SOAP Message Security specification. An X.509 certificate specifies a binding between a public key and a set of attributes that includes (at least) a subject name, issuer name, serial number, and validity interval. An X.509 certificate is used to validate a public key that is used to sign the incoming SOAP message. Upload the certificate in the Certificate module and reference it in the X509 Certificate field. If this is a bound session, select the user to impersonate when the WSSecurity authentication succeeds.

See the following document: http://www.oasis-open.org/committees/download.php/16785/wssv1.1-spec-os-x509TokenProfile.pdf

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 381

##### WSS Username Token Profile

In addition to specifying the X.509 Token Profile, a UsernameToken can also be supplied in the SOAP request. A UsernameToken is used as a means of identifying the requester by "username", and optionally using a password (or shared secret, or password equivalent) to authenticate that identity to the instance. The UsernameToken profile cannot be used independent of the X.509 Token Profile currently.

**1.** Authenticate using the Username of the incoming SOAP request to lookup a User by the specified **User field to match UserName** value. The password value in the incoming Username Token is used to authenticate the request. When the **Bind session** option is selected, the user that authenticates successfully is used for the session.

**2.** Authenticate using a separate pair of user name / password that is unrelated to users in the User table. When the **Bind session** option is selected, the user that is specified in the **Run as** **user** field is used for the session.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 382

##### Example WS-Security SOAP Envelope Headers

##### Note:

This sample has been formatted with line returns to fit the content into the frame.

<SOAP-ENV:Header><wsse:Securityxmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-ws security-secext-1.0.xsd"SOAP-ENV:mustUnderstand = "1" ><wsse:BinarySecurityTokenxmlns:wsu = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-ws security-utility-1.0.xsd"EncodingType = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-so ap-message-security-1.0﷯Base64Binary"ValueType = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x5 09-token-profile-1.0﷯X509v3"wsu:Id = "CertId-2D914AB929A6719E7F13068829874641"xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-ws security-secext-1.0.xsd" > MIIEgzCCA2ugAwIBAgILAQAAAAABLOZQMtEwDQYJKoZIhvcNAQ EFBQAwQDEXMBUGA1UEChMOQ3liZXJ0cnVzdCBJbmMxJTAjBg NVBAMTHEN5YmVydHJ1c3QgU3VyZWNyZWRlbnRpYWwgQ0Ew HhcNMTAxMjE0MTgyMjU1WhcNMTECMjE0MTgyMjU1WjB3MQsw CQYDVQQGEwJVUzEUMBIGA1UEChMLU2VydmljZS1Ob3cxKDA mBgkqhkiG9w0BCQEWGWRhdmlkLmxvb0BzZXJ2aWNlLW5vdy5jb 20xKDAmBgNVBAMTH1NlcnZpY2UtTm93IFBhcn3uZXIgRGV2ZWx vcG1lbnQwggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIB AQCvtcRIb6zkGnN9uyhtcSDNSIuCW6FgnTbTDUvw2nGlNA9y9iEV wTp5TG3eELOOFBCuRLeY5x28lN+cJ72v+zCwi/rZcbEPj8oWyLVA OqJThgrzhDabj0vDM/zU8bvAXcw6FoCUDFKkc64WC7Y4HpBdfW4 JT7FBgDQ3LEudq80Up+TfETiGwrEA3jRgy9fF92TKD7MN3Vkyhz2 xZLOFiN5HJixl9juNJmLWugqqIG04yZSuCutc1gjCy0U+f0NXKgh0Q rRheNpwcqWbbJvLbR9Ybso6l3UAYCQ09hrRnI7VaPvfiueUvuLopap o4Kel6iL8aMUAfEUDtkf1AbqRIIQ5AgMBAAGjggFFMIIBQTAfBgNVH SMEGDAWgBRJTJILzUojts557p5VM2taRMAClTA7BgNVHR8ENDA yMDCgLqAshipodHRwOi8vY3JsLm9tbmlyb290LmNvbS9TdXJlQ3JlZ GVudGlhbC5jcmwwHQYDVR0OBBYEFB+OqlvcdiYmq0enW6mgaV wZp9eaMA8GA1UdEwEB/wQFMAMCAQAwDgYDVR0PAQH/BAQD AgTwMBEGCWCGSAGG+EIBAQQEAwIFoDBJBg3rBgEFBQcBA1Q 9MDswOQYIKwYBBQUHMAKGLWh0dHA6Ly9jYWNlcnQub21uaXJv b3QuY29tL3N1cmVjcmVkZW50aWFsLmNydDAkBgNVHREEHTAbg RlkYXZpZC5sb29Ac2VydmljZS1ub3cuY29tMB0GA1UdJQQWMBQG CCsGAQUFBwMCBggrBgEFBQcDBDANBgkqhkiG9w0BAQUFAAO CAQEAmeoP0Bgtx2JN1ldLnnK6WLEqDk25zaHP5wTxqVlFxzJy1zi6 A0lk5U0T5LKYjjGWRIOoSeK8iBU0p7Mq4PE8QCETkjYNyuWJd9zm 7GPCHdOoL18rQHQRsU8pTDHA10zG+i3zdxAMrHl/H673E4myzvU DkJnxNAZdw4h4Ba/Y1+VFCWhOm2GwZdXtzklyZaKtMp+31qmf3bG OSU34M/dW40pXgfLDqdGD+6YDQPg25aYeCqcNhwg6VlAWG566g aWXYxRaVj0qotSDMdaK8b+7Vlo7KhGGaE62v7f44OSekJeBvTfZCR 7zRSK8N+0qUpqP/n8vgDkmYIE5IQrRE0rEWA== </wsse:BinarySecurityToken><ds:Signature xmlns:ds = "http://www.w3.org/2000/09/xmldsig﷯"Id = "Signature-2" ><ds:SignedInfo xmlns:ds = "http://www.w3.org/2000/09/xmldsig﷯" ><ds:CanonicalizationMethodAlgorithm = "http://www.w3.org/2001/10/xml-exc-c14n﷯" xmlns:ds = "http://www.w3.org/2000/09/xmldsig﷯" /><ds:SignatureMethod Algorithm = "http://www.w3.org/2000/09/xmldsig﷯rsa-sha1"xmlns:ds = "http://www.w3.org/2000/09/xmldsig﷯" /><ds:Reference

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. Other company names, product names, and logos may be trademarks of the respective companies with which they are associated.

383

Long-running SOAP request properties

The following properties are available for long-running SOAP requests.

Long-running SOAP request properties

Property Description

###### glide.http.connection_timeout Specify the maximum number

of milliseconds an outbound HTTP request (such as Web Services) will wait to establish a connection.

**-** Type: integer

**-** Default value: 10000 (10 seconds)

**-** Location: system properties [sys_properties] table

###### glide.http.timeout Specifies the maximum number

of milliseconds to wait before an outbound transaction times out.

**-** Type: integer

**-** Default value: 175000 (175 seconds)

**-** Location: Add to system properties [sys_properties] table

###### glide.soap.max_redirects Specifies the maximum number

of redirects the server sends to the client before the soap request is timed out.

**-** Type: integer

**-** Default value: 20

**-** Location: system properties [sys_properties] table

###### glide.soap.request_processing_timeout Specify the maximum number

of seconds an inbound SOAP request has to finish processing before the connection times out. This property computes a default value from the value of the property

###### glide.http.timeout

divided by 1000.

This property accepts values 5– 1200 seconds (20 minutes).

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 384

Long-running SOAP request properties (continued)

Property Description

Customers might have network infrastructure (such as proxy servers) in place which implement a shorter timeout. In this case, a socket timeout may occur unless this property is set to a shorter value. Set this property to a value several seconds less than the shortest socket inactivity timeout in effect anywhere in the network path between the client application and the instance.

**-** Type: integer

**-** Default value: 60

**-** Location: system properties [sys_properties] table

###### glide.soapprocessor.allow_long_running_threads Enables or disables a

307-Temporary Redirect when the request includes

###### a redirectSupported=true

parameter. The default setting is true (enabled).

###### glide.soapprocessor.max_long_running_threads Controls the maximum number

of long-running SOAP threads which can run at any one time. The default value for this property is determined dynamically based on the number of SOAP semaphores configured. It should not be necessary to change this value.

Retrieve a large number of records using SOAP

By default, a single SOAP request can retrieve a maximum of 250 records.

SOAP relies on Extensible Markup Language (XML) as its message format, and usually relies on other Application Layer protocols (most notably Remote Procedure Call (RPC) and HTTP) for message negotiation and transmission. SOAP can form the foundation layer of a web services protocol stack, providing a basic messaging framework upon which web services can be built.

Because of the verbose XML format, SOAP can be considerably slower than other transport methods. Therefore, sending a large amount of data via SOAP is inefficient and is discouraged. Because of this, ServiceNow has imposed a hard-limit of 250 records that can be retrieved at any time in a single query. You may find that this limit poses some technological challenges for your integration design.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 385

SOAP strategies

Retrieve the information that you need and make your integration more efficient.

Use filters to limit the number of results

One way to make your web service calls fit within the 250 record limit is to think about the design of your integrating application.

For example, let's assume that we are making an incident form in C⌘ to show a user the incidents that are assigned to him.

##### Problematic query approach

The C⌘ application makes a soap call to retrieve all of the incidents within ServiceNow. The application would then store the results locally in memory. When the user decides to view the incidents that are assigned to him, the application loops the internal array and displays the incidents that are assigned to the user.

##### A better query approach

The C⌘ application makes a soap call to retrieve all of the incidents within ServiceNow that are assigned to the logged-in user. The results are stored locally in memory. When the user decides to view the incidents that are assigned to him, the application shows all the results to the user.

##### A performance-optimized query approach

The C⌘ application makes no SOAP call initially. When a logged-in user decides to view the incidents that are assigned to him, the application presents him with the choice of viewing active, closed, etc. It gives him the ability to filter the results that he wants to see before the SOAP call is even made. Then, the user is only presented with the results that he wished to view.

Use a local data store to pull data from

If a large amount of data needs to be queried often, and the data does not need to be realtime, perform a sync of the ServiceNow table that you're interested in with your integrating application's data store.

##### Data push

**-** Using a scheduled job, ServiceNow can generate a csv/xml from a report and have it emailed to a specific location. The receiver might have a trigger to take the email attachment, parse it, and populate an internal table from which the application can communicate when the data is needed.

**-** Using a schedule job, ServiceNow can generate a csv/xml from a report and FTP it to an public FTP/FTPS location. The integrating product would consume this csv file on a regular basis and populate an internal table from which the application can communicate when the data is needed.

##### Note: Currently, the platform does not provide a method for extracting very large amounts

of data and sending the output to an FTP server. However, a customization to perform that function is described at here. The customization was developed for use in specific ServiceNow instances, and is not supported by ServiceNow Customer support. The method is provided as-is and should be tested thoroughly before implementation. Post all questions and comments regarding this customization to our community forum.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 386

##### Data pull

Using a cron job, a machine internal to your network can make a wget call to pull csv/xml data from any table within ServiceNow. The integrating product would consume this csv/xml file on a regular basis and populate an internal table from which the application can communicate when the data is needed. Examples of the wget command that would be used:

**-** wget --user=itil --password=itil --no-check-certificate https://<instance name>.service- now.com/incident_list.do?CSV

**-** wget --user=itil --password=itil --no-check-certificate https://<instance name>.service- now.com/incident_list.do?XML

Use Java/C#/PHP code to fetch the XML data using basic authentication

If a local data store is not an option, another way to get the data is to call the CSV/XML processor directly and then parse the results.

Use the resulting data in a similar manner as you would a direct SOAP call. An example of this in PHP:

 <?php //This example is in PHP 

 $user = "itil"; $pass = "itil"; $userPass = $user.':'.$pass; 

 $ch = curl_init(); curl_setopt($ch, CURLOPT_URL, 'https://<instance name>.service-now.com/incident_list.do?CSV'); curl_setopt($ch, CURLOPT_HEADER, 0); curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1); curl_setopt($ch, CURLOPT_FOLLOWLOCATION, true); curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC); curl_setopt($ch, CURLOPT_USERPWD, $userPass); 

 $data = curl_exec($ch); $info = curl_getinfo($ch); 

 if ($output === false) { $output = "No cURL data returned for $addr [". $info['http_code']. "]"; if (curl_error($ch)) $output .= "\n". curl_error($ch); print $output; } else{ echo $data; } curl_close($ch); ?>

JSONv2 web service

The ability to describe sets of data in JSON format is a natural extension to the JavaScript language.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 387

ServiceNow supports a web service interface that operates on the JSON object as the data input and output format.

The JSONv2 web service is provided by a platform-level processor similar to the services for SOAP, WSDL, CSV, Excel, and XML. Like those services, the JSON web service is triggered by a standalone JSONv2 URL parameter. For example:

https://<instance name>.service-now.com/mytable.do?JSONv2

Having the JSON object available as a data format for web services means that you can create (insert), update, and query any data in the system using the JSON object format, and get results in the JSON object format.

##### Security

Like all other HTTP-based web services available on the platform, the JSONv2 web service is required to authenticate using basic authentication by default. The user ID that is used for authentication is subjected to access control in the same way as an interactive user.

Related topics

SOAP web services security

JSON object format

The JSON object is built in two structures.

**-** A collection of name/value pairs. In various languages, this is realized as an object, record, struct, dictionary, hash table, keyed list, or associative array.

**-** An ordered list of values. In most languages, this is realized as an array, vector, list, or sequence.

In its simplest form, a JSON object is just a comma delimited set of name/value pairs. For example:

{"name one":"value one","name two":"value two"}

The following is a sample of a single record array of incidents in JSON:

{"records": [{"closed_by":"", "\_\_status": "success", "category":"inquiry", "escalation":"0", "state":"1", "location":"", "reassignment_count":"0", "time_worked":"", "order":"0", "due_date":"", "number":"INC0010180", "upon_approval":"proceed", "sla_due":"2010-03-04 22:51:49", "follow_up":"", "notify":"1", "business_stc":"0", "caused_by":"", "rejection_goto":"", "assignment_group":"d625dccec0a8016700a222a0f7900d06",

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 388

"incident_state":"1", "opened_at":"2010-02-23 22:51:49", "wf_activity":"", "calendar_duration":"", "group_list":"", "caller_id":"", "comments":"", "priority":"3", "sys_id":"fd0774860a0a0b380061bab9094733ad", "sys_updated_by":"itil", "variables":"", "delivery_task":"", "sys_updated_on":"2010-02-23 22:51:49", "parent":"", "active":"true", "opened_by":"681b365ec0a80164000fb0b05854a0cd", "expected_start":"", "sys_meta":"System meta data", "watch_list":"", "company":"", "upon_reject":"cancel", "work_notes":"", "sys_created_by":"itil", "cmdb_ci":"", "approval_set":"", "user_input":"", "sys_created_on":"2010-02-23 22:51:49", "contact_type":"phone", "rfc":"", "approval_history":"", "activity_due":"", "severity":"3", "subcategory":"", "work_end":"", "closed_at":"", "close_notes":"", "variable_pool":"", "business_duration":"", "knowledge":"false", "approval":"not requested", "sys_mod_count":"0", "problem_id":"", "calendar_stc":"0", "work_start":"", "sys_domain":"global", "sys_response_variables":"", "correlation_id":"", "sys_class_name":"incident", "short_description":"this was inserted with python", "impact":"1", "description":"", "correlation_display":"", "urgency":"3", "assigned_to":"", "made_sla":"true", "delivery_plan":""}

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 389

] }

The following is a record array of incident responses with an error.

{ "records": [ { "**error": { "message": "Invalid Insert into: incident", "reason": "Data Policy Exception: Short description is mandatory " }, "**status": "failure", "active": "true", "activity_due": "", "approval": "not requested", "approval_history": "", "approval_set": "", "assigned_to": "", "assignment_group": "d625dccec0a8016700a222a0f7900d06", "business_duration": "", "business_stc": "", "calendar_duration": "", "calendar_stc": "", "caller_id": "", "category": "inquiry", "caused_by": "", "child_incidents": "0", "close_code": "", "close_notes": "", "closed_at": "", "closed_by": "", "cmdb_ci": "", "comments": "", "comments_and_work_notes": "", "company": "", "contact_type": "phone", "correlation_display": "", "correlation_id": "", "delivery_plan": "", "delivery_task": "", "description": "", "due_date": "", "escalation": "0", "expected_start": "", "follow_up": "", "group_list": "", "impact": "3", "incident_state": "1", "knowledge": "false", "location": "", "made_sla": "true", "notify": "1", "number": "INC0010001", "opened_at": "2013-07-23 18:01:17",

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 390

"opened_by": "6816f79cc0a8016401c5a33be04be441", "order": "", "parent": "", "parent_incident": "", "priority": "5", "problem_id": "", "reassignment_count": "0", "reopen_count": "0", "resolved_at": "", "resolved_by": "", "rfc": "", "severity": "3", "short_description": "", "skills": "", "sla_due": "", "state": "1", "subcategory": "", "sys_class_name": "incident", "sys_created_by": "admin", "sys_created_on": "2013-07-23 18:01:17", "sys_domain": "global", "sys_id": "a96479343cb60100a92ec9a477ba9e45", "sys_mod_count": "0", "sys_updated_by": "admin", "sys_updated_on": "2013-07-23 18:01:17", "time_worked": "", "upon_approval": "proceed", "upon_reject": "cancel", "urgency": "3", "user_input": "", "watch_list": "", "work_end": "", "work_notes": "", "work_notes_list": "", "work_start": "" } ] }

JSON response status

JSONv2 requests may return one of several response statuses.

##### JSON Success Response

Each JSON success response includes a record array containing the records retrieved by the given action. Each JSON object contains one or more metadata elements, prefixed with \_\_, regarding the status for the action on each record, as illustrated in the previous examples. The JSON success responses use the following syntax:

\_\_status

"\_\_status": "<value>"

where <value> is success or failure.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 391

##### JSON Failure Response

When the \_status element returns failure, the \_error element is added to identify the error and reason.

"\_\_error": { "message": "<error value>", "reason": "<reason value> "}

where <error value> is the error message text and <reason value> is the reason the error was triggered.

The JSON error response contains only the error and reason elements. Generally, this indicates that the whole JSON operation failed and no records can be processed.

For example:

{"\_error":"Cannot update with empty sysparm_query","reason":null}

Setting the number of rows returned

The following system property controls how many rows JSON returns with each query.

Setting the Number of Rows Returned

Property Description

glide.processor.json.row_limit Specify the maximum number of rows a JSON query returns.

**-** Type: Integer

**-** Default value: 10,000

**-** Location: Add glide.processor.json.row_limit to the system properties [sys_properties] table

Requiring basic authentication for incoming JSONv2 requests

The following system property controls whether basic authentication is required for incoming JSONv2 requests.

Requiring Basic Authentication for Incoming JSONv2 Requests

Property Description

###### glide.basicauth.required.jsonv2 Enables (true) or disables (false) requiring basic

authentication for incoming JSONv2 requests.

**-** Type: true | false

**-** Default value: true

**-** Location:Add to the System Properties [sys_properties] table

##### Note: To learn more about this property, see Basic auth: JSONv2 requests in Instance

Security Hardening Settings.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 392

Action parameters

Action parameters are separate and different from data parameters because they specify the action to take when the JSON object parameter is part of an HTTP GET or POST request.

The parameters can also be specified as a field in the supplied JSON object. They have the effect of triggering an action in the case of sysparm_action, or filtering the results of an update or query in the case of sysparm_query.

##### sysparm_action

The following are the valid values for sysparm_action and the corresponding action triggered by the API.

Data Retrieval

Method Summary

Description

getKeys Query the targeted table using an encoded query string and return a comma delimited list of sys_id values.

getRecords Query the targeted table using an encoded query string and return all matching records and their fields.

get Query a single record from the targeted table by specifying the sys_id in the sysparm_sys_id URL parameter, and return the record and its fields.

Data Modification

Method Summary

Description

insert Create one or more new records for the table targeted in the URL.

insertMultiple Create multiple new records for the table targeted in the URL.

update Update existing records in the targeted table in the URL, filtered by an encoded query string.

deleteRecord Delete a record from the table targeted in the URL by specifying its sys_id in the sysparm_sys_id URL parameter.

deleteMultiple Delete multiple records from the table targeted in the URL, filtered by an encoded query string.

##### sysparm_query

Specify an encoded query string to be used in get, getRecords, update or deleteMultiplesysparm_action value.

##### sysparm_view

Specify a form view to customize the return values for get and getRecords function calls. When using a view, the query returns only the fields defined in the view, including referenced values. If there is no view name, or if the view name is not valid, then the query returns all field names that are marked active in the dictionary.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 393

##### sysparm_sys_id

Specify a target sys_id during a get or delete function call (sysparm_action value).

##### sysparm_record_count

Specify an integer value to limit the number of records retrieved for this request. Note that this

###### value is capped by the glide.processor.json.row_limit system property.

##### displayvalue

Get the display value of a reference field, if any are in the record. For example, the Incident record can have an assigned_to field that is a reference to a user record. Instead of sending the sys_id of the user record, the user name is sent.

The displayvalue parameter can have three values: true , false , or all.

**- true** : All the references fields show the display value instead of sys_id.

**- false** (default): All reference fields show sys_ids.

**- all** : The display value and the sys_id are shown. For example, the assignedto field in the Incident record is sent back as assigned_to:1234556, dv_assigned_to:Fred Luddy.

##### displayvariables

Set this boolean value to true during a get or getRecords function call to retrieve all variables attached to this record.

JSON Data Retrieval API

Query for data by issuing an HTTPS GET request to the instance.

###### By default, a GET request is interpreted as a get function if a sysparm_sys_id parameter

is present. Otherwise, it is interpreted as a getRecords function. You can also specify a URL

###### parameter sysparm_action=get. Query responses are always encapsulated by a records

hash of records, where each individual record's values are themselves hashed by field name.

##### Return Display Value for Reference Variables

When you are getting a record from a get or getRecords function, all the fields associated with that record are returned. The fields are often reference fields that contain a sys_id for another table. The base system behavior is to return the sys_id value for those fields. To have the display value for the field returned, use one of these options:

**-** Add the property glide.json.return_displayValue to the system properties, and every JSON request will return a display value for a reference field.

**-** Add the parameter displayvalue=true to the JSON request URL and JSON requests with that parameter will return a display value instead of the sys_id for a reference field. The JSON URL would look like this:

https://<instance name>.service-now.com/incident.do?JSON&sysparm_action=getRecor ds&sysparm_query=active=true^category=hardware&displayvalue=t rue

**-** Add the parameter displayvalue=all to the JSON request URL and JSON requests with that parameter return a display value and the sys*id for a reference field. The response element name for the display value field will be prefixed with dv*, for example dv_caller_id.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 394

##### Get variables

###### Use the displayvariables query parameter to return an array of variables associated with a

###### Service Catalog item record. To get variables, add the parameter displayvariables=true

to the JSON request URL. For example, here is a URL to retrieve a record in JSON format that includes Service Catalog variables:

https://<your-instance>.servicenow.com/sc_req_item.do?JSONv2&sys parm_action=getRecords&sysparm_query=sys_id=5018da81742bd410f877 1974894916fe&displayvariables=true

Here is the example response that displays a multi-row variable set from the record:

{ "records":[ { … "variables":[ { "display_value":[ { "quantity":"1", "color":"Black", "device_type":"Apple iPhone 8", "storage":"64GB" }, { "quantity":"1", "color":"Black", "device_type":"Apple iPhone 8", "storage":"64GB" } ], "columns_meta":[ { "name":"device_type", "label":"Device Type", "id":"da7d3f3241411300964ff05369414eca", "type":5, "order":"0" }, { "name":"storage", "label":"Storage", "id":"691e337241411300964ff05369414e31", "type":5, "order":"1" }, { "name":"color", "label":"Color", "id":"e89fb77241411300964ff05369414e74", "type":5, "order":"2" }, { "name":"quantity",

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 395

"label":"Quantity", "id":"2d5f737241411300964ff05369414eaf", "type":5, "order":"3" } ], "max_rows":50, "name":"mobile_devices_set", "id":"e84d3f3241411300964ff05369414e3e", "type":"one_to_many", "value":[ { "quantity":"1", "color":"black", "device_type":"iphone8", "storage":"64GB" }, { "quantity":"1", "color":"black", "device_type":"iphone8", "storage":"64GB" } ], "row_count":2 }, { "question_text":"Department", "name":"department", "type":8, "value":"Development", "order":100 }, { "question_text":"Who is this request for?", "name":"requested_for", "type":8, "value":"System Administrator", "order":100 }, { "question_text":"When do you need this?", "name":"needed_by", "type":5, "value":"Today", "order":200 }, { "question_text":"Business Justification", "name":"business_justification", "type":2, "value":"Example justification", "order":200 } ], … }

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 396

] }

The keys in the response are defined as follows:

Key Description

display_value Multi-row variable set question display value. Only returned with multi-row variable sets.

columns_meta Array of multi-row variable set metadata, such as the sys_id and name of the field. Only returned when the variable contains multiple fields.

max_rows Maximum rows allowed in the multi-row variable set. Only returned with multi-row variable sets.

name Question name.

id Sys_id of the multi-row variable set. Only returned with multi-row variable sets.

type Type of question.

value Question value.

row_count Current number of rows in the multi-row variable set. Only returned with multi-row variable sets.

question_text Question label. Only returned with single-row variable sets.

order Order of the question.

##### Control the order of records

You can control the order that records appear in the JSON response. To set an order, use the ORDERBY or ORDERBYDESC clauses in the URL encoded query. For example,

sysparm_query=active=true^ORDERBYnumber^ORDERBYDESCcategory

filters all active records and orders the results in ascending order by number first, and then in descending order by category. For more information, see Encoded query strings.

##### getKeys

Get the sys_id of multiple records by specifying an encoded query string in the

###### sysparm_query parameter.

https://<instance name>.service-now.com/incident.do?JSONv2&sysparm_action=getKeys &sysparm_query=active=true^category=hardware

##### get

###### Get a record directly by specifying the sys_id in a sysparm_sys_id parameter.

https://<instance name>.service-now.com/incident.do?JSONv2&sysparm_sys_id=9d38501 7c611228701d22104cc95c371

###### Optionally, you may also specify the sysparm_action parameter:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 397

https://<instance name>.service-now.com/incident.do?JSONv2&sysparm_action=get&sys parm_sys_id=9d385017c611228701d22104cc95c371

##### getRecords

###### Get all records by specifying an encoded query string in the sysparm_query parameter.

https://<instance name>.service-now.com/incident.do?JSONv2&sysparm_action=getReco rds&sysparm_query=active=true^category=hardware

JSON Data Modification API

Modify data using the JSON web service by sending an HTTPS POST request to the instance.

The HTTP POST must contain a sysparm_action parameter to indicate the type of action to be performed, with the incoming JSON object post in the body.

##### Note: The content-type of the POST should be application/json. It cannot be application/

x-www-form-urlencoded or multipart/form-data.

##### insert

Create a new record in ServiceNow. The JSON object has to be POSTed as the body (contenttype is usually application/json, although not enforced). The response from the record creation is a JSON object of the incident that was created.

For example, posting the following JSON object:

{"short_description":"this is a test","priority":"1"}

to the following URL:

https://your_instance.service-now.com/incident.do?JSONv2&sysparm \_action=insert

creates an incident.

Optionally, you may also specify the sysparm_action in the JSON object. The parameter inside the JSON object takes precedence over the URL parameter. For example:

{"sysparm_action":"insert","short_description":"this is a test","priority":"1"}

##### insertMultiple

To create multiple new records in ServiceNow, the input JSON object for the insert function must be an array. The response from the record creation is a JSON object of the incidents that were created. For example, the following JSON object:

{ "records" : [ { "short_description" : "this was inserted with python using JSON 1" , "priority" : "1 Critical" , "impact" : "1" , "caller_id" : "Fred Luddy" } , { "short_description" : "this was inserted with python using JSON 2" , "priority" : "1

- Critical" , "impact" : "1" , "caller_id" : "Fred Luddy" } ] }

posted to one the following URLs:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 398

https://<instance name>.service-now.com/incident.do?JSONv2&sysparm_action=insert https://<instance name>.service-now.com/incident.do?JSONv2&sysparm_action=insertM ultiple

creates two incidents. Note the fields described as an array value for the records field.

##### update

Update a record or a list of records filtered by an encoded query string specified by the sysparm_query URL parameter. The JSON object has to be posted as the body (content-type is usually application/json, although not enforced). The response from the record creation is an array of JSON objects representing the records that were updated.

For example, posting the following JSON object:

{"short_description":"this was updated with python", "priority": "3", "impact":"1"}

to the following URL:

https://instance_name.service-now.com/incident.do?JSONv2&sysparm \_query=priority=3&sysparm_action=update

updates all incidents with priority 3, and sets the values specified by the JSON object.

##### deleteRecord

Delete a single record from the targeted table, identified by a sysparm_sys_id parameter. The parameter may be encoded in the input JSON object or given as a URL parameter.

For example, posting:

{"sysparm_sys_id":"fd4001f80a0a0b380032ffa2b749927b"}

to the following URL:

http://instance_name.service-now.com/incident.do?JSONv2&sysparm_ action=deleteRecord

deletes the incident record identified by the sys_id fd4001f80a0a0b380032ffa2b749927b.

##### deleteMultiple

Delete multiple records from the targeted table, filtered by an encoded query string specified in the sysparm_query URL parameter. The filter may also be encoded in the input JSON object.

For example, posting:

{"sysparm_query":"short_description=this was updated with python"}

to the following URL:

http://instance_name.service-now.com/incident.do?JSONv2&sysparm_ action=deleteMultiple

deletes all incident records where the short_description field contains the value "this was updated with python".

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 399

RSS web service

RSS (Rich Site Summary) is a format for delivering web-based information that changes regularly.

RSS feed generator

ServiceNow supports the dynamic generation of RSS feeds.

Much like our Web Services implementation, the retrieval of an RSS feed representation of information is simply done by specifying an RSS parameter at the end of the URL to a table list. For example, the following will return a list of all incidents in RSS 2.0 format.:

##### Adding a Query

###### To associate a query to the list so that a filtered list is returned, use the sysparm_query

parameter. For example, the following will return a list of all incidents where the priority field is 1 (Critical):

https://<instance name>.service-now.com/incident.do?sysparm_query=priority=1&RSS

If you have a multi part query then you would separate the parts with the ^ character. For example to get all priority 1 incidents with a category of software you would:

https://<instance name>.service-now.com/incident.do?sysparm_query=priority=1^cate gory=software&RSS

If you want to query on a field that is a reference to another file then you need to use javascript to resolve the reference to the other file. For example, the assigned_to field in incident is a reference to a user record. If you wanted to find all the incidents assigned to "ITIL User" then you would do the following:

https://<instance name>.service-now.com/incident.do?sysparm_query=assigned_to=jav ascript:GetIDValue('sys_user','ITIL%20User')&RSS

##### Note: You can in most cases simply append "&RSS" to a URL that you generate in the

U.I. or that of your favorite module. The easiest way to get the URL is to simply click the last breadcrumb from the list view. After appending "&RSS" then you can use this URL in your RSS feed reader

Get Bread URL

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 400

Limiting results with a view

The description element in the returned RSS xml is constructed using the view as specified in the URL, when no view is specified, the default no-name view is used.

###### To change this format, specify the sysparm_view parameter on the URL. For example, the

following request will return the incidents list. However the result will be restricted to only the fields available in the ess view:

https://<instance name>.service-now.com/incident.do?sysparm_query=priority=1&sysp arm_view=ess&RSS

###### Additionally, the RSS item title can be modified using the sysparm_title_view URL

parameter. When specified, the item title will be constructed using the fields specified in the view. For example:

https://<instance name>.service-now.com/incident.do?sysparm_query=priority=1&sysp arm_view=ess&sysparm_title_view=rss_title&RSS

Formatting results

The description element in the returned RSS xml can be formatted by setting the URL

###### parameter sysparm_format=true and specifying the format string in the property

###### glide.rss.description_format.

By default, when the URL parameter is present, the description element will be formatted to contain the field label and value using the following format string:

<b>{1}</b>: {2}<br/>

**-** {0} - field name

**-** {1} - field label

**-** {2} - field value

This default format string can be overridden using the property

###### glide.rss.description_format. An example of the formatted RSS feed can be seen in

the following screen capture from Firefox:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 401

RSS Format

RSS basic authentication

To enforce basic authentication on each request for an RSS feed, set the property

###### glide.basicauth.required.rss to true.

RSS request would have to contain the Authorization header as specified in the Authentication protocol. Because the request is non-interactive, we always require the Authorization header during a request.

##### Note: If you plan to disable RSS basic authentication, make sure that tables in the

platform have the right ACL entries to protect from unauthorized access.

To specify basic authentication on the URL, put the username and password pair separated by a colon in front of the server name before an @ character. For example, to submit the demo credentials for the ITIL user, use the following URL.

https://itil:itil@<instance name>.service-now.com/incident.do?RSS

Some older browsers, such as Microsoft IE 7 do not support direct URL authentication. If the site uses basic authentication, Internet Explorer automatically prompts users for a user name and a password. In some cases, users can click the Remember my password box in the prompt to save their credentials for later visits to that site.

Related topics

http://www.w3.org/Protocols/HTTP/1.0/draft-ietf-http-spec.html⌘BasicAABasic

http://support.microsoft.com/kb/834489

RSS request authorization

RSS title override

You may optionally override the automatically generated title of the RSS feed by added the

###### sysparm_title parameter to the request URL.

For example, you can specify the title Priority One Incidents using the following request URL.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 402

https://<instance name>.service-now.com/incident.do?sysparm_query=priority=1&sysp arm_view=ess&RSS&sysparm_title=Priority%20One%20Incidents

This will produce results as follows:

RSS Out

RSS feed reader

Create a scrolling RSS feed reader using a UI page.

You must create a feed parser using an RSS API, such as the Google Feed API.

Developer's guide: http://code.google.com/apis/ajaxfeeds/documentation/

API: http://code.google.com/apis/ajaxfeeds/documentation/reference.html

Scrollable areas

A scrollable area is a div where contents scroll from the bottom up over time.

You can scroll any HTML content, and anything inside the scroller is operational HTML with functioning links and images.

To make a scrollable areas, wrap the scrolling content inside of a scrollable_area tag, likely in a UI Page:

<g:scrollable_area height="100px"> <g2:evaluate var="jvar_temp" expression="var kb = new GlideRecord('kb_knowledge');"/> <g:inline template="kb_section.xml"/> </g:scrollable_area>

The system will then create a 100 pixel high div and the contents will automatically scroll from bottom to top. If you have a 1000 pixel high block of text, for example, you'll see the top 100 pixels and then pixels 2-101, then 3-102, etc. Once it reaches the top it'll wrap back around to the bottom.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 403

This sample code will create a scroller with a list of priority 1 incidents.

 <?xml version="1.0" encoding="utf-8" ?> <j:jelly trim="false" xmlns:j="jelly:core" xmlns:g="glide" xmlns:j2="null" xmlns:g2="null"> <g2:evaluate var="jvar_inc"> var inc = new GlideRecord('incident'); inc.addActiveQuery(); inc.addQuery('priority',1); inc.query(); </g2:evaluate>

<g2:scrollable_area height="100px"> <table border="0" cellspacing="2" cellpadding="0" width="100%"> <j2:while test="$[inc.next()]"> <j2:set var="jvar_inc_link" value="incident.do?sys_id=$[inc.sys_id]"/> <j2:set var="jvar_inc_list_link" value="incident_list.do?sysparm_query=active=true"/> <tr> <td> <a href="$[jvar_inc_link]"> <IMG SRC="images/services.png" style="padding-right:10px"></IMG> </a> <a href="$[jvar_inc_link]" style="padding-right:10px; color:blue">$[inc.number]</a> </td> <td>$[inc.short_description]</td> </tr> </j2:while> <tr> <td align="center" colspan="2"><a href="$[jvar_inc_list_link]" style="color:blue">View all active incidents</a></td> </tr> </table> </g2:scrollable_area> </j:jelly>

Add scrolling elements in forms

You can add scrolling areas to forms as well as UI pages.

###### Procedure

**1.** Create a UI Macro with the script.

**2.** Create a Formatter to reference the script.

Priority 1 incidents example

This example scrolling element demonstrates how to create a UI macro to a scrolling list of priority 1 incidents.

Use the following example code:

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 404

 <?xml version="1.0" encoding="utf-8" ?> <j:jelly trim="false" xmlns:j="jelly:core" xmlns:g="glide" xmlns:j2="null" xmlns:g2="null"> <g2:evaluate var="jvar_inc"> var inc = new GlideRecord('incident'); inc.addActiveQuery(); inc.addQuery('priority',1); inc.query(); </g2:evaluate>

 <div style="background-color:DDDDDD; padding-left:10px; line-height:19px; border:2px white solid" width="100%" nowrap="true"> Priority 1 Incidents: <input id="make_spacing_ok" style="visibility:hidden;width:0px:" title=""/> </div> <g2:scrollable_area height="100px" width="100%">

<j2:while test="$[inc.next()]"> <j2:set var="jvar_inc_link" value="incident.do?sys_id=$[inc.sys_id]"/> <j2:set var="jvar_inc_list_link" value="incident_list.do?sysparm_query=active=true"/> <span style="line-height: 10px; padding-left:10px"> <a href="$[jvar_inc_link]"> <IMG SRC="images/services.png" style="padding-right:10px"></IMG> </a> <a href="$[jvar_inc_link]" style="padding-right:10px; color:blue">$[inc.number]</a> $[inc.short_description] </span> <br style="line-height:5px"/> </j2:while> <span> <a href="$[jvar_inc_list_link]" style="color:blue; padding-left:10px">View all active incidents</a> </span>

</g2:scrollable_area> </j:jelly>

Navigate to System UI > Formatters and create a Formatter that refers to the UI Macro above.

RSS feed reader example

An example of how to set up an RSS feed reader using an RSS feed.

For an example RSS feed reader, go to the ServiceNow Community site and search for RSS Feed Reader.

Exporting and converting records into complex data types

Use URL parameters to export table records and convert them into complex data types, such as JSON, XML, PDF, CSV, and XLS.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 405

##### Exporting records as complex data types

###### You can use an HTTP GET request to retrieve records from a table and put them in a specified

###### format. For example, use the PDF parameter in a GET request to export records from a table

###### as PDF files; use the XLS parameter to export records from a table as XLS files. For example,

###### to retrieve a list of incident records as XLS files, issue an HTTP GET using the following URL:

https://instance_name.service-now.com/incident.do?XLS. The file returned

###### is incident.xls. incident.do is basically a GET that returns a list of the records from the

###### incident table. The XLS parameter converts those records into XLS files.

The general syntax is: https://<serviceNow-instance-name>/<tablename>.do?<Data-type-parameter>

##### URL parameters

###### The following table shows URL parameters you can use in GET requests, filters you can use

###### to filter out unwanted table records in the return, and an indicator of whether you can POST

the data type directly to a table. The parameter becomes the extension of the returned file, for

###### example, using the XLS parameter returns a file in the form <table-name>.xls.

URL parameters

Data type Parameter Valid filters Directly POST to table?

CSV CSV sysparm_query, sysparm_view Y

Excel XLS, EXCEL, XLSX sysparm_query, sysparm_view Y

JSON JSONv2 Various. See JSON data retrieval API.

Y

PDF PDF sysparm_query, sysparm_view N

RSS RSS sysparm_query, sysparm_view and more. See Limiting results with a view.

N

XML XML, XSD, SCHEMA sysparm_query, useUnloadFormat

N

For more information about retrieving and converting table records into the JSON file format, see JSONv2 Web Service.

For more information about retrieving and converting table records into the RSS file format, see RSS feed generator.

##### Converting records to PDFs

For PDF export, there is a distinction between targeting a table and targeting its list. To generate a PDF of a list of records, suffix the target with \_list. To target a single record, you must specify

###### the sys_id parameter to identify the record for which you are generating the PDF.

##### Filters

All URL parameters work with filters that enable you to export a subset of table records.

###### For example, sysparm_query=active=true in a GET request exports only

active records. The following example exports only active incident records in an Excel format: https://instance_name.service-now.com/incident.do? EXCEL&sysparm_query=active=true.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 406

The general syntax is: https://<serviceNow-instance-name>/ <table_list>.do?<Data-type-parameter>&<filter>

Filters include:

**-** sysparm_query—Filters the data using the encoded query before exporting files, for example, sysparm_query=active=true exports only active records.

**-** sysparm_view—Specify the name of a list view to control which fields are returned. For example, to return the ESS view, use sysparm_view=ess.

**-** useUnloadFormat—Indicates that the XML format returned is an unload format. The unload format is the same format you get when, from a list in the UI, you select Export > XML > ... You can import unload-formatted XML files back into the tables. To enable the unload format from a URL, use the useUnloadFormat=true URL parameter, for example, https://instance_name.service-now.com/incident.do? XML&useUnloadFormat=true.

##### Example GET queries

GET request examples

Data type Example query

CSV https://instance_name.service-now.com/incident.do? CSV&sysparm_query=active=true

Excel https://instance_name.service-now.com/incident.do? XLS&sysparm_query=active=true

PDF https://instance_name.service-now.com/incident.do? PDF&sysparm_view=ess

RSS https://instance_name.service-now.com/incident.do? RSS&sysparm_view=ess

XML https://instance_name.service-now.com/incident.do? XML&sysparm_query=active=true

##### Returned files

###### GET queries return records from a table in the format specified in the request. For example, a

###### query that uses the XLS parameter returns a table record in a file with the .xls extension.

The Content-Disposition header in the response displays the file name and extension of the returned file. The file name is based on the table you export from, such as incident.xls, incident.pdf, or incident.xml.

##### Exporting data into tables

###### You can POST the following data types directly into tables:

**-** CSV

**-** Excel

**-** JSON

The file headers must match the field columns in the targeted table. For more information, see Post CSV or Excel files directly to an import set.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 407

Inbound web service examples

Inbound web service examples demonstrate how to access ServiceNow web services.

Java Apache Axis2 web services client examples

Examples demonstrating an integration with Axis2 Version 1.4.

##### Requirements

**-** An "elementFormDefault" value of qualified means that an unqualified element is in the default namespace defined on an ancestor. If it is "unqualified" then an unqualified element is in the empty namespace (xmlns=""). The default is "unqualified".

**-** To Resolve the Axis Client deserialization failure you should go to **System Properties** > **Web Services** and uncheck the property that sets the elementFormDefault attribute of the embedded XML schema to the value of unqualified. Save the property setting and regenerate your Axis2 client code if your client code was generated before changing this property.

Element Form Default Property

Java Apache Axis2 web services client examples insert

An example class to insert an incident record.

public class Insert {

public static void main ( String args [ ] ) { try { HttpTransportProperties. Authenticator basicAuthentication = new HttpTransportProperties. Authenticator ( ) ; basicAuthentication. setUsername ( "admin" ) ; basicAuthentication. setPassword ( "admin" ) ;

ServiceNowStub proxy = new ServiceNowStub ( ) ;

proxy.\_getServiceClient ( ). getOptions ( ). setProperty (org. apache. axis2. transport. http. HTTPConstants. CHUNKED, Boolean. FALSE ) ; proxy.\_getServiceClient ( ). getOptions ( ). setProperty (org. apache. axis2. transport. http. HTTPConstants. AUTHENTICATE, basicAuthentication ) ;

ServiceNowStub. Insert inc = new ServiceNowStub. Insert ( ) ; ServiceNowStub. InsertResponse resp = new ServiceNowStub. InsertResponse ( ) ;

inc. setAssigned_to ( "Christen Mitchell" ) ; inc. setCategory ( "hardware" ) ; inc. setPriority ( BigInteger. ONE ) ; inc. setDescription ( "The WI_FI in the reception area is down" ) ; inc. setCaller_id ( "Joe Employee" ) ;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 408

resp = proxy. insert (inc ) ;

System. out. println ( "New Incident: " + resp. getNumber ( ) ) ; } catch ( Exception e ) { System. out. println (e. toString ( ) ) ; }

} }

Java Apache Axis2 web services client examples update

An example of an Axis Client program that calls the getKeys function to query all incidents where the category is Hardware.

##### getKeys

A list of sys_id is returned as a result:

package com.service_now.www ;

public class DemoClient {

public static void main ( String args [ ] ) { try { ServiceNowStub proxy = new ServiceNowStub ( ) ; ServiceNowStub. GetKeys getInc = new ServiceNowStub. GetKeys ( ) ; ServiceNowStub. GetKeysResponse resp = new ServiceNowStub. GetKeysResponse ( ) ;

getInc. setActive ( true ) ; getInc. setCategory ( "hardware" ) ;

proxy.\_getServiceClient ( ). getOptions ( ). setProperty (org. apache. axis2. transport. http. HTTPConstants. CHUNKED, Boolean. FALSE ) ;

resp = proxy. getKeys (getInc ) ;

String [ ] keys = resp. getSys_id ( ) ;

System. out. println ( "Key: " + keys [ 0 ] ) ; } catch ( Exception e ) { System. out. println (e. toString ( ) ) ; }

} }

##### getRecords

package com.service_now.www ;

import com.service_now.www.ServiceNowStub.GetRecordsResult_type0 ;

public class GetRecords {

/\*\* _ @param args _/ public static void main ( String [ ] args ) { try { ServiceNowStub proxy = new ServiceNowStub ( ) ;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 409

ServiceNowStub. GetRecords incidents = new ServiceNowStub. GetRecords ( ) ; ServiceNowStub. GetRecordsResponse result = new ServiceNowStub. GetRecordsResponse ( ) ;

incidents. setActive ( true ) ; incidents. setCategory ( "hardware" ) ; incidents. setSys_created_on ( "> 2009-06-08 10:30:00" ) ;

proxy.\_getServiceClient ( ). getOptions ( ). setProperty (org. apache. axis2. transport. http. HTTPConstants. CHUNKED, Boolean. FALSE ) ;

result = proxy. getRecords (incidents ) ;

GetRecordsResult_type0 [ ] keys = result. getGetRecordsResult ( ) ;

for ( int key = 0 ; key < keys. length ; key ++ ) { System. out. println ( "Key: " + keys [ 0 ]. getSys_id ( ) ) ; } } catch ( Exception e ) { System. out. println (e. toString ( ) ) ; }

}

}

Java Apache Axis2 web services client examples advanced

Examples showing how to construct and use an Axis2 client to consume a ServiceNow Web Service.

Axis is essentially a SOAP engine -a framework for constructing SOAP processors such as clients, servers, or gateways. The current version of Axis is written in Java. This content is intended for system admins with a light development background in Java. To begin you would need Java JDK version 1.4.2 or higher and Axis2 version 1.0 or higher.

##### Create a Java Project

This example uses Eclipse SDK Version: 3.4.2 for managing the source code and executing the web request. Eclipse is not required.

**-** Open Eclipse and from the menu select **File** > **New** > **Project** > **Java Project**.

**-** Give the project a name.

**-** Verify that the correct JRE is specified.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 410

◦ If using wsdl2java run "java -version" on the command line and this will be the version to specify for the project specific JRE.

◦ If using the Axis2 Codegen plugin use default JRE.

Java Project

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 411

##### Generate your Axis2 client code

**-** From a command line in the bin directory of the axis folder:

./wsdl2java.sh -uri https://<instance name>.service-now.com/incident.do?WSDL -o /glide/workspace/TestWebService/

**-** In the above example:

◦ The "-uri" is either the path where you have saved a copy of the wsdl to either ".wsdl" or ".xml", or the URL the WSDL resides at.

◦ The "-o" is the path where you want the files to be written out to. If not specified, the files will be written out to the current bin location.

**-** In Eclipse refresh the project and the generated Stub and CallbackHandler should now be displayed

Axis Stub

##### Basic Authentication

HttpTransportProperties.Authenticator basicAuthentication = new HttpTransportProperties. Authenticator ( ) ; basicAuthentication. setUsername ( "admin" ) ; basicAuthentication. setPassword ( "admin" ) ; ... ServiceNowStub proxy = new ServiceNowStub ( ) ; ...

proxy.\_getServiceClient ( ). getOptions ( ). setProperty (org. apache. axis2. transport. http. HTTPConstants. AUTHENTICATE, basicAuthentication ) ;

##### Compatibility with Axis2 Versions 1.1 and higher

Chunking support is only available in HTTP Version 1.1. By default chunking is enabled in Axis2.xml for versions 1.1 and higher. ServiceNow does not support Chunking, so you will need to disable chunking at deployment time or at runtime.

**-** Deployment time: One can disable HTTP chunking by removing or commenting out the following element from Axis2.xml

<parameter name= "Transfer-Encoding" >chunked</parameter>

**-** Runtime: User can disable the chunking using following property set in Client or Stub, versions 1.1.1 and higher only

options.setProperty (org. apache. axis2. transport. http. HTTPConstants. CHUNKED, Boolean. FALSE ) ;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 412

##### Creating Unique Packages

You can use the Axis2 parameter namespace2package (ns2p) to create unique package names. The parameter uses this format:

<Axis path>\bin\wsdl2java.bat -u -p cr2 -ns2p <namespace>=<package name> -uri <wsdl to convert>

For example:

<Axis path>\bin\wsdl2java.bat -u -p cr2 -ns2p http://www.service-now.com/change_request=my.change_request -uri change_request

Microsoft .NET web services client examples

Examples demonstrating an integration with Microsoft .NET Web Services Client.

##### Requirements

.NET 2.0 Versions and Higher:

**-** An "elementFormDefault" value of qualified means that an unqualified element is in the default namespace defined on an ancestor. If it is "unqualified" then an unqualified element is in the empty namespace (xmlns=""). The default is "unqualified".

**-** To Resolve the .NET Client deserialization failure you should go to **System Properties** > **Web Services** and uncheck the property that sets the elementFormDefault attribute of the embedded XML schema to the value of unqualified. Save the property setting and recreate your WSDL Reference.cs class. See Also "Compatibility with Clients generated from WSDL" below.

Element Form Default Property

Perl web services client examples

Examples demonstrating an integration with a Perl web services client.

##### Note: The following examples require the usage of the Perl language and the SOAP::Lite

package.

##### System Requirements

Perl 5.8

**-** SOAP::Lite (prerequisites [http://soaplite.com/prereqs.html](http://soaplite.com/prereqs.html) )

**-** Crypt::SSLeay

**-** IO::Socket::SSL

##### insert

The following example will insert a record into the Incident table.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 413

﷯!/usr/bin/perl -w

﷯ declare usage of SOAP::Liteuse SOAP::Lite;

﷯ specifying this subroutine, causes basic auth to ﷯use its credentials when challengedsub SOAP::Transport::HTTP::Client::get_basic_credentials{﷯ login as the itil userreturn'itil'=>'itil';}

﷯ declare the SOAP endpoint heremy$soap= SOAP::Lite->proxy('https:// myinstance.service-now.com/incident.do?SOAP');

﷯ calling the insert functionmy$method= SOAP::Data->name('insert')->attr({xmlns =>'http://www.service-now.com/'});

﷯ create a new incident with the following short_description and categorymy@params=( SOAP::Data->name(short_description =>'This is an example short description'));push(@params, SOAP::Data->name(category =>'Hardware'));

﷯ invoke the SOAP callmy$result=$soap->call($method=>@params);

﷯ print any SOAP faults that get returned print_fault($result);﷯ print the SOAP response that get return print_result($result);

﷯ convenient subroutine for printing all resultssub print*result {my($result)=@*;

if($result->body&&$result->body->{'insertResponse'}){my %keyHash=%{$result->body->{'insertResponse'}};foreachmy$k(keys%k eyHash){print"name=$k value=$keyHash{$k}\n";}}}

﷯ convenient subroutine for printing all SOAP faultssub print*fault {my($result)=@*;

if($result->fault){print"faultcode=".$result->fault->{'faultcod e'}."\n";print"faultstring=".$result->fault->{'faultstring'}."\n ";print"detail=".$result->fault->{'detail'}."\n";}}

##### insert (With XML payload)

The following is an example of inserting a record into the ecc_queue table where the payload field is an XML document. This is done using the Perl language and the SOAP::Lite package, the XML document creation uses the XML::Writer package :

﷯!/usr/bin/perl -w﷯use SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;use XML::Writer;use XML::Writer::String;

﷯﷯ Get parameters passed by OVO notification﷯$OVMSG{id}=$ARGV[0];$OVMSG{node_name}=$ARGV[1];$OV MSG{node_type}=$ARGV[2];$OVMSG{date_created}=$ARGV[3];$OVMSG{tim e_created}=$ARGV[4];$OVMSG{date_received}=$ARGV[5];$OVMSG{time_r

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 414

eceived}=$ARGV[6];$OVMSG{application}=$ARGV[7];$OVMSG{msg_grou p}=$ARGV[8];$OVMSG{object}=$ARGV[9];$OVMSG{severity}=$ARGV[10];$ OVMSG{operator_list}=$ARGV[11];$OVMSG{msg_text}=$ARGV[12];$OVMSG {instruction}=$ARGV[13];

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

my$soap= SOAP::Lite->proxy('http://<instance name>.service-now.com/ecc_queue.do?SOAP');

my$method= SOAP::Data->name('insert')->attr({xmlns =>'http://www.service-now.com/'});

﷯ get all incidents with category Networkmy@params=( SOAP::Data->name(agent =>'OVO_Notification'));push(@params, SOAP::Data->name(queue =>'input'));push(@params, SOAP::Data->name(name =>'HP Openview OVO Notification'));push(@params, SOAP::Data->name(source =>$OVMSG{id}));

my$s= XML::Writer::String->new();my$writer=new XML::Writer(OUTPUT =>$s);

﷯$writer-xmlDecl();$writer-startTag('notification');

write_element('id'); write_element('node_name'); write_element('node_type'); write_element('date_created'); write_element('time_created'); write_element('date_received'); write_element('time_received'); write_element('application'); write_element('msg_group'); write_element('object'); write_element('severity'); write_element('operator_list'); write_element('msg_text'); write_element('instruction');

$writer->endTag('notification');

$writer->end;

sub write_element {my $label=shift;my$value=$OVMSG{$label};$writer->startTag($label);i f($value){$writer->characters($value);}$writer->endTag($label);}

push(@params, SOAP::Data->name(payload =>$s->value()));

print$soap->call($method=>@params)->result;</pre>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 415

=== Response to the ''insert''===<source lang="xml"><?xml version="1.0" encoding="UTF-8"?><soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XML Schema-instance"><soap:Body><insertResponse xmlns="http:// http://www.service-now.com/ecc_queue"><sys_id>1a5ad50e0a0a021101bef2e07 705f87a</sys_id><name>HP Openview OVO Notification</name></insertResponse></soap:Body></soap:Envelo pe>

##### update

﷯!/usr/bin/perl -w

use﷯ SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

my$soap= SOAP::Lite->proxy('http:// localhost:8080/glide/incident.do?SOAP');

my$method= SOAP::Data->name('update')->attr({xmlns =>'http://www.service-now.com/'});

﷯ update incident by sys_idmy@params=( SOAP::Data->name(sys_id =>'e8caedcbc0a80164017df472f39eaed1'));push(@params, SOAP::Data->name(short_description =>'this is a new description'));

my$result=$soap->call($method=>@params);

print_fault($result); print_result($result);

sub print*result {my($result)=@*;

if($result->body&&$result->body->{'updateResponse'}){my %keyHash=%{$result->body->{'updateResponse'}};foreachmy$k(keys%k eyHash){print"name=$k value=$keyHash{$k}\n";}}}

sub print*fault {my($result)=@*;

if($result->fault){print"faultcode=".$result->fault->{'faultcod e'}."\n";print"faultstring=".$result->fault->{'faultstring'}."\n ";print"detail=".$result->fault->{'detail'}."\n";}}

##### getKeys

The following is an example of retrieving a list of s y s \_ i d s for records of Incident where C a t e g o r y is Network.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 416

﷯!/usr/bin/perl -w

use﷯ SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

my$soap= SOAP::Lite->proxy('http://<instance name>.service-now.com/incident.do?SOAP');

my$method= SOAP::Data->name('getKeys')->attr({xmlns =>'http://www.service-now.com/'});

﷯ get all incidents with category Networkmy@params=( SOAP::Data->name(category =>'Network'));

print$soap->call($method=>@params)->result;

##### get

The following is an example of retrieving an Incident record using its sys_id value.

﷯!/usr/bin/perl -w﷯use SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

my$soap= SOAP::Lite->proxy('http://<instance name>.service-now.com/incident.do?SOAP');

my$method= SOAP::Data->name('get')->attr({xmlns =>'http://www.service-now.com/'});

﷯ get incident by sys_idmy@params=( SOAP::Data->name(sys_id =>'9d385017c611228701d22104cc95c371'));

my %keyHash=%{$soap->call($method=>@params)->body->{'getResponse' }};

﷯ iterate through all fields and print themforeachmy$k(keys%keyHash){print"$k=$keyHash{$k}\n";}

##### getRecords

To query for an Incident using its incident number value:

﷯!/usr/bin/perl -w﷯use SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 417

my$soap= SOAP::Lite->proxy('http://<instance name>.service-now.com/incident.do?SOAP');

my$method= SOAP::Data->name('getRecords')->attr({xmlns ='http://www.service-now.com/'});﷯ get incident by numbermy@params=( SOAP::Data->name(number =>'INC10001'));

my %keyHash=%{$soap->call($method=>@params)->body->{'getRecordsResp onse'}->{'getRecordsResult'}};

﷯ iterate through all fields and print themforeachmy$k(keys%keyHash){print"$k=$keyHash{$k}\n";}

##### getRecords (Returning Multiple Results)

The following is an example of retrieving and displaying an array of Incident records by querying all Incidents that have a

C a t e g o r y of "Network"

﷯!/usr/bin/perl -w﷯use SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

my$soap= SOAP::Lite->proxy('http://<instance name>.service-now.com/incident.do?SOAP');

my$method= SOAP::Data->name('getRecords')->attr({xmlns =>'http://www.service-now.com/'});

﷯ get incident by sys_idmy@params=( SOAP::Data->name(category =>'Network'));

my %keyHash=%{$soap->call($method=>@params)->body->{'getRecordsResp onse'}};

my$i=0;my$size=@{$keyHash{'getRecordsResult'}};for($i=0;$i< $size;$i++){my %record=%{$keyHash{'getRecordsResult'}[$i]};print"----------------------------$i ----------------------------\n";foreachmy$kk(keys%record){print "$kk=$record{$kk}\n";}}

##### deleteRecord

﷯!/usr/bin/perl -w

use﷯ SOAP::Lite ( +trace => all, maptype => {} );use SOAP::Lite;

sub SOAP::Transport::HTTP::Client::get_basic_credentials{return'iti l'=>'itil';}

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 418

my$soap= SOAP::Lite->proxy('http:// localhost:8080/glide/incident.do?SOAP');

my$method= SOAP::Data->name('deleteRecord')->attr({xmlns =>'http://www.service-now.com/'});

﷯ delete incident by sys_idmy@params=( SOAP::Data->name(sys_id =>'46f67787a9fe198101e06dfcf3a78e99'));

my$result=$soap->call($method=>@params);

print_fault($result); print_result($result);

sub print*result {my($result)=@*;

if($result->body&&$result->body->{'deleteRecordResponse'}){my %keyHash=%{$result->body->{'deleteRecordResponse'}};foreachmy$k( keys%keyHash){print"name=$k value=$keyHash{$k}\n";}}}

sub print*fault {my($result)=@*;

if($result->fault){print"faultcode=".$result->fault->{'faultcod e'}."\n";print"faultstring=".$result->fault->{'faultstring'}."\n ";print"detail=".$result->fault->{'detail'}."\n";}}

Python web services client examples

Examples demonstrating an integration with a Python web services client.

##### Requirements

The following examples require the installation of the following Python modules:

**-** fpconst [http://pypi.python.org/pypi/fpconst/0.7.2](http://pypi.python.org/pypi/fpconst/0.7.2)

**-** PyXML [http://pyxml.sourceforge.net/topics/](http://pyxml.sourceforge.net/topics/)

**-** SOAPpy [http://pywebsvcs.sourceforge.net/](http://pywebsvcs.sourceforge.net/)

##### insert

This is an example of inserting an incident.

﷯!/usr/bin/python

from SOAPpy import SOAPProxy import sys

def createincident (params_dict ):

﷯ instance to send to instance = 'demo'

﷯ username/password username = 'itil'

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 419

password = 'itil'

﷯ proxy NOTE: ALWAYS use https://INSTANCE.service-now.com, not https://www.service-now.com/INSTANCE for web services URL from now on! proxy = 'https://%s:%s@%s.service-now.com/incident.do?SOAP' % (username , password , instance ) namespace = 'http://www.service-now.com/' server = SOAPProxy (proxy , namespace )

﷯ uncomment these for LOTS of debugging output ﷯server.config.dumpHeadersIn = 1 ﷯server.config.dumpHeadersOut = 1 ﷯server.config.dumpSOAPOut = 1 ﷯server.config.dumpSOAPIn = 1

response = server. insert (impact = int (params_dict [ 'impact' ] ) , urgency = int (params_dict [ 'urgency' ] ) , priority = int (params_dict [ 'priority' ] ) , category =params_dict [ 'category' ] , location =params_dict [ 'location' ] , caller_id =params_dict [ 'user' ] , assignment_group =params_dict [ 'assignment_group' ] , assigned_to =params_dict [ 'assigned_to' ] , short_description =params_dict [ 'short_description' ] , comments =params_dict [ 'comments' ] )

return response

values = { 'impact': '1' , 'urgency': '1' , 'priority': '1' , 'category': 'High' , 'location': 'San Diego' , 'user': 'fred.luddy@yourcompany.com' , 'assignment_group': 'Technical Support' , 'assigned_to': 'David Loo' , 'short_description': 'An incident created using python, SOAPpy, and web services.' , 'comments': 'This a test making an incident with python.\n Isn \' t life wonderful?' }

new_incident_sysid =createincident (values )

print "Returned sysid: "+ repr (new_incident_sysid )

##### getKeys

This is an example of executing getKeys on the demo instance using basic authentication.

﷯!/bin/env python

﷯ use the SOAPpy module from SOAPpy import SOAPProxy

username , password , instance = 'admin' , 'admin' , 'demo' proxy , namespace = 'https://username:password@www.service-now.com/'+instance+ '/incident.do?SOAP' , 'http://www.service-now.com/'

server = SOAPProxy (proxy ,namespace ) response = server. getKeys (category = 'Network' )

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 420

print response. sys_id. split ( ',' )

##### getRecords

In this example, we get an incident, querying for category == "Network" (with basic authentication).

﷯!/bin/env python

﷯ use the SOAPpy module from SOAPpy import SOAPProxy

username , password , instance = 'admin' , 'admin' , 'demo' proxy , namespace = 'https://username:password@www.service-now.com/'+instance+ '/incident.do?SOAP' , 'http://www.service-now.com/'

server = SOAPProxy (proxy ,namespace ) response = server. getRecords (category = 'Network' )

for record in response: for item in record: print item

##### get

In this example, we get an incident record by sys_id (with basic authentication).

﷯!/bin/env python

﷯ use the SOAPpy module from SOAPpy import SOAPProxy

username , password , instance = 'admin' , 'admin' , 'demo' proxy , namespace = 'https://username:password@www.service-now.com/'+instance+ '/incident.do?SOAP' , 'http://www.service-now.com/'

server = SOAPProxy (proxy ,namespace ) response = server. get (sys_id = '9c573169c611228700193229fff72400' )

for each in response: print each

##### Advanced

This is an example of advanced Python script that reads a log file for a keyword invalid spi and creates an ECC Queue record where the payload is set to an alert of XML format.

﷯!/bin/env python

﷯ kevin.pickard@service-now.com 2008.07.03 initial creation

from SOAPpy import SOAPProxy from xml. dom. minidom import getDOMImplementation import sys , os , socket , pickle , re

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 421

﷯ instance to send to instance = 'demo'

﷯ username/pass username = 'admin' password = 'admin'

﷯ log file to watch syslogfile = '/var/log/cisco.log.ksp'

﷯ state file statefile = '/tmp/syslog_ecc.state-test'

﷯ ECC queue values soapagent = 'SOAPpy' ecctopic = 'PIX Error: ' eccname = 'Invalid SPI: ' eccsource = 'Syslog'

﷯ regex string to match matchstring = 'invalid spi'

try: state = open (statefile , 'r' ) lastbyte = pickle. load (state ) state. close ( ) except: lastbyte = 0

﷯print 'DEBUG: lastbyte = '+str(lastbyte)

try: log = open (syslogfile , 'ro' ) except: errortopic = 'Script Error' errorname = 'Unable to open log file '+syslogfile+ '.' errorpayload = 'This message was generated due to an error condition encountered in a script. The name of the script is '+ os. path. basename ( sys. argv [ 0 ] )+ ' on server '+ socket. gethostname ( )+ '.'

proxy = 'https://'+username+ ':'+password+ '@'+instance+ '.service-now.com/ecc_queue.do?SOAP' namespace = 'http://www.service-now.com/' server = SOAPProxy (proxy , namespace ) server. config. dumpSOAPOut = 1 server. config. dumpSOAPIn = 1 response = server. insert (agent =soapagent , topic =errortopic , name =errorname , source = sys. argv [ 0 ] , payload =errorpayload )

sys. exit ( 1 )

if lastbyte != 0: try: log. seek (lastbyte ) except IOError: pass

loglines =log. readlines ( )

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 422

lastbyte =log. tell ( )

log. close ( )

state = open (statefile , 'w' ) pickle. dump (lastbyte , state ) state. close ( )

﷯ regex out the line matchedlines = [ ] for line in loglines: if re. search (matchstring , line ) != None: matchedlines. append (line )

﷯print 'DEBUG: len->loglines = '+str(len(loglines)) ﷯print 'DEBUG: lastbyte = '+str(lastbyte) ﷯print 'DEBUG: matchedlines = '+str(matchedlines)

if len (matchedlines ) == 0: sys. exit ( 0 )

proxy = 'https://'+username+ ':'+password+ '@'+instance+ '.service-now.com/ecc_queue.do?SOAP' namespace = 'http://www.service-now.com/'

server = SOAPProxy (proxy , namespace ) ﷯server.config.dumpSOAPOut = 1 ﷯server.config.dumpSOAPIn = 1

entriestosend = { } for line in matchedlines: device =line. split ( ) [ 3 ] sourceip =line. split ( ) [1 ] entriestosend [sourceip ] = [device , line ]

for key ,value in entriestosend. iteritems ( ): ﷯impl=getDOMImplementation() ﷯newdoc = impl.createDocument(None, "log_line", None) ﷯top_element = newdoc.documentElement ﷯text = newdoc.createTextNode(value[1]) ﷯top_element.appendChild(text)

response = server. insert (agent =soapagent , topic =ecctopic+value [ 0 ] , name =eccname+key , source =eccsource , payload =value [ 1 ] )

Web services C Sharp .NET end to end tutorial

Examples demonstrating how to use .NET to consume a ServiceNow web service.

This tutorial will show you how to configure ServiceNow correctly to receive a web service request from your .NET client, as well as how to consume our web services using C⌘ .NET.

Configure C sharp with .NET

Configure web services within ServiceNow.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 423

###### Procedure

**1.** To configure web services within ServiceNow, access the **System Properties** > **Web Services** module.

This module displays the system properties that are specific to web services within your instance. For security reasons, you will want to make sure that you require basic authorization for incoming SOAP requests. This ensures that only authenticated users will be able to make any web services calls, whether it be via web service import sets or inserting/deleting/ querying via direct web services.

**2.** This next step is very important if you are using .NET as a client to connect to ServiceNow. You

###### must set the elementFormDefault property to false.

This property defines how the WSDLs are qualified. Of course, if you do not consume our WSDL and just create the XML manually, then this property is irrelevant.

Call a web service in visual studio .NET

Call a web service using Visual Studio 2008.

In this example, we will be using Visual Studio 2008. First, create a new Windows Form Application for this example.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 424

Dot net project

On the resulting form, we created a richTextBox (which we named 'richTextBoxResult') and a button (named buttonResult).

Dot net example form

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 425

Use a service reference in a C Sharp integration

Use a wizard to add a service reference for a C Sharp integration.

Go to the Solutions Explorer and select Service References > Add Service Reference. A wizard will appear asking for an address. Use: https://<instance name>.service-now.com/incident.do? WSDL. Accept the defaults for the rest of the wizard.

Open the app.config file and change the Security mode to "Transport" and the clientCredentialType and proxyCredentialType to "Basic"

Dot net app config

Use a web reference in a C Sharp integration

Use a wizard to add a web reference for a C Sharp integration.

Go to the Solutions Explorer and select Service References > Add Service Reference. A wizard will appear. At the bottom of the form, there is an Advanced button. Click on it and click on the Add Web Reference button at the bottom of the new wizard page. This will start the Web Reference wizard. For the URL, use: https://<instance name>.service-now.com/incident.do? WSDL and name the web reference, 'WebReference1'. Accept the defaults for the rest of the wizard.

C Sharp integration source code

After defining the source code, insert it.

Now we are ready to insert the code. Double-click on the Send Web Service button on your form to open the backend code to the form that has been created. Here is the code to insert a record into the demo instance and to read the response.

using System; using System.Collections.Generic; using System.ComponentModel; using System.Data; using System.Drawing; using System.Linq; using System.Text; using System.Windows.Forms;

namespace ExampleWebServiceForWiki { public partial class FormMain : Form { public FormMain() { InitializeComponent(); }

private void buttonSend_Click(object sender, EventArgs e) {

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 426

/\* SERVICE REFERENCE-SPECIFIC CODE ServiceReference1.ServiceNowSoapClient soapClient = new ServiceReference1.ServiceNowSoapClient(); soapClient.ClientCredentials.UserName.UserName ="itil"; soapClient.ClientCredentials.UserName.Password ="itil";

ServiceReference1.insert insert = new ExampleWebServiceForWiki.ServiceReference1.insert(); ServiceReference1.insertResponse response = new ExampleWebServiceForWiki.ServiceReference1.insertResponse(); // END OF SERVICE REFERENCE CODE \*/

// WEB REFERENCE-SPECIFIC CODE WebReference1.ServiceNow_incident soapClient = new ExampleWebServiceForWiki.WebReference1.ServiceNow_incident(); System.Net.ICredentials cred = new System.Net.NetworkCredential("itil", "itil"); soapClient.Credentials = cred;

WebReference1.insert insert = new WebReference1.insert(); WebReference1.insertResponse response = new WebReference1.insertResponse(); // END OF WEB REFERENCE CODE

insert.category = "Category"; insert.comments = "Comments"; insert.short_description = "My short description";

try { response = soapClient.insert(insert); this.richTextBoxResult.Text = "Incident Number: " + response.number + "\n"; this.richTextBoxResult.Text += "Sys_id: " + response.sys_id; } catch (Exception error) { this.richTextBoxResult.Text = error.Message; } } }

}

C Sharp integration results

If you have followed the tutorial correctly, you should receive the result whether you used a Service Reference or a Web Reference.

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 427

Dot net tutorial results

Troubleshoot a null response in a C Sharp integration

Receiving a null response from ServiceNow's web service.

If you are receiving a "null" response from your web service in your client code, then you may have missed the step in this tutorial for setting the elementFormDefault setting to "False".

Remember to recompile your code against the WSDL after you have changed this setting and saved it.

Sample ASP.NET with C Sharp redirect with cookies

This sample ASP.NET code creates a simple authentication portal and passes an unencrypted HTTP header as a cookie.

##### Note: Functionality described here requires the Admin role.

##### Note: Cookies are domain specific and cannot be used across different network domains.

The only domain that can read a cookie is the domain that sets it. It does not matter what domain name you set. If you do not have an option of your SSO portal being in the same network domain as your ServiceNow instance (for example, in an on-premisis deployment,

###### an alternative is to pass the SSO token using URL GET or POST parameters.

This sample assumes:

**-** The web server supports ASP.NET and C⌘

**-** The target ServiceNow instance is https://<instance name>.service-now.com/

**-** SiteMinder or another single sign-on application has pre-authenticated the user

**-** The target ServiceNow instance expects an HTTP header of SM_USER

Change the ASP code to redirect users to the proper ServiceNow instance.

 <html xmlns="http://www.w3.org/1999/xhtml" > <head runat="server"> <title>Portal Page Login</title> <%-<meta http-equiv="REFRESH" content="0;url=https://<instance name>.service-now.com/">--%>

 </head> <body> <form id="form1" runat="server"> <h2><b> Portal Page Login </b></h2>

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 428

 <hr style="position: static" /> <br /> <asp:Label ID="Label2" runat="server" Font-Size="Larger" Height="21px" Style="position: static" Text="Instance URL:" Width="113px"></asp:Label> <asp:TextBox ID="urlBox" runat="server" Font-Size="Large" Style="position: static"></asp:TextBox><br /> <br /> <asp:Label ID="Label1" runat="server" Font-Size="Larger" Height="17px" Style="position: static;" Text="User Id:" Width="113px"></asp:Label> <asp:TextBox ID="userNameBox" runat="server" Font-Size="Large" Style="position: static;"></asp:TextBox>

<br /> <br /> <asp:Button ID="Button1" runat="server" Height="39px" Style="position: static;" Text="Ok" Width="88px" OnClick="Button1_click" /> </form> </body> </html> </asp>

ASP Portal Redirect

###### The following C⌘ code handles the OnClick button event for the form. The code:

**-** Creates the cookie "SM_USER"

**-** Performs a redirect to the URL specified on the ASP form.

Change the C⌘ code to create the proper cookie name.

using System; using System.Data;

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 429

using System.Configuration; using System.Web; using System.Web.Security;

public partial class \_Default : System.Web.UI.Page { protected void Page_Load(object sender, EventArgs e) {

} protected void Button1_click(object sender, EventArgs e) { try { HttpCookie myCookie = new HttpCookie("SM_USER"); myCookie.Value = userNameBox.Text; Response.Cookies.Add(myCookie); Response.Redirect(urlBox.Text);

}catch {} } }

Sample ASP Script for unencrypted single sign-on

This sample ASP.NET code creates a simple authentication portal and passes an unencrypted HTTP header as a URL parameter.

This sample assumes:

**-** The web server supports ASP.NET

**-** The target instance is https://<instance name>.service-now.com/

**-** SiteMinder or another single sign-on application has pre-authenticated the user

**-** The target instance expects an HTTP header of SM_USER

Change the ASP code to redirect users to the proper instance and create the proper HTTP header.

 <html xmlns = "http://www.w3.org/1999/xhtml" > <head runat = "server" > <title >Portal Page Login </ title > <%-<meta http-equiv = "REFRESH" content = "0;url=https://<instance name>.service-now.com/">--%>

 <script runat = "server" > 

 public void go_to(object sender, EventArgs e) { ////Send URL parameters String URL = urlBox.Text + "?SM_USER=" + userNameBox.Text; Response.Redirect(URL); } </ script > 

 </ head > <body > <form id = "form1" runat = "server" > <h2 >< b > Portal Page Login </ b >< / h2 > <hr style = "position: 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 430 


 static" / > <br / > <asp:Label ID = "Label2" runat = "server" FontSize = "Larger" Height = "21px" Style = "position: static"Text = "Instance URL:" Width = "113px" >< / asp:Label> <asp:TextBox ID = "urlBox" runat = "server" FontSize = "Large" Style = "position: static" >< / asp:TextBox> <br / > <br / > <asp:Label ID = "Label1" runat = "server" FontSize = "Larger" Height = "17px" Style = "position: static;"Text = "User Id:" Width = "113px" >< / asp:Label> <asp:TextBox ID = "userNameBox" runat = "server" FontSize = "Large" Style = "position: static;" >< / asp:TextBox> <br / > <br / > <asp:Button ID = "Button1" runat = "server" Height = "39px" Style = "position: static;" Text = "Ok"Width = "88px" OnClick = "go_to" / > </ form > </ body > </ html > 

 Designer 

##### Outbound web services 

 You can use any of several outbound web services to integrate with ServiceNow applications, including REST and SOAP. 

 Outbound REST web service 

 ServiceNow outbound REST functionality allows you to retrieve, create, update, or delete data on a web services server that supports the REST architecture. 

 A REST message can be sent by a REST workflow activity or by using the RESTMessageV2 script API. You can run REST messages from a MID Server which allows the message to communicate with REST providers on an internal network. 

 ServiceNow REST functionality is flexible enough to accommodate many web service APIs. Be sure you are familiar with your web service and the parameters it accepts before attempting to define a REST message in ServiceNow. 

 REST message elements 

 An outbound REST message is composed of several elements, such as the endpoint and HTTP methods. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 431 


 A REST message contains the following elements: 

 Elements 

 Element Description 

 Endpoint The endpoint is the URL of the data to be retrieved, updated, or deleted. Every REST message must specify an endpoint. 

 Headers HTTP headers in REST messages contain information about the request, such as the desired response format. A REST message may specify any number of headers. 

 Authentication settings 

 Authentication settings include which type of authentication to use, such as basic auth or OAuth, as well as the credentials to use. 

 HTTP methods 

 HTTP methods, such as GET, POST, or DELETE interact with the data at the endpoint. 

 You can optionally override the parent REST message configuration in each HTTP method such as by specifying a different endpoint, authentication credentials, or headers. 

 HTTP methods that send content, such as POST, include a message body detailing this content. 

 A REST message may specify multiple HTTP methods. When sending a REST message, such as through a workflow activity or script, you must specify which HTTP method to use. 

 Create a REST message 

 Send requests to a REST web service endpoint by creating a REST message record. 

###### Before you begin 

 Role required: web_service_admin 

###### Procedure 

**1.** Navigate to **All** > **System Web Services** > **REST Message**. 

**2.** Click **New**. 

**3.** Complete the following fields: 

 REST Message form 

 Field Description 

 Name Enter a descriptive name for this message. 

 Endpoint Enter the endpoint that this REST message is sent to. The endpoint value 

###### may include variables using the format ${variable}. 

 Authentication type 

 Select the type of authentication to use, if any, and the profile record that contains the user credentials. 

 Outbound REST supports basic authentication and OAuth 2.0. Outbound REST supports mutual authentication with basic authentication only. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 432 


 Field Description 

 Authentication configured here is inherited by the associated HTTP methods. You can configure authentication for each method which overrides any authentication setting at the message level. 

 HTTP Headers Double-click a row in the HTTP Headers embedded list to define the header Name and Value. 

 The web service provider determines which headers are supported or required. 

**4.** Click **Submit**. 

 After creating the REST message, a GET HTTP method is created automatically using the values from the REST message record. 

###### What to do next 

 Create or edit HTTP methods and run a request. 

 Define a REST message HTTP method 

 Define an HTTP method such as GET or POST to send a request to a web service provider. 

###### Before you begin 

 Role required: web_service_admin 

###### About this task 

 When you create a REST message record, several default HTTP methods are automatically created using settings inherited from the REST message record, such as the Endpoint. Subsequent changes to the REST message record are not applied to the HTTP methods automatically. You can create additional HTTP methods or modify the default HTTP methods to implement new behavior. 

###### Procedure 

**1.** Navigate to **All** > **System Web Services** > **Outbound** > **REST Message**. 

**2.** Select a REST message you want to define an HTTP method for. 

**3.** In the **HTTP Methods** related list, click **New**. 

**4.** Select the **HTTP method** you want to use, such as GET or POST. 

**5.** Enter the **Endpoint** this HTTP method should access. 

###### The endpoint value may include variables using the format ${variable}. 

**6.** Right-click the form header and select **Save**. 

###### What to do next 

 After creating the HTTP method, you can override the security settings from the parent REST message, configure HTTP headers, add variables, or test the method. For PUT, POST, and PATCH methods you can define a message body. 

 Testing REST message HTTP methods 

 Test an HTTP method for an outbound REST message to ensure that the request is valid and the response returns as expected. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 433 


###### Before you begin 

 Role required: web_service_admin or admin 

###### Procedure 

**1.** Navigate to **All** > **System Web Services** > **Outbound** > **REST Message**. 

**2.** Select the REST message with an HTTP method to test. 

**3.** In the HTTP Methods related list, select the HTTP method to test. 

**4.** Under Related Links, select **Test**. 

 If the HTTP method includes variables, the Test value for each variable in the Variable Substitutions related list is used when testing the method. 

 Each test run displays the response status, such as 200 for a successful GET request, the full endpoint URL, any parameters passed in the request, and the response body. 

##### Note: Fields on the Test Runs form are for information only; changes to these fields 

 do not apply to the REST message or HTTP method. Do not modify these values when testing different REST message configurations. Instead, update the REST message or HTTP method, then run a new test. 

###### Result 

 Completed test runs for an HTTP method appear in the Test Runs related list. If there was an error during the request, the Error Code and Error Message fields appear. 

 Define a REST message HTTP header 

 Define an HTTP header for a REST message or HTTP method to send that header with REST requests. 

###### Before you begin 

 Role required: web_service_admin 

###### About this task 

 You can specify an HTTP header for a REST message, or for an HTTP method. Headers defined for a REST message apply to all HTTP methods for that REST message. If you specify the same header for both a REST message and a child HTTP method, the value defined for the HTTP method overrides the value from the parent REST message. 

###### Procedure 

**1.** Navigate to **All** > **System Web Services** > **REST Message**. 

**2.** Select a REST message. 

**3. Optional:** To specify a header for an HTTP method instead of the REST message, in the **HTTP**     **Method** related list, select an HTTP method. 

**4.** Select the **HTTP Request** tab. 

**5.** In the **HTTP Headers** embedded list, click **Insert a new row**. 

**6.** Enter the name of the header, such as Content-Type or Accept. 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 434 


##### Note: 

 ◦ Multipart Content-Type is not supported in RestMessage. You can use REST step instead. 

 ◦ For other supported headers, it depends on the REST web service provider that you are connecting. Refer to the documentation of your web service provider to identify which headers are valid or required. 

**7.** Click on the **Value** field for the new row and enter the value you want to assign this header.     You can use a variable in the format ${variable} instead of a static value. You can assign a value     to the variable when sending a REST request. 

**8.** Click **Update**. 

 Sending outbound REST messages through a MID Server 

 You can configure a REST message HTTP method to be sent through a MID Server. 

 By using a MID Server, the request can reach an endpoint that is behind a firewall or within a private network. 

 To configure an HTTP method to use a MID Server, select a MID Server in the Use MID Server field on the HTTP Method form. The instance must have an active MID Server to use this functionality. 

 Using special characters in URIs 

 A REST function URI or function variable may use special characters, such as pipe (|) characters. 

 When using these characters in a REST message, use URL encoding to escape these characters. 

###### For example, to use a parameter value of user|title, enter user%7Ctitle. Entering 

 special characters directly may cause the REST message to fail and display the response Invalid uri <URI>: Invalid query. 

 Outbound REST authentication 

 Outbound REST messages support multiple types of authentication. 

 Different web service providers may require a specific type of authentication. Outbound REST supports the following authentication formats. 

**-** Basic authentication using a username and password 

**-** OAuth 2.0 using an OAuth provider and profile 

**-** Mutual authentication using protocol profiles 

##### Overriding REST authentication 

 You can define authentication for a REST message, or individually for each HTTP method. HTTP methods inherit authentication from their parent REST message record when the HTTP method Authentication type is Inherit from parent , which is the default value. 

 You can disable authentication for a specific HTTP method by setting the Authentication type field to No authentication , or specify authentication that is different from the parent REST message by selecting basic auth or OAuth. 

##### Authentication requirements 

 Authentication requirement for REST Outbound are as follows: 

© 2025 ServiceNow, Inc. All rights reserved. ServiceNow, the ServiceNow logo, Now, and other ServiceNow marks are trademarks and/or registered trademarks of ServiceNow, Inc., in the United States and/or other countries. 435 


**-** Outbound REST supports mutual authentication only when using basic authentication. Mutual     authentication is not available with OAuth 2.0. 

**-** OAuth 2.0 can be used only with messages that are not configured to use a MID Server.     You cannot send OAuth 2.0 authenticated messages through a MID Server. Also, mutual     authentication is not supported with MID Server. 

**-** When scripting new REST messages configured with authentication you must use the     RESTMessageV2 API. The legacy RESTMessage APIs do not support current authentication     formats. 

**-** AWS credentials or any other custom authentication are supported only with the REST step ,     not with the RestMessage API. 

 Configure a REST message with basic auth 

 Configure an outbound REST message to provide basic authentication credentials with each request. 

###### Before you begin 

 Before starting this procedure, ensure there is a REST Message record that you want to configure to use basic auth. 

##### Note: Ensure any scripts that call this REST message use the RESTMessageV2 API. The 

 RESTMessageV2 API is required to send authenticated REST messages via scripts. 

 Role required: web_service_admin 

###### Procedure 

**1.** Navigate to **All** > **System Web Services** > **Outbound** > **REST Message**. 

**2.** Select a REST message record. 

**3.** In the **Authentication type** field, select **Basic**. 

##### Note: The Basic (Simple) choice appears on REST message records configured to use 

 basic authentication prior to the Geneva release. This choice is intended for compatibility with older REST messages and should not be used for REST messages created in the Geneva release or later. 

**4.** In the **Basic auth profile** field, select the basic authentication profile that contains the     credentials you want to send. 

**5.** Click **Submit**. 

###### What to do next 

 Test the REST message to ensure you receive the expected response. You can optionally specify different authentication settings for each HTTP method related to this REST message, overriding the parent REST message settings. 

 Create a basic auth profile
