# Set-up and Configurations

## Installing Required Libraries

To set up the pyhton environment the necessary libraries where installed which include: smtplib, email, msal, pyspark, requests.

**smtplib:** use to send email

**email:** use to structure the email

**msal:** use to obtain access token for microsoft entra ID authentication.

**pyspark:** use to initialize the Spark session

**requests:** use to make HTTP requests to external services (Sends a POST request to trigger dataset refreshes via the Power BI API and can also be use to get access token from Azure).

Anaconda jupyter notebook was used for development and testing before deploying the code to Microsoft fabric workspace.

## Configurating Permissions

Granted permissions is required to access all Power BI REST APIs. Azure service principal is a security identity used on this project to acquire access token to access Power BI Workspace and dataset APIs,
because its a good choice for production and supports the security rule of least priviledges. The Azure service principal do not need a Power BI pro license. But, the Power BI tenant admin must enable
the use of service principals and register a service principal security group and moreso, should have a Power BI Pro license.

**Azure Portal Configurations:** To register a service principal get the relevant credentials:
- Create a new security group in Azure portal under the groups in manage and add member(s).
- Register an App in Azure portal under App registrations, then copy the **application ID** which is the **client ID** and the Directory(tenant) ID which is the **tenant ID**.(The App will use the service principal to acquire an access token
- Create a client secret under the certificates and secrets, click add, then copy the **key value** which is the **client secret**
- Add the App to the security group you created ealier(by going back to groups, click on all groups, then select the group, under total member, click view members, then click add members, select the App to add to the security group)
The App users identity is used to access and query Power BI datasets.

**Power BI Services Configuations:** To allow service principal to use Power BI APIs and get workspace and dataset IDs:
- From the admin portal of power BI service in tenant settings under the developer settings enable the settings to allow service principals to use Power BI APIs and specify the App security group you created in Azure portal to assign settings and apply.
- Goto the workspace carrying the dataset to configure access properties: click the access buttons and search for the App you created in Azure portal, add and assign App permission(member) to the workspace to effectively grant permission to access API
  of the workspace with the dataset.
- Copy the workspace ID: Your workspace ID is the code in between the "groups/" and "/list?" of the URL of your workspace page(example groups/****workspaceID****/list?)
- Click on the dataset and copy the dataset ID: Your dataset ID is the code in between the "dataset/" and "/details?"(example groups/**** workspaceID **** /dataset/ ****datasetID****/details?)

**Email Notifications Configurations:** To configure SMTP email settings and define a function that sends customized notications with detailed error handling:
- SMTP email settings parameters: smtp_server, smtp_port, smtp_user(sender email address), smtp_password, and recipient_email

Your smtp_server and smpt_port choice is defined by the sender email service provider. The smtp_server and port used in the notebook is for gmail users. If, you are using a different email service provider like outlook you will have to replace the smtp_server and smtp_port for that of outlook. For gmail users smtp_password is not your email login password. Google security requires you to generate app password(google "how to get google application password" to get the detailed steps.(The procedure is under ther security settings of your google account). 

- Define python functions that print and send the notification respectively, when the code execution result is either sent email successfully, failed to send email, sucessfully triggered dataset refreshes, failed to trigger refresh, failed to obtain access token, failed to trigger dataset refresh, or an error occurred while refreshing the dataset.

