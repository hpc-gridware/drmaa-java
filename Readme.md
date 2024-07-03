# Cluster Scheduler DRMAA Java API

The DRMAA Java is a wrapper for around the [Cluster Scheduler](https://github.com/hpc-gridware/clusterscheduler)
DRMAA version 1 C/C++ API.
It uses JNI to access the libdrmaa shared library.

It comes with howtos (same logic as the DRMAA C howtos but in Java) and Javadoc documentation.
A comprehensive testsuite can be run from within the Cluster Scheduler testsuite.

## Prerequisits

Cluster Scheduler DRMAA Java requires the following Software for Building
* Java JDK >= 1.8
* Maven
* A Cluster Scheduler installation including the architecture specific drmaa shared library (usually libdrmaa.so)

## Build / Package

Build the jdrmaa jar file with Maven and copy it to the Cluster Scheduler installation:
```Shell
mvn -Dmaven.test.skip package
cp target jdrmaa-1.0.jar $SGE_ROOT/lib
```

## Basic Test

A basic DRMAA Java example application `DrmaaExample` (`src/main/java/DrmaaExample.java`) is part of the DRMAA Java jar file.
In order to run it you need a Cluster Scheduler installation, the host running the example
must be submit host.

The example application submits a number of array jobs and sequential jobs and waits
for them get scheduled and to finish.

```Shell
source $SGE_ROOT/$SGE_CELL/common/settings.sh
java -cp target/jdrmaa-1.0.jar DrmaaExample $SGE_ROOT/examples/jobs/sleeper.sh
```

## Running the Test Suite

Testing the Cluster Scheduler DRMAA Java API requires and is called from
the Cluster Scheduler testsuite.
The testsuite will be open sourced in the near future.

## License

The original files contributed by Sun Microsystems are licensed under

- [Sun Industry Standards Source License v1.2](https://github.com/hpc-gridware/drmaa-java/blob/master/License_SISSL_v1-2.txt)

Newer contributions from HPC-Gridware GmbH (and others like Univa Inc. or individual contributors) are licensed under

- [Apache License v2.0](https://github.com/hpc-gridware/drmaa-java/blob/master/License_APACHE_v2-0.txt)


