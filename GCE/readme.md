# GCE Questions
# Q1 Create an Instance and resize it

## Code to create the instance

```
gcloud compute instances create gcp-krishna \
    --machine-type f1-micro \
    --image-family ubuntu-1604-lts \
    --image-project ubuntu-os-cloud \
    --boot-disk-size 10GB  \
    --zone us-east1-b
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q1/Q1-2.PNG?raw=true)
## Code to resize it
```
gcloud compute disks resize gcp-krishna --zone=us-east1-b --size 50
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q1/Q1.PNG?raw=true)

# Q2
## Create Instance Template and use the following user data ie bash script to install Apache on startup
```
  #!/bin/bash apt-get update 
  apt-get install -y apache2 
  echo "Hello world from $(hostname)" > /var/www/html/index.html 
  systemctl start apache2 
  systemctl enable apache2
```

## Create an Instance Group with the instance template that was created

![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q2/Q21.PNG?raw=true)

## Attach a load balancer to the instance group with autoscaling enabled.
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q2/Q22.PNG?raw=true)

## Access the http website using external IP address
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q2/Q23.PNG?raw=true)

# Q3
## Perform the following actions on bucket
First two buckets are to be created for further operations
```
# Create a bucket
gsutil mb gs://gcpbktkrishna/

# Create second bucket for later operations
gsutil mb gs://gcpbktkrishna2/

# Create files for transfer operations
echo 'this is the 1st a test file.' > testfile.txt
echo 'this is the 2nd test file' > testfile2.txt
```
## Transfer file from one bucket to another
```
gsutil cp gs://gcpbktkrishna/testfile.txt gs://gcpbktkrishna2/
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q3/Q3a.PNG?raw=true)

## Transfer a local file from PC to the bucket
```
echo 'this is the 1st a test file.' > test1.txt
gsutil cp test1.txt gs://gcpbktkrishna/
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q3/Q3b.PNG?raw=true)

## Download a file from bucket to local
```
gsutil -m cp gs://gcpbktkrishna/test2.txt
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q3/Q3c.PNG?raw=true)
## List all the objects in the bucket
```
gsutil ls -r gs://gcpbktkrishna/**
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q3/Q3d.PNG?raw=true)

## Delete objects in the bucket
```
gsutil rm gs://gcpbktkrishna/**
```
![Image](https://github.com/Sri-krishna98/test/blob/master/GCE/Q3/Q3d.PNG?raw=true)


