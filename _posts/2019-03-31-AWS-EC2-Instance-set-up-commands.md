---
layout: post
published: true
title: 'AWS EC2 Instance commands '
date: '2019-04-01'
---

After the Amazon EC2 Linux instance is created to install the base modules following commands are run. 	

#### Install Java, Python and Wget 
	
-  ###### sudo yum update
-  ###### sudo yum install java
-  ###### sudo yum install python
-  ###### sudo yum install wget
	
#### get Pip setup 
-  ###### curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
-  ###### sudo python get-pip.py

	
#### Checking the version of PIP
- ###### pip -v
- ###### pip list

#### Install awscli
- ###### sudo pip install awscli

#### Install npm
-  ###### sudo yum install -y gcc-c++ make
-  ###### curl -sL https://rpm.nodesource.com/setup_6.x | sudo -E bash -
-  ###### sudo yum install nodejs
-  ###### npm -v
-  ###### node -v
-  ###### npm list
