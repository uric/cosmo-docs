---
layout: default
title: User guide Cloudify 3.0
category: Getting Started
publish: false
abstract: Explains how to use Cloudify 3.0 for users in different levels
pageord: 102
--- 
# Introduction
This user guide is written to serve different users with different needs and skillsets
We have created sections designated to early begginers. Other sections address more advnaced users and moving forward all the way to very advanced users that need custom workflows.
Here are the sections with their audience and content description
* Early beginners - You need to master YAML and have scripts that install and start your components. This section will teach you how to write basic blueprints using Openstack VMs and Bash executer plugin to run your scripts
* Average users - You need to master YAML and be able to configure Chef or Puppet in the most basic level. In this section we will teach you how to create any blueprint with built in types and plugins and customize it your needs
* Advanced Users - You will need to master YAML and write python. In this section we will teach you how to add your own types to Cloudify and how to add your custom plugins as implementation logic for these types
* Advanced Developers - In this section you will learn how to master the Radial DSL and how to use it in order to write your own custom workflows

# Early Begginers
**Before you start**
Before you start creating and running your first Cloudify blueprints, we recommend that you read the Quick Startup Guide and try it

## Writing Cloudify Blueprints
Cloudify blueprints are YAML documents that describes the application components and the relationships between them. 
each component is a node under the nodes section of the blueprint. Each node is an instance of a Type. These types asre usually out of the box types but more advanced users can add types. The blueprint needs to be portable between Cloud APIs and between DevOps tools used to install the application. Therefore, the nodes in the blueprint will be instances of abstract types that don't have any implementation details associated with them. These types only declare the basic set of properties. Properties that make sense with any deployement.

Each node might also have relationships declared with other nodes. There are 2 types of abstract relationships:
* `contained_in` relationship meaning that the current node is hosted inside the specified node. This can be a middleware component that is hosted within a VM or application package deployed within the middleware component.
* `connected_to` relationship meaning that the current node is connected to the specified node. For example: an appliaction server might have a connection to the database server. The `connected_to` relationship will be implemented by a concrete relationship type with a plugin that has hooks to invoke in order to configure the source or the target nodes or both in order to enable the relationship.

### Working with type implementations
Type implementations are pieces of YAML that holds the concrete properties for one node in the blueprint. This means that the type implementation is an instance of a concrete type (e.g. `openstack_host` that implements host using a Nova API plugin). The type implementation also decalres a reference to a specific node in the portable blueprint using the `node_reference` attribute.

### Working with Openstack built in types
Cloudify 3.0 includes support for OpenStack main types such as:
* Nova Server (VM)
* Neutron Network
* Neutron Subnet
* Neutron Router
* Neutron Security Group
* Neutron Floating IP
* Neutron Port

In this section we will teach you how to create type implementation for each one of this types. We will also show hot to express the dependencies between them in the portable blueprint and in the type implementation section. Let's get started
#### Working with Openstack Nova Server
