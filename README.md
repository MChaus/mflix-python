mflix in Docker
=====

This repository provides Docker utilities for mflix project, which is a drill project for M220P: MongoDB for Python Developers course 
(https://university.mongodb.com/courses/M220P/about).

Setup Environment
-----------------

Open your terminal, go to the Docker folder and build the image:

```console
$ docker image build -t course_m220p .
```
  
After building process finished, create a Docker container with bind mount and exposed ports:

```console
$ cd ..
$ docker create -v $(pwd):/course_m220p/mflix_python -p 5000:5000 -p 8080:8080 --name course_m220p course_m220p  
```

Port 5000 is for the mflix app and port 8080 is for jupyter.
Start container by the following comand:

```console
$ docker container start course_m220p
```

Start bash session to dive into:

```console
$ docker container exec -it course_m220p bash
```
  
For starting jupyter run following comand:

```console
$ jupyter notebook --ip=0.0.0.0 --port=8080
```

Copy one of the URLs provided by jupyter. Ensure that you use correct ip. It 
may differ if you run Docker on virtual machine.

Now you can change the project from your host os and all the changes will be
seen in the container. Everything seems to work, as I passed all labs from the course without
any troubles. My solutions are in the dev_course branch, don't pry into them ;)


Environment Configuration
-------------------------------------------

I used virtualenv for creating isolated environment and oficial mongo image from dockerhub.
Also I updated mflix project, because the version from github is outdated, comparing to one
providied by M220P: MongoDB for Python Developers course.

Also I updated slightly run.py, so it could run from container.