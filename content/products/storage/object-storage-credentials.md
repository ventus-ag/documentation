---
title: Object Storage Credentials
weight: 12
---
___
On this page, you can find an explanation of how to create, delete and instructions for other steps to manage an Object Storage Credentials in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Object Storage Credentials page](#object-storage-credentials-page)
  - [Create Object Storage credentials](#create-object-storage-credentials)
  - [Show secret key](#show-secret-key)
  - [Re-generate secret key](#re-generate-secret-key)
  - [Delete Object Storage Credentials](#delete-object-storage-credentials)

## Object Storage Credentials page
To get to the *Object Storage Credentials page*, select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the the **S3 Browser* **TAB:**
![](../../../assets/images/vol/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/store/1.png?width=30pc&classes=border,shadow) 

On this page you can find created Object Storage credentials in the current Project with the *Create or Browse buckets button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Object Storage credentials:
![](../../../assets/images/store/2.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions:
- *Show access secret* - this option is used to find the secret key of the selected Object Storage credentials;
- *Re-generate secret* -  this option is used to re-generate the secret key of the selected Object Storage credentials;
- *Delete storage* - this option is for Object Storage credentials deletion.

{{% notice note %}}
Please be aware that there are current limitations in the Cloud Console. You can create only one set of Object Storage credentials within one project.
{{% /notice %}}

If you haven't created Object Storage Credentials yet, you will find the **Create S3 Credentials** button available in the upper left corner. 
![](../../../assets/images/store/15.png?width=45pc&classes=border,shadow)

Once you have created the credentials, this button will change to the **Browse Buckets** button, which allows you to access and manage your existing buckets using the integrated S3 browser. 
![](../../../assets/images/store/14.png?width=45pc&classes=border,shadow)

Keep in mind that you can only have one set of credentials per project, so ensure you have the necessary credentials before attempting to use the integrated S3 browser for bucket management.

## Create Object Storage credentials
To create a new Object Storage credentials in the Cloud Console, do the following:
- go to the *Object Storage Credentials page* and click on the CREATE S3 CREDENTIALS icon in the upper left corner;  
- confirm your action on the next opened window by clicking on the CREATE icon:

![](../../../assets/images/store/3.png?width=35pc&classes=border,shadow) 

The next opened page will provide your *access secret key* and you can save it by clicking on the COPY TO CLIPBOARD icon. 

After these steps, the newly created Object Storage credentials will be added to the *Object Storage Credentials page*.

{{% notice note %}}
Please be aware that there are current limitations in the Cloud Console. You can create only one set of Object Storage credentials within one project.
{{% /notice %}}

Next steps, how to use Object Storage credentials to connect to the Cloud Object Storage in different ways you can find in the article - [Object Storage Clients](https://docs.ventuscloud.eu/products/storage/object-storage-clients/).

## Show secret key 
To show again secret key of the created Object Storage credentials, do the following:
- on the *Object Storage Credentials page* identify Object Storage credentials from what you want to get secret key;
- click on the **Actions** icon and select the **Show access secret** in the list of available options;
- confirm your action on the next opened window by clicking on the SHOW icon.

After these steps, the next opened page will again provide your *access secret key* and you can save it by clicking on the COPY TO CLIPBOARD.

## Re-generate secret key
To re-generate secret key of the created Object Storage credentials, do the following:
- on the *Object Storage Credentials page* identify Object Storage credentials from what you want to re-generate secret key;
- click on the **Actions** icon and select the **Re-generate secret** in the list of available options;
- confirm your action on the next opened window by clicking on the RE-GENERATE SECRET icon.

After these steps, the next opened page will provide your new *access secret key* and you can save it by clicking on the COPY TO CLIPBOARD icon.

## Delete Object Storage Credentials
To delete the Object Storage credentials, do the following:
- identify this unnecessary Object Storage credentials on the *Object Storage Credentials page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Object Storage credentials deletion on the next opened *Confirmation window*.

After these steps, the selected Object Storage credentials will be deleted.

