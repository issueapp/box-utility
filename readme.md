Utility box hosts:

- stage mongoDB
- production import mongoDB
- elasticsearch monitor
- CI

It is based on elasticsearch-monitor AMI: ami-7edc8a14.

# Getting Started

    $ vagrant up
    $ vagrant ssh
    > cd /vagrant
    > sudo bin/setup
    > exit
    $ bin/test

# Customization

### Mongo User

    > MONGO_USER=bam MONGO_PASS=bam sudo -E bin/setup
    > exit
    $ MONGO_URL=mongodb://bam:bam@10.11.12.27 bin/test

# Live

    $ ssh user@box
    > curl -fsSL https://raw.githubusercontent.com/issueapp/box-utility/master/bin/mongo | USR=bam PAS=bam sudo -E sh


### Troubleshoot

[add swap](https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04)
    $ ssh user@box
    > curl -fsSL https://raw.githubusercontent.com/issueapp/box-memcached/master/bin/swap | SIZE=2G sudo -E sh

# Opsworks

larger root ebs size

- http://docs.aws.amazon.com/cli/latest/reference/opsworks/create-instance.html
- http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/block-device-mapping-concepts.html


    $ cat config/instance.json
    {
        "InstanceType": "c4.large", 
        "RootDeviceType": "ebs", 
        "BlockDeviceMappings": [
            {
                "DeviceName": "ROOT_DEVICE", 
                "Ebs": {
                    "VolumeSize": 20, 
                    "VolumeType": "gp2", 
                    "DeleteOnTermination": true
                }
            }
        ] 
    }
    $ aws opsworks create-instance --cli-input-json file://./config/instance.json --stack-id <stack-id-number-here> --layer-ids <one-or-more-layer-id-numbers-here>

    $ # or oneliner
    $ aws opsworks create-instance --stack-id <stack-id-number-here> --layer-ids <one-or-more-layer-id-numbers-here> --instance-type <e.g. c4.large> --block-device-mappings '[{"DeviceName":"ROOT_DEVICE","Ebs":{"VolumeType":"gp2","VolumeSize":20}}]'

