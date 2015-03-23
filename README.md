# Ansible deployment for JIRA

## 0. Current Stats

[![Build Status](https://travis-ci.org/configuresystems/ansible-jira.svg)](https://travis-ci.org/configuresystems/ansible-jira)

|    Name         |    Description            |
| --------------- | ------------------------- |
| Version         | 1.0                       |
| Updated         | 03.22.2015                |
| Ansible Version | 1.8.4                     |
| Author          | Johnny Martin             |
| Website         | http://configure.systems/ |
| License         | MIT                       |


## 1. QuickStart

```bash
git clone https://github.com/configuresystems/ansible-jira.git roles/ansible-jira
# Create a playbook file to use, there's a sample one in tests/test.yml
# Create a group_vars or update the default values in defaults/main.yml
ansible-playbook -i path/to/inventory ansible-jira.yml
```

    
## Table of contents

- [1. QuickStart](#1-quickstart)
- [2. Overview](#2-overview)
- [3. Requirements](#3-requirements)
  - [3.1 Ubuntu](#31-ubuntu)
  - [3.2 Compile from Source](#32-compile-from-source)
- [4. Usage](#4-usage)
  - [4.1 Playbook Arguments](#41-playbook-arguments)
  - [4.2 Not Currently in Use](#41-not-currently-in-use)
- [5. After Install](#5-after-install)
- [6. Jira Control](#6-jira-control)
  - [6.1 Stop](#61-stop)
  - [6.2 Start](#62-start)
  - [6.3 Restart](#63-restart)


## 2. Overview

An Ansible playbook to automate the installation of Atlassian jira.

It uses the self installer along with the response.varfile to automate
the installation.


## 3. Requirements

Ansible installed on the local machine.

#### 3.1 Ubuntu

```bash
pip install ansible
```

#### 3.2 Compile from Source

```bash
git clone git://github.com/ansible/ansible.git --recursive
cd ./ansible
source ./hacking/env-setup
```

## 4. Usage

1. `git clone http://github.com/configuresystems/ansible-jira`
2. Create a vars file in your group_vars, host_vars, set vars in the Playbook,
   or update the 'defaults/main.yml' file
3. run the Ansible playbook, the fastest way is:

```bash
ansible-playbook ansible-jira.yml
```

### 4.1 Playbook Arguments

- jiraRmi: jira Controller Port
- jiraHttp: Accessible jira Port
- jiraHome: The home dir of jira, not the install dir
- jiraData: Install dir of jira
- jiraExec: Name of the bin autoinstaller
- jiraUrl: Location of where jira is to be downloaded from
- mysqlConnectorJar: In order to use MySQL, a plugin must be added, 
                     this is that file
- mysqlConnectorUrl: Where to download the the connector plugin from
  
### 4.2 Not Currently in use
- mysqlHost: Host of the database to utilize 
- mysqlPort: Database port
- mysqlDatabase: Database Name
- mysqlUser: Datebase User
- mysqlPasswd: Database Passwd


### 5. After install

Visit the jira server via the browser by going to:

http://your.ip.address.yes:{{ jiraHttp }}

Finish up the install process by adding the database info and
product key probvided by Atlassian.

### 6. Jira Control

#### 6.1 Stop

```bash
service jira stop
```

#### 6.2 Start

```bash
service jira start
```

#### 6.3 Restart

```bash
service jira restart
```
