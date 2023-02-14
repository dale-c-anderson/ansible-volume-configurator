# ansible-volume-configurator

## What it does

* Reads the EC2 tags associated with each non-root EBS volume attached to the instance
* Creates new file systems (default == `xfs`) for each secondary volume
* Adds each secondary volume to `/etc/fstab` file for permanent use
* Mounts each volume for immediate use


## Requirements

* Your instance must be EC2 running at AWS
* Your EC2 instance(s) must have IAM permissions to be able to read metadata about itself.
* The following tags must be present on the ebs volumes attached to the instance:
  * Name: `FileSystem`, Value: `<desired path for the mounted the file system in the OS>`
  * If you desire a different file system type than `xfs`, you can specify it with the tag `FileSystemType`, Value: `<desired file system type>`


## Tested with

* Amazon Linux 2018
* Amazon Linux 2
* Oracle Linux 7
