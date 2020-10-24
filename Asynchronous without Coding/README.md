Install the StarCluster toolkit (http://star.mit.edu/cluster/) <br />
To configure StarCluster, edit the config file (found in .starcluster folder) as follows:<br />
Add AWS Security Keys in the fields AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY, AWS User Id in the field AWS_USER_ID.<br />
Generate an EC2 Key pair.Add the key location in the StarCluster config file, by defining a "key" in the config file (in KEY_LOCATION). <br />
Define plugin templates in the config file to add MPI and mpi4py to the EC2 cluster machines in the AMI section as follows, <br />
[plugin mpich2]<br />
SETUP_CLASS = starcluster.plugins.mpich2.MPICH2Setup<br />
<br />
[plugin mpi4py]<br />
SETUP_CLASS = starcluster.plugins.pypkginstaller.PyPkgInstaller<br />
PACKAGES = mpi4py<br />
Define volume templates in the config file to attach an EBS volume to an EC2 cluster via NFS-share. (Volume id and mount path) <br />
Define cluster templates in the config file to launch a cluster on EC2. <br />
[cluster mycluster] <br />
KEYNAME = myrandomkey<br />
CLUSTER_SIZE = 21<br />
CLUSTER_USER = sgeadmin<br />
CLUSTER_SHELL = bash<br />
NODE_IMAGE_ID = ami-6b211202<br />
NODE_INSTANCE_TYPE = t2.micro<br />
MASTER_IMAGE_ID = ami-3393a45a<br />
MASTER_INSTANCE_TYPE = m1.small<br />
PLUGINS = mpi4py, mpich2<br />
SPOT_BID = 0.5<br />
SUBNET_ID = subnet-9999a99b9<br />
PUBLIC_IPS = True<br />
VOLUMES = mydata<br />
Start using, <br />
starcluster start -c mycluster mynewcluster <br />
    Clone this repository into the Master node of  the cluster<br />
    Edit the Makefile as needed.<br /> 
        Specify the folder containing data in the field DATA_FOLDER<br />
        Specify the data set path and size in the fields DATASET, N_ROWS and N_COLS, and set IS_REAL to 1.<br />
        Use make arrange_real_data to preprocess the data and break it into partitions.<br />
    Edit the number of iterations, regularization coefficient and learning rate schedules in the file main.py through the variables num_itrs, alpha and learning_rate_schedule etc.<br />
    Now, run: <br />
        make <filename>.
        

