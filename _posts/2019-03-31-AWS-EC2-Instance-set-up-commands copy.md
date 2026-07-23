---
layout: post
published: true
title: "AWS EC2 Instance Setup Commands"
subtitle: "Base package installation for an Amazon Linux 2 instance"
date: '2019-04-01'
tags: [aws, linux, devops]
comments: false
---

A quick reference for bootstrapping a fresh Amazon Linux 2 instance on EC2. The commands below install the base modules I use on a new instance: Java, Python, pip, the AWS CLI, Node.js/npm, and Apache.

## Install Java, Python, and Wget

```bash
sudo yum update
sudo yum install -y java
sudo yum install -y python
sudo yum install -y wget
```

## Set Up pip

```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python get-pip.py
```

## Check the pip Version

```bash
pip -v
pip list
```

## Install the AWS CLI

```bash
sudo pip install awscli
```

## Install Node.js and npm

```bash
sudo yum install -y gcc-c++ make
curl -sL https://rpm.nodesource.com/setup_6.x | sudo -E bash -
sudo yum install nodejs
npm -v
node -v
npm list
```

## Install Apache

```bash
sudo su
yum install -y httpd.x86_64
systemctl start httpd.service
systemctl enable httpd.service
```

With these packages in place, the instance is ready to host applications or serve as a general-purpose build box.
