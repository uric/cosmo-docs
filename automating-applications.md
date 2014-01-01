---
layout: default
title: Automating Your Application
category: Automation Orchestration
publish: false
abstract: Explains how to use CLoudify in order to orchestrate and fully automate your applications
pageord: 401
--- 

# Uploading a Blueprint

Uploading a blueprint is the first step for using a blueprint with Cloudify. This can be done using the [REST API upload call](http://www.cloudifysource.org/cosmo-rest-docs/#!/manager-rest-0.1-spec.json/upload_post_1). You can use the equivalent CLI command to achieve the same result.

Once uploaded, you can create deployements and run workflows on the deployements

# Creating a Deployment
A Deployement is an instance of the Blueprint on which you can run workflows, modify the blueprint information and get runtime inforamtion. In other words, a Deployment refelcts the plan and the runtime of a single application environment. To create a new Deployement use the [REST API call for Deployment Creation](http://www.cloudifysource.org/cosmo-rest-docs/#!/manager-rest-0.1-spec.json/createDeployment_post_6). Alternatively use the following CLI command:


# Running a Workflow

Once you have a Delpoyment ready, you can [list the Blueprint available workflows](#missing) and run a workflow. Typically, you will first run the Install workflow (this name stands for the default installation workflow, you can call your custom workflow with any name you want)

# Tracking Workflow progress and result

# Updating Policies: set thresholds, change policy definition, add/remove/suspend/resume policies 

# Implementing Continuous Delivery

# Implementing Infrastructure Updates

# Scaling your applicayion

# Creating and Modifying Blueprints

## Using the CLI for Scaffolding

## Using the GUI

# Implementing Monitoring
