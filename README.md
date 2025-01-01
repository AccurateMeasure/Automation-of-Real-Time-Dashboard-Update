# Automation-of-Real-Time-Dashboard-Update

This project aims to automate the process of refreshing Power BI dashboards through API calls and sending email notifications using Python. 

Refreshing Power BI datasets updates Power BI dashboard connected to the dataset in real time.
The proposed solution integrates with Azure Entra ID and use the msal, smtplib, email, pyspark, requests library, to ensure secure and efficient access to the Power BI REST API and streamline data management. 

This project highlights practical steps to implement in automating power BI dashboards update using python script, secure configuration of power BI API permissions in Azure portal and Power BI services as a power BI global admin to allow access to service principals, respecting the security rule of assigning least priviledges required for thier specified task, set up of python script environment, and alternative server or free task scheduler like Windows task scheduler, cron jobs, jupyter scheduler which are different from cloud services(like Azure, Google, AWS and Snowflake) or power automate that are often not free or reflexible enough to successfully automate Power BI dataset/dashboard refreshes with secure and customized implemented email notifications that handles detailed errors.

## Table of Content

- [Set-Up and Configurations](./SetUp_and_Configurations.md)
- [Deployment](./Deployment.md)
- [Summary](./Summary.md)
- [Appendix (Python Notebook)](./DatasetAutomationNotebook.ipynb)
