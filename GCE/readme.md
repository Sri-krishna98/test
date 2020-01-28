# GCE Questions
## Q1 Create an Instance and resize it

## Code to create the instance
gcloud compute instances create gcp-krishna \
    --machine-type f1-micro \
    --image-family ubuntu-1604-lts \
    --image-project ubuntu-os-cloud \
    --boot-disk-size 10GB  \
    --zone us-east1-b

## Code to resize it
gcloud compute disks resize gcp-krishna --zone=us-east1-b --size 50
