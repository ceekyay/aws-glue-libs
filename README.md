# aws-glue-libs

This repository is forked from the official repo: https://github.com/awslabs/aws-glue-libs. The only difference between the 2 repo's is the `setup.py`, which has been added here to help install `awsglue` lib through `pip`.

---


This repository supports python libraries for local development of glue pyspark batch jobs. Glue streaming is not supported with this library.

- [awsglue](awsglue) -- This Python package includes the Python interfaces to the AWS Glue ETL library.

## Running gluepyspark shell, gluesparksubmit and pytest locally

The Glue ETL jars are now available via the maven build system in a s3 backed maven repository. We use the copy-dependencies target in
maven to get all the dependencies needed for glue locally.

Install apache maven from the following location:
https://aws-glue-etl-artifacts.s3.amazonaws.com/glue-common/apache-maven-3.6.0-bin.tar.gz

Install the spark distribution from the following location based on the glue version:
Glue version 0.9: https://aws-glue-etl-artifacts.s3.amazonaws.com/glue-0.9/spark-2.2.1-bin-hadoop2.7.tgz
Glue version 1.0: https://aws-glue-etl-artifacts.s3.amazonaws.com/glue-1.0/spark-2.4.3-bin-hadoop2.8.tgz

Export SPARK_HOME environment variable to extracted location of the
above spark archive.
Glue version 0.9: export SPARK_HOME=/home/$USER/spark-2.2.1-bin-hadoop2.7
Glue version 1.0: export SPARK_HOME=/home/$USER/spark-2.4.3-bin-spark-2.4.3-bin-hadoop2.8

The gluepytest script assumes that the pytest module is installed and available in the PATH

Glue shell: ./bin/gluepyspark
Glue submit: ./bin/gluesparksubmit
pytest: ./bin/gluepytest

## Licensing

The libraries in this repository licensed under the [Amazon Software License](http://aws.amazon.com/asl/) (the "License"). They may not be used except in compliance with the License, a copy of which is included here in the LICENSE file.

---

# Release Notes

## August 27 2021
* The master branch has been modified from representing Glue 0.9 to Glue 3.0, we have also created a glue-0.9 branch to reflect the former state of the master branch with Glue 0.9. To rename your local clone of the older master branch and point to the glue-0.9 branch, you may use the following commands:
```
git branch -m master glue-0.9
git fetch origin
git branch -u origin/glue-0.9 glue-0.9
git remote set-head origin -a
```

