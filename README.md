# Hadoop Example

### This is ment as a repository to easily and successfully run an example with Hadoop to better understand it. Below there will be some code that you can copy-paste into your terminal. 

##### This will run through a couple of steps:
#####   1. Install Docker
#####   2. Pull the Hadoop Docker instance
#####   3. Run an example using word count 
#####   4. See the output of the code

# Install Docker
### Linux 
Using this command should install docker on your machine. This is the suggested fastest way to download and install docker

'''
curl -sSL https://get.docker.com/ | sh
'''

# Pull the Hadoop instance
Once we have docker installed we can pull the instance we're gonna use using the command below
''' 
sudo su
docker pull sequenceiq/hadoop-docker:2.7.0
'''

Then once we're done pulling we start the container
'''
docker run -it sequenceiq/hadoop-docker:2.7.0 /etc/bootstrap.sh -bash
'''

We should now be in the docker container. You should see as your $ 'bash-4.1#'.

# Run an example using word count
Once we are in the docker container we can start by running our job using the script below:

'''
cd $HADOOP_PREFIX
bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.0.jar wordcount input output
'''

In order to see the output of our job we run the code below:
'''
bin/hdfs dfs -cat output/*
'''

