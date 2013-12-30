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

## Message Broker

## Tasks

## Agents

## Plugins

# Supported Clouds & Tools
