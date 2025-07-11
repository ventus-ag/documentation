---
title: Transfer Images between Regions
weight: 20
---
___
On this page, we will discuss a workflow to help you to transfer Images between Projects in the different Regions.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Workflow](#workflow)
    - [Prepare custom Image](#prepare-custom-image)
    - [Save custom Image](#save-custom-image)
    - [Upload custom Image](#upload-custom-image)

## Prerequisites
In this article, we will assume that we have already created two Projects, belonging to different Regions, and the following resources within these Projects:

- **Project-1** named *v-dev*, that related to the *Vienna* Region, with the following resources:
  - **CLI User** named *v-CLIuser* and which RC file has already been loaded;  
  - **Ubuntu Virtual Machine** - IP: 88.218.53.162, Name: *test-1*; it was created with an additional firewall, configured to allow connection to this VM remotely via SSH;

- **Project-2** named *sw-dev*, that related to the *Eastern-Switzerland* Region, with the following resources:
  - **CLI User** named *sw-CLIuser* and which RC file has already been loaded;  

For more information on the prerequisites discussed, see the following articles:     
    [Projects](https://docs.ventuscloud.eu/getting-started/projects/)  
    [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/)  
    [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/)          
    [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)  
    [Images](https://docs.ventuscloud.eu/products/images/custom-images/)  
    [Create Image from Snapshot](https://docs.ventuscloud.eu/products/images/image-from-snapshot/).

## Workflow
In this article, we look at a scenario where it is needed to share a custom Image, uploaded to the Project-1 named *v-dev* related to the *Vienna* Region, with the Project-2 named *sw-dev* related to the Eastern-Switzerland Region.
This workflow consists of the next steps:
1. Prepare custom Image in the Project-1
2. Save custom Image on the VM
3. Upload custom Image to the Project-2

Let's take a closer look at each of them.

### Prepare custom Image
You can upload any custom Image that was already saved locally, or create the necessary Image from an Snapshot.

Please choose, what is better for you, and see detailed instructions in the next articles:  
    [Custom Images](https://docs.ventuscloud.eu/products/images/custom-images/#custom-images);  
    [Create Image from Snapshot](https://docs.ventuscloud.eu/products/images/image-from-snapshot/)

### Save custom Image
To save custom Image on the VM do the following:
- connect to the previously created Virtual Machine in the current Project-1 *v-dev*;   
To find detailed instructions, how to connect to the Linux VM, see the article: [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)

- install Openstack client on the current VM;   
To find detailed instructions, how to Install and configure OpenStack CLI, see the article: [Installation OpenStack CLI](https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/)

- use CLI User named *v-CLIuser* created in the Project-1 - place RC File of the created CLI User to your Virtual Machine and execute it starting with dot:  
    `vi v-openrc`    
    `. v-openrc`    
To find detailed instructions, how to load RC Files, see the article: [CLI Users](https://docs.ventuscloud.eu/products/security/cli-users/) 

{{% notice note %}}
Please note, that RC file of the current CLI User has already loaded.   
{{% /notice %}} 

- find the ID of the Image you want to transfer:  
    `openstack image list`  
    
    In our case the output will be next: 

![](../../../assets/images/images/5.png?width=45pc&classes=border,shadow) 
- save the selected Image on your VM:  
    `openstack image save --file <file-name>.raw <image-id>`  

    In our case the command will look like:  
    ```
    ubuntu@vm-1:~$ openstack image save --file image.raw 87a57-...-XXX
    ```

### Upload custom Image
To Upload custom Image to the Project-2 do the following:

* use CLI User named *sw-CLIuser* created in the Project-2 - place RC File of the created CLI User to your Virtual Machine and execute it starting with dot:  
    `vi sw-openrc`    
    `. sw-openrc` 

{{% notice note %}}
Make sure you are logged in to the correct OpenStack platform with your CLI tools
{{% /notice %}} 

* upload your image that you’ve just downloaded using the following command: 
    ```
    openstack image create --container-format bare \
                       --disk-format qcow2 \
                       --file <image_file_name> \
                       --property os_platform='linux' \
                       <image_name>
    ```
    
    In our case the command will look like: 
    ```
    openstack image create --container-format bare \
                       --disk-format qcow2 \
                       --file image.raw \
                       --property os_platform='linux' \
                       image-migrated
    ```
    
* check that the Image is added:  
    `openstack image list`  

    In our case the output will be next:    
![](../../../assets/images/tutorials/22.png?width=45pc&classes=border,shadow) 

After these steps, the newly created Image will be added to the *Images page* of the Project-2 related to the *Eastern-Switzerland* Region and you can use it to create new Virtual Machines within this Region:   
![](../../../assets/images/tutorials/23.png?classes=border,shadow) 
 ![](../../../assets/images/tutorials/24.png?width=30pc&classes=border,shadow) 