# Hadoop Example

### This is meant as a repository to easily and successfully run an example with Hadoop to better understand it. Below there will be some code that you can copy-paste into your terminal. 

##### This will run through a couple of steps:
# Table of Contents
1. [Install Docker](#install_docker)
2. [Pull the Hadoop Docker instance](#pull_instance)
3. [Run an example using word count](#run_example)
4. [Example Code](#example_code)

## Install Docker <a name="install_docker"></a>
### Linux 
Using this command should install docker on your machine. This is the suggested fastest way to download and install docker

```bash
sudo su
curl -fsSL get.docker.com -o get-docker.sh
sh get-docker.sh
```

## Pull the Hadoop instance <a name="pull_instance"></a>
Once we have docker installed we can pull the instance we're gonna use using the command below
```bash
sudo su
docker pull sequenceiq/hadoop-docker:2.7.0
```

Then once we're done pulling we start the container
```bash
docker run -it sequenceiq/hadoop-docker:2.7.0 /etc/bootstrap.sh -bash
```

We should now be in the docker container. You should see as your $ 'bash-4.1#'.

## Run an example using word count <a name="run_example"></a>
Once we are in the docker container we can start by running our job using the script below:

```bash
cd $HADOOP_PREFIX
sudo bin/hadoop jar share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.0.jar wordcount input output
```

In order to see the output of our job we run the code below:
```bash
bin/hdfs dfs -cat output/*
```

## Example code <a name="example_code"></a>
The code for the wordcount should be found [here](https://hadoop.apache.org/docs/stable/hadoop-mapreduce-client/hadoop-mapreduce-client-core/MapReduceTutorial.html#Example:_WordCount_v1.0).

## Remove file
If you would like to run it again you will get an error stating that there is a file that already exists in the output directory. Use this command below to remove the file to run it again. 

'''bash
bin/hadoop fs -rm -r -skipTrash /user/root/output/
'''
'''
