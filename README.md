# What is this?
This is a docker system containing containers hosting mongoDBs, aem authors and nginx server (for load balancing)

# Running for first time
This requires adding aem jar file, license file and setting up mongodb

## Copy files
Please copy cq-quickstart-6.5.0.jar and license.properties to aem/files/.

## Spin up mongodb cluster
    docker-compose up mongosetup

## Setting mongo for aem
Spin up only one author instance
    docker-compose up -d aemaut1
This step will take lot of time (probably 10-20 mins depending on your machine)

You can either tail the logs or wait for login screen http://localhost:4501.

In case you run into issue (such as Authentication service may be missing error), stop the aem container, delete its volume (only the aemauth1 volume) and spin it up again. Repeat until you see login screen.


## Spinning up the system
Once the DB is setup for aem, you can jus spin up all the containers using
    docker-compose up -d

You can hit the LB endpoint at http://localhost:4000

>Note:
>The mongosetup container stops after setting up the cluster and this is normal.

# mongo

mongo status:

    mongo docker:27017 --eval 'rs.status();'

