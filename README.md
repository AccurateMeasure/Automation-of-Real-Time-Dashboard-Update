# Automation-of-Real-Time-Dashboard-Update

This project aims to automate the process of refreshing Power BI datasets through API calls and sending email notifications using Python. Refreshing Power BI datasets updates Power BI dashboard connected to the dataset in real time.
The solution integrates with Azure Entra ID and use the msal, smtplib, email, pyspark, requests library, to ensure secure and efficient access to the Power BI REST API and streamline data management. This project implements practical steps to automate power BI dashboards update using python script, how to configure sercure power BI API permissions in Azure portal and Power BI services as a power BI global admin and allow as access to service principals, respecting the security rule of assigning least priviledges required for thier specified task, setting up the python script environment, and highlight alternative server or free task scheduler like Windows task scheduler, cron jobs, jupyter scheduler different from cloud services(like Azure, Google, AWS and Snowflake) or power automate which are ofen not free to run scheduled task for successful automation of Power BI dataset/dashboard refreshes and secure implemented email notifications.

## Table of Content

- [Set-Up and Configurations](./SetUp_and_Configurations.md)
- [Deployment](./Deployment.md)
- [Summary](./Summary.md)
- [Appendix (Python Notebook)](./DatasetAutomationNotebook.ipynb)
