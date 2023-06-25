---
title: Projects Overview
summary: This article describes the concepts needed for setting up a project.
authors:
    - Jason Novich
date: 2022-June-18
---
# Projects Overview

**Projects** is a tool for Administrators and researchers to control resource allocation, create efficient organizational structures, and help prioritize workloads. When a project is created it is assigned a [department](department-setup.md#departments), a name (a namespace), resource quotas, users (access control), and scheduling rules.

For Administrators, **Projects** provides a clear way of organizing, isolating, and allocating GPU, CPU, and other resources for specific workloads. With granular control over the project resources, Administrators are able to monitor resource allocation, utilization, and workload performance.

For researchers, **Projects** provides granular control over workload resource allocation and prioritization. Researchers can assign a specific node pool or pools for a workload as well as select and adjust the node pool priority. With node affinity Researchers can even limit the workload to a specific node type.

## Department

A project must be associated with a **Department**. A department is a container for one or more projects and has its own resource allocation. For more information, see [Departments](department-setup.md#departments).

!!! Note
    It is recommended that the total amount of resources in projects assigned to a department not exceed the total amount of resources allocated to the department.

## Project name and namespace

The name of a project is the Kubernetes namespace where the project is run. This is the mechanism used for isolating groups of resource and assigning them to the project and workloads within. For more information, see [Kubernetes Namepsaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/){target=_blank}.

## Quota management

Quota management for a Project is configured through node pool resource allocation. The total resources available for the project is the sum of all the node pool quotas. Resources allocated in the project are guaranteed to all of the workloads in the project regardless of the cluster status. Workloads are prioritized based on the node pool priority list and if not specified, the workloads will be scheduled using the default priority list. For more information, see [Node pool priority](../../Researcher/scheduling/using-node-pools.md#multiple-node-pools-selection).

### Over quota

**Over quota** for the project or workload allows the workloads to receive more resources than specified in the quota settings. This allows unused resources to be assigned to the project from other projects and nodes. Workloads can be assigned resources allocated to other projects from the same node pool.

!!! Note
    GPUs that were allocated as **over quota** will be reassigned when needed for other workloads.

 **Over quota** is enabled per node pool and assigned an **over quota priority**. For more information, see [Over quota priority](../../Researcher/scheduling/the-runai-scheduler.md#over-quota-priority).

## Scheduling rules

Scheduling rules provide a means to control the compute resources allocated to a project. Rules are applied based on a duration and utilization of resources. There are four kinds of rules:

### Idle GPU timeout

This rule controls the amount of time that GPUs which are idle will be remain assigned to the project. When the time elapses the GPUs will be reassigned as needed for other projects or for over quota requests. This rule is based on the workload type and is configured in days, hours, and minutes.

### Workspace duration

Setting a workspace duration will limit the length of time a workspace will run for. Workspaces are interactive sessions that typically require human interaction. This rule is used in cases where researchers have left their training sessions open, which leaves idle resources allocated . This rule enables better resource and over quota management. The workspace will stop regardless of the activities currently running and is configured in days, hours, and minutes.

### Training duration

Setting a training duration for a project will limit the length of time training workloads will run for. This enables better resource and over quota management. The training will stop regardless of the activities currently running and is configured in days, hours, and minutes.

### Node type (Affinity)

Node affinity is the ability to assign a Project to run on specific nodes. Machine learning frequently has workloads
that require the use of a CPU but not GPU. Node Affinity ensures workloads that are running receive optimized resources. This means workloads can only use nodes from one of those node affinity groups. A workload that specified which node to use, is bounded to it by the Project. There are a number of reasons to use specific nodes for a Project:

* The project needs specialized hardware.
* The project team is the owner of specific hardware.
* Direct specific workloads to work on hardware that optimized for the workload.

## Working with Projects

To configure your project, see [Configuring Projects](project-setup-ui.md#configuring-projects).
