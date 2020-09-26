Launch an EC2 cluster using StarCluster.<br />
    Clone this repository into the Master node of  the cluster<br />
    Edit the Makefile as needed.<br /> 
        Specify the folder containing data in the field DATA_FOLDER<br />
        Specify the data set path and size in the fields DATASET, N_ROWS and N_COLS, and set IS_REAL to 1.<br />
        Use make arrange_real_data to preprocess the data and break it into partitions.<br />
        Specify the total number of workers and the number of stragglers in the fields N_PROCS and N_STRAGGLERS, respectively.<br />
        When using partial coding schemes, specify the no. of partitions each worker processes in N_PARTITIONS, and also set PARTIAL_CODED to 1<br />
    Edit the number of iterations, regularization coefficient and learning rate schedules in the file main.py through the variables num_itrs, alpha and learning_rate_schedule etc.<br />
    Now, run gradient descent for various schemes as follows:
        make naive for the Naive (uncoded) scheme<br />
        make avoidstragg for the Ignoring Stragglers scheme<br />
        make cyccoded for the Cyclic Repetition scheme<br />
        make repcoded for the Fractional Repetition scheme<br />
        make partialcyccoded for the Partial Cyclic Repetition scheme<br />
        make partialrepcoded for the Partial Fractional Repetition scheme<br />
