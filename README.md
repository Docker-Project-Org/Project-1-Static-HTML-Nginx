Since you're learning Docker as a DevOps Engineer, 
let's do a complete beginner-friendly Docker sample project from scratch. 
We'll create a simple HTML website, package it inside an Nginx Docker container, run it, and access it in the browser.
This is one of the easiest Docker projects and teaches the core concepts you'll use in real DevOps work.


Project Overview

We will create this project.

docker-html-app/

Dockerfile

index.html

The flow will be:

<img width="809" height="383" alt="image" src="https://github.com/user-attachments/assets/473cc9b3-0760-436f-b33b-41ad38384956" />


You'll learn:

Create project files

Write a Dockerfile

Build a Docker image

Run a Docker container

Access the application in a browser

Understand each Docker command

Project Folder Structure:
=========================
<img width="347" height="148" alt="image" src="https://github.com/user-attachments/assets/c4a6c595-d924-4ab1-8ff5-0d9eeba35ce7" />

Understand the Dockerfile:
==========================
This file tells Docker how to build the application.

_**Line 1**_
FROM nginx:alpine

Meaning:
--------

Download the lightweight Nginx image.

alpine is a very small Linux distribution.

Think of this as the base operating system.

_**Line 2**_
COPY index.html /usr/share/nginx/html/index.html

Meaning:
--------

Copy your website into the Nginx web server.

Source:

index.html

Destination:

/usr/share/nginx/html/

Nginx automatically serves files from this folder.


_**Line 3** _
EXPOSE 80

Meaning:
--------

Tell Docker that the application uses port 80.

Important:

EXPOSE is documentation.

The actual browser access happens using docker run -p.


**Build the Docker Image**
Run:

docker build -t my-html-app .

Notice the dot (.).

It means:

Build using the current directory.

Expected output:

Successfully built xxxxxxx
Successfully tagged my-html-app:latest


What Happened?
==============

Docker performed these steps.
<img width="543" height="440" alt="image" src="https://github.com/user-attachments/assets/03899569-b085-4e6d-b50d-4029a12a1932" />


Verify the Image
================

List images.

docker images

<img width="972" height="115" alt="image" src="https://github.com/user-attachments/assets/616d1825-cff3-4bf8-97a2-7c5feb347514" />

Important columns:
<img width="483" height="152" alt="image" src="https://github.com/user-attachments/assets/755c815d-75a6-4ee5-ac9c-9dbfb6efcb3d" />

Run the Container
=================

Run:

docker run -d -p 8080:80 --name html-container my-html-app

Breakdown:

<img width="595" height="225" alt="image" src="https://github.com/user-attachments/assets/e142b4f0-78f8-4666-97ec-fdb03ce6c6a8" />

Port Mapping Explained
======================

This is the most important concept.

<img width="751" height="174" alt="image" src="https://github.com/user-attachments/assets/4e0bb5b5-f30a-47c9-b4f4-2959b589d028" />
Meaning:

Browser uses 8080

Container internally uses 80

Command:

8080:80
Read it as:

My computer's port 8080 goes to the container's port 80.

Verify the Running Container
============================

Check:

docker ps
<img width="965" height="132" alt="image" src="https://github.com/user-attachments/assets/cc02346e-87a2-4cd3-9b9b-73dcc66fa155" />
Important part:

0.0.0.0:8080->80/tcp

This confirms browser access is available.

Access the Application
======================

Open your browser.

Visit:

http://localhost:8080


<img width="1364" height="384" alt="image" src="https://github.com/user-attachments/assets/a3077bf6-3b6a-4d4d-8e00-6c947c490e37" />

Test from Terminal
==================
curl http://localhost:8080

<img width="620" height="254" alt="image" src="https://github.com/user-attachments/assets/57e4acd1-e7b9-49c7-b65c-a8b1ec81371d" />
