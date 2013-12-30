---
layout: default
title: How It Works
category: How it works
publish: false
abstract: Explains the architecture and flow of Cloudify 3.0 the DevOps Orchestrator
pageord: 201
--- 

# What is Cloudify?

# What are Cloudify use cases?

# Components and Flow

## Architecture Overview and flow

## REST API & UI
Cloudify is controlled via REST API. The REST API covers all Cloudify functionality. See [Cloudify REST API Documentation](http://www.blabla.org/docs).
You can use the REST API through Cloudify Non-interactive CLI or write your own REST client.

Cloudify commercial edition comes with Web GUI. The Web GUI works vs. the REST API but adds additional value and visibility.

The GUI has the following screens:
* Blueprints screen
* Blueprint Topology Screen
* Deployments screen
* Deployment Topology screen
* Deployment Network Topology screen
* Deployment Events screen
* Deployment Performance Metrics screen


## Workflow Engine
Cloudify uses a Workflow engine to allow for any automation process through built-in and custom workflows.
The Workflow engine is responsible for timing and orchestrating tasks for creating / manipulating the application components. To achieve that the worflow engine interacts with the Blueprint and runtime data to get the properties and plugin information and writes tasks to the task broker.
Cloudify wroflow engine uses workflows written in a mini language called [Radial](http://ruote.rubyforge.org/definitions.html#radial)

## Runtime Model

Cloudify stores the blueprint information and the runtime information in JSON documents. The runtime model includes the following information: //Idan to provide 

## Metrics Database

CLoudify uses [Graphite](http://graphite.readthedocs.org/en/latest/overview.html) to persist and aggregate the application availability and performance metrics.

Cloudify users don't need to access Graphite API directly in order to consume the persisted data. Cloudify exposes all the metreics data through REST API and Web GUI.

Typically, the Graphite server is installed on a dedicated host. [You can configure the location of your graphite server during bootstrap](#)

## Policy Engine

Cloudify offers a policy engine that runs custom policies in order to make runtime decisions about availability, SLA, etc. For example, during installation, the policy engine consumes streams of events coming from monitoring probes or tools. The policy engine analyze these stream to decide if a specific node is up and running and provides the required functionality. The results of such "stasrt detection" policy are fed into the runtime model.

Cloudify uses [Riemann.IO CEP](http://riemann.io/) as the core of the policy engine component. Cloudify user doesn't need to acces or config Riemann directly. The Policies are registered, activated, deactivated and deleted by the Workflow Engine as part of the orchestration process.

The policies are written in [Clojure](http://clojure.org/). Riemann offers many [built it functions for analyazing monitoring information](http://riemann.io/api.html).
Cloudify offers policy examples for the common use cases.

## Tasks Broker

Cloudify uses [Celery](http://www.celeryproject.org/) with [RabbitMQ](http://www.rabbitmq.com/) message bus to manager task distribution and execution.
Cloudify tasks contain the blueprint information and the runtime information (if applicable) of the relevant node, the plugin (name and URL) that will execute the task and the operation name this plugin need to execute.

Cloudify agents that are based on Celery workers listen to the RabbitMQ queues to obtain tasks they need to execute (see more information below). Once a message arrive, they invoke the task and report back.

## Tasks
Task is a bit overloaded term - it is a step in the Workflow and for Celery it means an extension to execute
In this documentation we refer to the former as a task and to the later as a plugin (at least as the plugin python facade)

## Agents

Cloudify agents are extended celery workers. an agent can be located remote to the Node it manipulates or collocated on the same host. Cloudify have agent(s) on the management VM to perform IaaS tasks (such as host creation) and other remote tasks (such as agent installation using SSH on new application hosts)


## Plugins

# Supported Clouds & Tools
