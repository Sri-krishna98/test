# Q1 Steps to export all the logs related to firewall rules to BigQuery for further analysis. Use console.

##  Setting up firewall for logging
* Enable Logging for the firewall rules you want to get logs from.
* Go to the Firewall rules page in the Google Cloud Console.
* Select the firewall rule that you want to update.
* Click Edit.
* For the Logs setting, select On.
* Click Save.

## Creating Sinks

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

## Q2 Configure Apache2 HTTP server on a GCE VM instance and setup an email alert notification which triggers when the health check of the instance fails. Use console.

* Installing Stackdriver on the VM Instance
```
curl -sSO https://dl.google.com/cloudagents/install-monitoring-agent.sh
sudo bash install-monitoring-agent.sh
```
* Installing Logging Agent on the VM Instance
```
curl -sSO https://dl.google.com/cloudagents/install-logging-agent.sh
sudo bash install-logging-agent.sh --structured
```

## Create an alert policy using the following rules
* Use CPU Utilization as one metric
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q2/Q2a.PNG?raw=true)
* Use CPU Usage as another metric
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q2/Q2b.PNG?raw=true)
* Alert notification must be set to your email address.
* To increase cpu usage to 100% use this code
```
dd if=/dev/zero of=/dev/null
```
* On doing so an alert notification will be sent to your email address
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q2/Q2c.PNG?raw=true)
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q2/Q2e.PNG?raw=true)
* Setup an Uptime Health check and attach it as the Uptime Metric
* Stop the instance to recieve an Uptime Health Check alert
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q2/Q2d.PNG?raw=true)

# Q3 Create a Cloud Function to convert the pub/sub message to json file and store it in GCS bucket\

## First Create a pub/sub

![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q3/Q3a.PNG?raw=true)

## Then Click on the Trigger Cloud Function
 
## Use the main.py and requirements.txt to create the cloud function using Python Inline Editor
* main.py [Link](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q3/main.py)
* requirements.txt [Link](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q3/requirements.txt)
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q3/Q3d.PNG?raw=true)
 
## Create any random subscriber and publish a message in the json format as shown below
```
{
"name":"test-file",
"content":'{"source": "pub/sub", "destination": "gcs"}'
}
```
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q3/Q3b.PNG?raw=true)
## The Cloud function will be triggered and a json file will be created in the Destination mentioned in the message.
![Image](https://github.com/Sri-krishna98/GCP/blob/master/Cloud%20Function-SD-PubSub/Q3/Q3c.PNG?raw=true)
