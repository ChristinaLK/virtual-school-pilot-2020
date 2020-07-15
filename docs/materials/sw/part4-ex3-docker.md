---
status: in progress
---

<style type="text/css"> pre em { font-style: normal; background-color: yellow; } pre strong { font-style: normal; font-weight: bold; color: #008; } </style>

Software Exercise 4.3: Using Docker
====================================

In this exercise, you will run the same Python script as the other Python exercises, but using a Docker container.

Setup
-----

For this exercise, you will need to be logged into `learn.chtc.wisc.edu`, not `login04.osgconnect.net`. If you haven't done one of the previous Python exercises, 
make sure to get a copy of the script and recommended commands [here](/materials/sw/part2-ex3-python). 

Submit File Changes
-------------------

1.  Make a copy of your submit file from the [previous Python exercise](/materials/sw/part2-ex3-python) or build from an existing submit file. 
1.  Add the following lines to the submit file or modify existing lines to match the lines below: 

		:::file
		universe = docker
		docker_image = python:3.7.0-stretch

	Here we are requesting HTCondor's Docker universe and using a pre-built python image that, by default, will be pulled from a public website of Docker images called DockerHub.  Behind the scenes, HTCondor will ensure that we run on computers whose operating system can support Docker.

1.  Adjust the executable and arguments lines. The executable can now be the Python script itself, with the appropriate arguments: 

		:::file
		executable = fib.py
		arguments = 90

1.  Finally, we no longer need to transfer a Python tarball (whether source code or pre-built) or our Python script. You can remove both from the `transfer_input_files` line of the submit file if it's already present. 

Python Script
-------------

1.  Open the Python script and add the following line at the top: 

		:::file
		#!/usr/bin/env python3

	This will ensure that the script uses the version of Python that comes in the Docker container.

Once these steps are done, submit the job.

