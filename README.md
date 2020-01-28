# Q1
##  Steps to export all the logs related to firewall rules to BigQuery for further analysis. Use console.
*Enable Logging for the firewall rules you want to get logs from.
*Go to the Firewall rules page in the Google Cloud Console.
*Select the firewall rule that you want to update.
*Click Edit.
*For the Logs setting, select On.
*Click Save.

# Create Sinks

a) Go to the StackDriver Logs Viewer page in console.
b) Click on Create Sink, and fill in the Edit Export panel as follows.
c) Set a filter to show all logs related to firewall rules.
```
          resource.type="gce_subnetwork" AND
          log_name="projects/pe-training/logs/compute.googleapis.com%2Ffirewall"
```
d) Set the Sink name.
e) Select Sink Service as Bigquery.
f) In Sink Destination, create a new dataset and give it a suitable name.
g) Click Create Sink
h) Go to Logs Router page to check that the log exporter is created.
