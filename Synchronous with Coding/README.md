Launch an EC2 cluster using StarCluster.
    Clone this repository into the Master node of  the cluster
    Edit the Makefile as needed. 
        Specify the folder containing data in the field DATA_FOLDER
        Specify the data set path and size in the fields DATASET, N_ROWS and N_COLS, and set IS_REAL to 1.
        Use make arrange_real_data to preprocess the data and break it into partitions.
        Specify the total number of workers and the number of stragglers in the fields N_PROCS and N_STRAGGLERS, respectively.
        When using partial coding schemes, specify the no. of partitions each worker processes in N_PARTITIONS, and also set PARTIAL_CODED to 1
    Edit the number of iterations, regularization coefficient and learning rate schedules in the file main.py through the variables num_itrs, alpha and learning_rate_schedule etc.
    Now, run (accelerated) gradient descent for various schemes as follows:
        make naive for the Naive (uncoded) scheme
        make avoidstragg for the Ignoring Stragglers scheme
        make cyccoded for the Cyclic Repetition scheme
        make repcoded for the Fractional Repetition scheme
        make partialcyccoded for the Partial Cyclic Repetition scheme
        make partialrepcoded for the Partial Fractional Repetition scheme
