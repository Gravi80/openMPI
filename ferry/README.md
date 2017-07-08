Followed : http://drydock.readthedocs.io/en/latest/examples/openmpi.html
Using Python3 and pip3

####`Ferry` 
$ sudo pip install ferry --ignore-installed
Ferry is a Python application and runs on your local machine. 
All you have to do to get started is have docker installed and type the following 
**pip install -U ferry**

#####Ferry currently supports:
    1. Hadoop/YARN (version 2.5.1)
    2. Cassandra (version 2.1.0) + Titan (0.3.1)
    3. Spark (version 1.1.0)
    4. GlusterFS (version 3.5)
    5. Open MPI (version 1.8.1)

Ferry helps to develop big data applications without the fuss of setting up the infrastructure.
Develop and test applications locally before being deployed onto an operational cluster.

you can create your big data application using YAML files.
$ ferry start openmpi

export FERRY_DIR="/var/lib/ferry"

docker-machine start default
eval $(docker-machine env default)
bash ferry-dust.sh install


unix:///path/to/socket

apt-get upgrade docker