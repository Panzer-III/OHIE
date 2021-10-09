# OHIE - Blockchain scaling

The repository contains C++ implementation of OHIE. 
The technical aspects of the approach are described in [our paper](https://arxiv.org/pdf/1811.12628.pdf). 

## What's New
The code here is tested in Ubuntu 20.04 with Boost version 1.67 and Openssl version 1.1.1f. Take care when install these libararies.

Makefile has been changed a lot, a seperated complier and link is nessary or to get multi-define error which hard to deal with. A clean and delete target is made for better use.

`quicktest.sh` is not recommanded, a restart of it can't kill the one is running and leaves a lot of processing in `ps` list.

The Following is the origin README, That's all and Good Luck.

## Dependencies

The code has been tested on Ubuntu 16.04 with Boost ASIO library installed:

	sudo apt-get install libboost-all-dev

## Quick Test

1. Compile the code `make` 
2. Run the script `quick_test.sh`

This will run OHIE network of 3 nodes -- their outputs are written in `outputnodeX.txt`. So, while running, for example, check the output with `tail -f outputnode1.txt`. 
At the end, make sure to kill the network, i.e. `fuser -k *`.

## Parameters

There are many parameters that can be configured, starting form the IP address of the nodes, to number of chains, block sizes, mining times, etc: 
- For most widely used parameters, check the file `_configuration`. 
- For a full list of parameters, check `configuration.cpp`. 
- The list of network nodes (ip:port) is defined in a separate file, check `_peers`
- To start a single node use 
```
./Node <portNumber> <file_peers> 
```

## Amazon EC2 Scripts

Large scale experiments (based on the above code) were conducted on Amazon EC2, using the scripts from `amazonEC2` folder. 

**Note:** For each AWS region you want to use, make sure you have the public key written in a file and stored in `keys` folder, and have the correct launching templates. Update `regions.py` to reflect the file paths and the templates. 

