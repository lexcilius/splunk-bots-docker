# Splunk BOTS Docker

## Overview

Splunk released the first three Boss of the SOC (BOTS) datasets several years ago. The idea behind it is a blue team CTF style exercise of doing an investigation in one of the most common and popular SIEM tools - Splunk. Unfortunately, as time has went on, the apps and files necessary to get a reliable and stable Splunk instance up and running to support it has become more and more difficult. This is where the idea for Splunk BOTS Docker comes into play. This is designed to be a nearly self-contained and self-sufficient source for building and utilizing a Splunk BOTS environment all on your own. Below are details about each of the BOTS datasets and how to spin each one up and access it. 

It is worth noting that the container comes with the temporary 30 day license, and if your container lives past that you will need to bring it down and then back up (thus resetting everything). The datasets themselves are not included due to GitHub having a max file size of 100MB and these files are all over that limit. If in the future these files become unavailable, I will find a way to get them from somewhere else.

Lastly, both the BOTSv1 and BOTSv2 environments have a walkthrough app to assist for folks not as familiar with Splunk, and to walk you through the scenarios and your investigation.

Happy Hunting!

## Using the Docker Compose File

Edit the `docker-compose.yml` file and change the value in `SPLUNK_PASSWORD=` to your preferred password the default is `changeme`. The username to login is `admin` for all containers.

Use the `docker-compose up` or `docker compose up` commands to bring up all containers (this may take a while).

To bring up just the BOTSv1 container run `docker-compose up bots1 -d` this brings up the container in a detached mode so you can continue to use your terminal for other things. Then navigate to `http://localhost:8000` on your local machine or on the IP of the system running it and port 8000 to access from another system.

For BOTSv2 run `docker-compose up bots2 -d` This one might take a while as the dataset it has to download is about 3.4GB. Then navigate to `http://localhost:8020` on your local machine or on the IP of the system running it and port 8020 to access from another system. It is worth noting that at this time, there are two apps not included but referenced by the Splunk release - Collected App for Splunk Enterprise and Splunk Add-on for Microsoft IIS. This is due to compatibility issues of the publicly available apps. I will continue to investigate and see if I can find usable versions of these for the future of this project.

For BOTSv3 run `docker-compose up bots3 -d` Then navigate to `http://localhost:8030` on your local machine or on the IP of the system running it and port 8030 to access from another system.

To bring everything back down just run `docker-compose down`

## BOTSv1

Data was created in 2016 based off of realistic data and scenarios developed into a fictional exercise.

Involves two scenarios: an APT and a ransomware event.

Walkthrough App: Investigating with Splunk Workshop

[Local copy of the BOTSv1 dataset details](docs/botsv1.md)

The Splunk App for Stream has been stripped of the binaries for bringing data in. It will work for the purposes of this lab, but not to bring in additional data.

## BOTSv2

Data was created in August 2017 based off of realistic data and scenarios developed into a fictional exercise.

Involves working through an APT investigation.

Walkthrough App: Advanced Hunting APTs with Splunk

[Local copy of the BOTSv2 dataset details](docs/botsv2.md)

## BOTSv3

Data was created in 2018 based off of realistic data and scenarios developed into a fictional exercise.

[Local copy of the BOTSv3 dataset details](docs/botsv3.md)

## CTF Scoreboard

Coming Soon...