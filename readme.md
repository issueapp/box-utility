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
