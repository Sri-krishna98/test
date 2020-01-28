# Q1

##  Steps to export all the logs related to firewall rules to BigQuery for further analysis. Use console.
* Enable Logging for the firewall rules you want to get logs from.
* Go to the Firewall rules page in the Google Cloud Console.
* Select the firewall rule that you want to update.
* Click Edit.
* For the Logs setting, select On.
* Click Save.

## Create Sinks

* Go to the StackDriver Logs Viewer page in console.
* Click on Create Sink, and fill in the Edit Export panel as follows.
* Set a filter to show all logs related to firewall rules.
```
          resource.type="gce_subnetwork" AND
          log_name="projects/pe-training/logs/compute.googleapis.com%2Ffirewall"
```
* Set the Sink name.
* Select Sink Service as Bigquery.
* In Sink Destination, create a new dataset and give it a suitable name.
* Click Create Sink
* Go to Logs Router page to check that the log exporter is created.
