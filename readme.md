Utility box hosts:

- stage mongoDB
- production import mongoDB
- elasticsearch monitor
- CI

It is based on ami-7edc8a14.

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
