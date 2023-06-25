# Configuring Projects

## Create a project

!!! Note

    * To create a project you must have at least one department configured. For more information, see [Configure a department](department-setup.md#creating-and-managing-departments).
    * To be able to create or edit Projects, you must have *Editor* access. See the [Users](admin-ui-users.md) documentation.

To create a project:

1. Login to the Run:ai interface and press **Projects**.
2. Press *+ New Project*.
3. In the *Departments* pane, select a department from the dropdown.

    !!! Note
        You must select a department from the dropdown list to create a project.

4. Enter a project name. By default, the namespace is created from the name of the project. To change the namespace to an exisitng one, press the *Namespace* dropdown, then select *Enter existing namespace from ther cluster*, and type it in.
5. In the *Access control* pane, press *+ User type*, then choose either *Users* or *Applications*.

    * *Users*&mdash;use the dropdown to select users that are defined in the system. Select as many users as needed.
    * *Applications*&mdash;use the dropdown to select from a list of applications in the system. Select as many applications as needed. 

6. In the *Quota management* pane, configure the behavior of the node pools:

    * *Order of priority*&mdash;the priority the node pool will receive when trying to schedule workloads. Choose `none`, `1`, `2`, or `3` from the dropdown menu. For more information, see [Node pool priority](../../Researcher/scheduling/using-node-pools.md#multiple-node-pools-selection).
    * *GPUs*&mdash;the number of GPUs in the node pool. Press the *GPUs* button and in the popup window, enter the nuber of GPUs you think you need, then press *Apply* to save.
    * *CPUs(Cores)*&mdash;the number of CPU cores in the node pool. Press the *CPUs* button and in the popup window, enter the nuber of CPUs you think you need, then press *Apply* to save.
    * *CPU Memory*&mdash;the amount of memory the CPUs will be allocated. Press the *CPU Memory* button and in the popup window, enter the amount of memory in MB you think you need, then press *Apply* to save.
    * Over quota priority&mdash;the priority for the specific node pool to receive over quota allocations. Choose `None`, `Low`, `Medium`, or `High` from the dropdown menu.

7. (Optional) In the *Scheduling rules* pane, use the dropdown arrow to open the pane. Press on the *+ Rule* button to add a new rule to the project. Add one (or more) of the following rule types:

    * *Idle GPU timeout*&mdash;controls the amount of time that GPUs which are idle will be remain assigned to the project. From the dropdown choose a workload type, then enter the number of days, hours, and minutes before the GPUs are reassigned. You can add multiple rules by pressing on the *+ Idle GPU Timeout*.
    * *Workspace duration*&mdash;limit the length of time a workspace will run for. Enter the number of days, hours, and minutes before the workspace is terminated. You can add multiple rules by pressing on the *+ Rukle*.
    * *Training duration*&mdash;limit the length of time training workloads will run for. Enter the number of days, hours, and minutes before the workspace is terminated. You can add multiple rules by pressing on the *+ Rule*.
    * *Node type (Affinity)*&mdash;limits workloads to run on specific node types. From the dropdown choose a workload type, and then enter a node typoe. You can add multiple rules by pressing on the *+ Node type*.

8. When you have finished the configuration, press *Create project*.

## Managing projects

After you have created a project, it will appear in the list of projects.

To change a project's configuration:

1. Select the project from the list of projects. You can select only one project at as time.
2. Press the *Edit* button.
3. Select a department from the dropdown list.
    !!! Note
        You can't change or edit the name of the project.
4. Using the dropdown, add users or applications. To remove users or applications, press the *x* next to the email or application.
5. In *Quota management* pane change:
    * *Order of priority*&mdash;the priority the node pool will receive when trying to schedule workloads. Choose `none`, `1`, `2`, or `3` from the dropdown menu. For more information, see [Node pool priority](../../Researcher/scheduling/using-node-pools.md#multiple-node-pools-selection).
    * *GPUs*&mdash;the number of GPUs in the node pool. Press the *GPUs* button and in the popup window, enter the nuber of GPUs you think you need, then press *Apply* to save.
    * *CPUs(Cores)*&mdash;the number of CPU cores in the node pool. Press the *CPUs* button and in the popup window, enter the nuber of CPUs you think you need, then press *Apply* to save.
    * *CPU Memory*&mdash;the amount of memory the CPUs will be allocated. Press the *CPU Memory* button and in the popup window, enter the amount of memory in MB you think you need, then press *Apply* to save.
    * Over quota priority&mdash;the priority for the specific node pool to receive over quota allocations. Choose `None`, `Low`, `Medium`, or `High` from the dropdown menu.
6. In te *Sceduling rules* pane you can choose to edit any of the folloing rules:
