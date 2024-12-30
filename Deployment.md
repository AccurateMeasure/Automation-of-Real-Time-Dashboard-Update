# Deployment

The Jupyter script can be deployed to run on scheduled intervals example every 5mins or at different frequency according to your available resources and as it meets your deployment need in any of the following server environment which includes: 
Windows tasks scheduler, Linux/MacOS cron jobs, Cloud services or jupyter scheduler on jupyterLab. But, I only deployed the script on Azure cloud service(Microsoft fabric notebook) and jupyterLab which I will demonstrate the steps below. 

## Azure Cloud Service(Microsoft fabric notebook)

Microsoft fabric services subscription is needed to deploy and schedule the script to run with Microsoft fabric notebook and the schedule runs even when your system is offline:
- Create a workspace or go to the workspace you have appropriate premissions to create new items, under prepare data select notebook, convert the cell to code cell, if its markdown and choose pyspark python environment
- Copy your code from the testing and development environment and paste on fabric notebook select Run next Edit before View and click on schedule, set scheduled run to on, set repeat and frequency,
choose start date and time, end date and time, your time zone and apply the settings.

## JupyterLab

Jupyter scheduler is free, but you have to install it on your work environment and your server needs to be active. Jupyter scheduler cannot run offline when you do not have internet network or your system is off:
- Open your anaconda prompt, activate your python environment with command "conda activate ***your python env***" and enter.
- Install jupyter scheduler extension if you don't have it already in your environment with the command "pip install jupyter_scheduler", then enter.
- Open jupyterLab from anaconda prompt within the same environment link the extension to your current python environment with the command "jupyter lab", and enter.
- From the jupyterLab server open the script and on the top left of the cell, to the right create a notebook job, you can change the job name if you want, then select run on schedule, under interval select custom schedule and in the cron expression type */5****
for the schedule to run every 5mins or choose the interval best suitable for your need, then choose your time and click on create to finish the setup. 

Microsoft task scheduler and Linux/MacOS cron jobs are also good options to run your script on schedule even when you are offline. What server or task scheduler you choose to use, ensure to end your spark session at the end of the script, else the recurring dataset refresh trigger will fail. Avoid, using exit() or quit() function to end your session, spark.stop() or mssparkutils.session.stop() is recommended especially on production environments.
