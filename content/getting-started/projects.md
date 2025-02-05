---
title: Projects
weight: 25
---
___
On this page, you can find an explanation of how to create a new Project, and how to manage them in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Projects page](#projects-page)
  - [Create Project](#create-project)
  - [Project Overview Page](#project-overview-page)
  - [Set Budget Limit](#set-budget-limit)
  - [Edit Project](#edit-project)
  - [Delete Project](#delete-project)
  - [Add users to Project](#add-users-to-project)

## Projects page

{{% notice note %}}
To see information about Projects of the Organization and to manage them, you can only if your User Role in this Organization is an *Administrator* or *Owner*. 
{{% /notice %}}

To see information about created Projects in the Organization or create more Projects in it, go to the *Organizations page* and click on the *Name* of the appropriate Organization:

![](../../assets/images/organizations/7.png?width=50pc&classes=border,shadow)  

This action will open additional sections on the *side-bar menu* and redirect you to the *Projects page*, where you can find all created Projects, related to the selected Organization with the *Create button, Search bar* and *Actions icon*, which opens a list of available management actions for the selected Project:  
- *Edit* - by selecting this option, you can change the Project name;
- *Delete* - this option is for Project removing.

Additionally, from this page, you can navigate to the overview page of each created Project by clicking on its **name**. There, you will find resource utilization graphs, quota details, and billing information for essential resources such as virtual machines, volumes, databases, and object storage. More information about the *Project overview page* will be provided in the following sections.   
![](../../assets/images/projects/2.png?width=50pc&classes=border,shadow) 

## Create Project

To create a new Project, do the following:
- go to the *Projects page* and click on the *CREATE PROJECT* icon in the upper left corner; 
- fill in the form on the next opened *Create Project window* and click on the CREATE icon: 
  - **Name**: set a name for the Project;
  - **Region**: specify, which region this Project will belong to. All other cloud resources, that will be created in this Project, will belong to this region too.

![](../../assets/images/projects/4.png?width=35pc&classes=border,shadow) 

After these steps, the newly created Project will be added to the *Projects page* and you can navigate to the *Project overview page* by clicking on its **name**:
![](../../assets/images/projects/5.png?width=45pc&classes=border,shadow) 

{{% notice note %}}
All subsequent services provided by the Cloud Console within the one Project, will be created in the corresponding Region, in which this Project was created.
{{% /notice %}}

## Project Overview Page
To open the *Project overview page*, click on the **Name** of the appropriate Project on the *Projects page*:
![](../../assets/images/projects/5.png?width=45pc&classes=border,shadow) 

This action will redirect you to the *Project overview page*, where you can find:   
- project **details area** with actual information about it (id, region):  
![](../../assets/images/projects/7.png?width=30pc&classes=border,shadow)   

- resource **utilization graphs** with its quota details:  
![](../../assets/images/projects/14.png?width=50pc&classes=border,shadow) 

- project **billing information** for essential resources such as virtual machines, volumes, databases, and object storage. 
Access to this section is granted only to Administrators or Owners (project members cannot view billing information):  
![](../../assets/images/projects/12.png?width=50pc&classes=border,shadow) 

## Set Budget Limit

In Cloud Console you can configure a **monthly budget tracker** for your Project to monitor and control cloud resource consumption. Once the budget reaches 80% of the set limit, the subscribed Administrators of your Organization will receive daily email notifications informing them that the budget is nearly exhausted.

{{% notice note %}}
Only Administrators or Owners can configure the monthly budget tracker (project members do not have access to billing information).
{{% /notice %}}

To set a budget limit, follow these steps:

- navigate to the **billing information** section on the *Project overview page* and click the **Set Budget Threshold** button:  
![](../../assets/images/projects/13.png?width=50pc&classes=border,shadow) 
- on the next opened *Set Budget Threshold* window - enter the budget limit amount, select subscribers who will receive budget alerts (from the list of Organization Administrators and the Owner) and click on the SET button:  
![](../../assets/images/projects/15.png?width=35pc&classes=border,shadow) 

Once the budget limit is set, a **Budget Tracker** will be displayed on the page, allowing Administrators to monitor the project's monthly consumption in real time.
![](../../assets/images/projects/16.png?width=50pc&classes=border,shadow) 

Additionally, if the budget limit is configured, when 80% of the budget is reached, subscribed Administrators of the Organization will receive daily email alerts, notifying them that the budget is close to being exceeded.

If you wish to disable the budget limit, set the amount to 0.

## Edit Project 
To edit the Project, do the following:
- identify the Project, that you want to edit on the *Projects page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Project Name on the next opened *Edit Project window*, and click on the SAVE icon.

After these steps, the selected Project will be updated.

Also, you can edit the Project from the *Project overview page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/projects/10.png?width=25pc&classes=border,shadow)

## Delete Project 

{{% notice note %}}
Deleting a Project will permanently erase all related resources, including virtual machines, Kubernetes clusters, volumes, and other components, with no option for recovery.
{{% /notice %}}

To delete the Project, do the following:
- identify this unnecessary Project on the *Projects page*;
- click on the **Actions** icon  and select the **Delete** in the list of available options;
- confirm the Project deletion on the next opened *Confirmation window*.

After these steps, the selected Project will be deleted.

Also, you can delete the Project from the *Project overview page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/projects/11.png?width=25pc&classes=border,shadow)

## Add users to Project

To add Users to the Project, you need to create a Group, in which you can create a list of Projects and a corresponding list of Users, who will be added to this Project as *Members*.

For more details, please, see - [Groups](https://docs.ventuscloud.eu/identity-management/groups/)

{{% notice note %}}
Added Members to the Group will have access to Projects from this Group and, accordingly, to all resources in this Project, but will not be able to see information about each other and manage the Groups and Administrators of the Organization that owns this Project or add additional Projects to this Organization.
{{% /notice %}}
