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

**Line 1**
FROM nginx:alpine

Meaning:

Download the lightweight Nginx image.

alpine is a very small Linux distribution.

Think of this as the base operating system.

**Line 2**
COPY index.html /usr/share/nginx/html/index.html

Meaning:

Copy your website into the Nginx web server.

Source:

index.html

Destination:

/usr/share/nginx/html/

Nginx automatically serves files from this folder.


**Line 3**
EXPOSE 80

Meaning:

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

