---
title: Object Storage Clients
weight: 10
---
___
On this page, you can find an explanation of what is Object Storage in the Cloud Console, how to create, delete buckets and instructions for other steps to manage an Object Storage in the Cloud Console using integrated S3 Browser, python API, or other third-party tools.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Use Object Storage with integrated S3-Browser](#use-object-storage-with-integrated-s3-browser)
    - [S3 Buckets page](#s3-buckets-page)
    - [Create bucket](#create-bucket)
    - [Browse folders and files within a bucket.](#browse-folders-and-files-within-a-bucket)
    - [Create folder](#create-folder)
    - [Upload file](#upload-file)
    - [Download file](#download-file)
    - [Delete and multi-delete objects](#delete-and-multi-delete-objects)
    - [Make bucket public](#make-bucket-public)
    - [Get bucket public URL](#get-bucket-public-url)
    - [Get object public URL](#get-object-public-url)
    - [Make bucket private](#make-bucket-private)
    - [Delete bucket](#delete-bucket)
  - [Use Object Storage with Python API](#use-object-storage-with-python-api)
    - [Create connection](#create-connection)
    - [Create bucket](#create-bucket-1)
    - [List buckets](#list-buckets)
    - [Create object](#create-object)
    - [List bucket content](#list-bucket-content)
    - [Change object ACL](#change-object-acl)
    - [Generate object download URL](#generate-object-download-url)
    - [Delete object](#delete-object)
  - [Use Object Storage with third-party tools](#use-object-storage-with-third-party-tools)

## Introduction

The Cloud Console Object Storage makes it possible to store data simply and cost-effectively. It provides a fully distributed, API-accessible storage platform that can be integrated directly into applications or used for backup, archiving, and data retention.

It’s built for scale and optimized for durability, availability, and concurrency across the entire data set. 

An Object Storage API differs from a conventional filesystem: instead of directories and files, you manipulate containers where you store objects. A container can hold millions of objects.

There is no notion of hierarchy with containers: you cannot nest a container within another, however, you can emulate a nested folder structure with a naming convention for your objects.

Before we start to configure and use Object Storage we need to create credentials that include the access key and secret key.   
To find instructions of how to create Object Storage Credentials in the Cloud Console, please, see the article - [Object Storage Credentials](https://docs.ventuscloud.eu/products/storage/object-storage-credentials/)


## Use Object Storage with integrated S3-Browser
In the Cloud Console, you have the ability to use our own integrated S3 browser, which offers essential Object Storage functionality.  
With our S3 browser, you can perform the following actions:
- Browse already created buckets and the files stored within them, even if they were created using different APIs or third-party tools;  
- Create new buckets;  
- Delete buckets;    
- Set a bucket to private or public access;  
- Navigate through folders and files inside a bucket;  
- Create a folder structure inside a bucket;  
- Upload files to a bucket;  
- Download separate files from the buckets;  
- Delete files from a bucket;    
- Obtain public links for buckets, folders, and individual files.   
  
This integrated S3 browser provides an efficient and user-friendly way to manage your Object Storage resources within the Cloud Console.

### S3 Buckets page
To start using integrated S3-Browser select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **S3 Browser* **TAB:**
![](../../../assets/images/vol/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/store/1.png?width=30pc&classes=border,shadow) 

These actions will redirect you to the Object Storage Credentials page and if you have already created Object Storage Credentials you will have available button **Bowse Buckets**.  
Clicking on this button will open the integrated S3-Browser and take you to the *S3 Buckets* page. On this page, you can view all your previously created buckets, create new ones, browse objects inside the buckets, and perform other related actions.
![](../../../assets/images/store/14.png?width=45pc&classes=border,shadow)  
![](../../../assets/images/store/16.png?width=45pc&classes=border,shadow) 

If you haven't created Object Storage Credentials yet, click on the **Create S3 Credentials** button and once you have completed this step, you will be able to use the **Browse Buckets** button.   
To find more information about how to manage Object Storage Credentials, please, see the article - [Object Storage Credentials](https://docs.ventuscloud.eu/products/storage/object-storage-credentials/).   
![](../../../assets/images/store/15.png?width=45pc&classes=border,shadow) 

### Create bucket
To create a new S3 Bucket in the Cloud Console, do the following:

- go to the *S3 Buckets* page and click on the CREATE BUCKET button in the upper left corner;
- specify the Name of the Bucket and click on the CREATE button:  
![](../../../assets/images/store/17.png?width=35pc&classes=border,shadow) 

After these steps the newly created Bucket will be added to the  *S3 Buckets* page with private access, which is set as the default access setting:
![](../../../assets/images/store/18.png?width=45pc&classes=border,shadow) 

### Browse folders and files within a bucket.
To access and navigate through the folders and files inside a bucket, click on the **Name** of the corresponding bucket on the *S3 Buckets* page:  
![](../../../assets/images/store/19.png?width=45pc&classes=border,shadow) 

This action will redirect you to the inside *Bucket* page, where you can find:

- *Bucket Details Area* and *Panel with Quick Actions* - this section displays basic information about the bucket, such as its name and whether it is set as public or private and provides various quick actions, including next options:  
  -  to change the bucket's access settings (make it public or private);  
  -  get the bucket's URL (if it is public);  
  -  delete the bucket;  
  -  perform multi-deletion for selected files/folders.   .    
![](../../../assets/images/store/22.png?width=35pc&classes=border,shadow) 

- *Create Folder Button* and *Upload Files Section* - this section allows you to create a new folder directly within the bucket, providing an efficient way to organize your files and enables you to upload files to the bucket from your local machine, making it easy to add new content to the bucket;    
![](../../../assets/images/store/23.png?width=35pc&classes=border,shadow) 

- *Table of All Folders and Files*, this section presents a comprehensive list of all folders and files stored within the bucket with their **action icon**, that opens a list of available management actions for the selected object:
  - download file (currently you can download only separate files);
  - show object url (available only if object has public visibility);
  - delete object.
![](../../../assets/images/store/20.png?width=45pc&classes=border,shadow) 

To browse inside folders within the bucket, click on the **Name** of the desired folder:  
![](../../../assets/images/store/21.png?width=45pc&classes=border,shadow) 

Inside the folder, you will have access to the same functionality as before, but on a deeper level. This allows you to continue navigating through the nested folder structure, perform actions like creating new folders or uploading files specific to the selected folder, and manage the files and folders within it.

To navigate to the parent level in the folder structure, click on the **../** icon. This action will take you up one level, allowing you to browse the contents of the previous folder in the hierarchy:
![](../../../assets/images/store/25.png?width=45pc&classes=border,shadow)

### Create folder
To create a new Folder inside S3 Bucket in the Cloud Console, do the following:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*
- click on the CREATE FOLDER button in the upper left corner;
- specify the Name of the Folder and click on the CREATE button. 

After these steps the newly created Folder will be added to the Bucket. Inside the folder, you will have access to the same functionality as before, but on a deeper level. This allows you to continue navigating through the nested folder structure, perform actions like creating new folders or uploading files specific to the selected folder, and manage the files and folders within it.

### Upload file
{{% notice note %}}
As of the current limitations, the largest file you can upload via this integrated S3 browser is 5 GB. 
{{% /notice %}}
To upload a File inside S3 Bucket in the Cloud Console, do the following:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page* and click on the SELECT FILE button;  
- on the appeared *File selection dialog* browse your local environment and choose the desired file you wish to upload;  
- after selecting the file you will be able to use UPLOAD FILE button.
Click on it to initiate the upload process, and you will see a loader icon indicating the progress of the upload:

![](../../../assets/images/store/26.png?width=25pc&classes=border,shadow)

{{% notice note %}}
If this is your first time attempting to upload a file to the selected bucket, the system may require you to set up CORS (Cross-Origin Resource Sharing) policies. In this case, a dialog window will appear asking you to grant permissions for console access to the specific bucket. Please click on Grant permissions to enable successful file uploading and proceed with the upload process.
{{% /notice %}}

### Download file
{{% notice note %}}
As of the current limitations, you can only download separate files one by one using the integrated S3 browser. There is no direct option to download entire folders or multiple files at once.
{{% /notice %}}

To download a File from S3 Bucket to your local environment, do the following:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- identify the file, that you want to download, on the *Bucket page*;
- click on the **Actions** icon  and select the **Download** in the list of available options:  
![](../../../assets/images/store/27.png?width=45pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on the DOWNLOAD button. 

After these steps, the downloading process of the selected file will start automatically.

### Delete and multi-delete objects
To delete a object URL from S3 Bucket, do the following:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- identify the file or folder, that you want to delete on the *Bucket page*;
- click on the **Actions** icon and select the **Delete** in the list of available options:
![](../../../assets/images/store/30.png?width=45pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on the DELETE button. 

After these steps, the selected file or folder will be deleted.

Also the integrated S3 browser allows you to perform **multiple deletions** of files and folders using the following steps:
- make checks in the checkboxes of the files or folders that you want to delete;  
- click on the delete icon which will become enabled on the *Panel with Quick Actions* once you have selected at least one object (file or folder):
![](../../../assets/images/store/31.png?width=45pc&classes=border,shadow)

- confirm your action on the next opened *Confirmation window* by clicking on the DELETE button.   

After these steps, the selected objects will be deleted in a few seconds.

### Make bucket public
You can make your bucket public from both the *Buckets page* and the inside of the selected *Bucket page*.

1. To make your bucket public from the *Buckets page*, follow these steps:

- go to the *Buckets page* in the Cloud Console.
- find the bucket you want to make public;  
- click on the **Actions** icon and select the **Make bucket public** in the list of available options:  
![](../../../assets/images/store/32.png?width=45pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on MAKE PUBLIC button.  

1. To make your bucket public from inside the selected *Bucket page*, follow these steps:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- inside the bucket on the *Panel with Quick Actions*, click an option icon that allows you to change the bucket's access permissions:    
![](../../../assets/images/store/33.png?width=35pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on MAKE PUBLIC button.

After these steps your bucket will be publicly available and you can obtain a URL that allows direct access to the entire bucket or to individual objects (files or folders) within it. This URL can be shared with others, and they will be able to access the bucket or objects directly through the provided link without requiring any special authentication or permissions.

{{% warning note %}}
Making a bucket public allows anyone to access its contents without requiring authentication or special permissions. Please be cautious when setting buckets to public, as it may expose sensitive data to the public. Always review and manage access controls carefully to ensure the security of your data.
{{% /notice %}}

### Get bucket public URL
{{% notice note %}}
You can obtain the URL for S3 bucket only if the bucket is publicly available. In such cases, you can generate a URL that allows direct access to the entire bucket or to individual objects (files or folders) through the provided link. However, if the bucket is not publicly accessible, generating a URL will not grant access, and users will require appropriate authentication and authorization to access the bucket.
{{% /notice %}}

You can get your bucket public URL from both the *Buckets page* and the inside of the selected *Bucket page*.

1. To get your bucket public URL from the *Buckets page*, follow these steps:

- go to the *Buckets page* in the Cloud Console.
- find the bucket which public URL you want to get;  
- click on the **Actions** icon and select the **Show URL** in the list of available options:  
![](../../../assets/images/store/34.png?width=35pc&classes=border,shadow)
- the next opened window will provide your *bucket URL* and you can save it by clicking on the COPY TO CLIPBOARD button. 

2. To get your bucket public URL from inside the selected *Bucket page*, follow these steps:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- inside the bucket on the *Panel with Quick Actions*, click an option icon that allows you to see bucket URL (this icon will be available only if your bucket is public):  
![](../../../assets/images/store/35.png?width=35pc&classes=border,shadow)
- the next opened window will provide your *bucket URL* and you can save it by clicking on the COPY TO CLIPBOARD button. 

### Get object public URL
{{% notice note %}}
You can obtain the URL for a folder or file in an S3 bucket only if the object is set as publicly available. In such cases, you can generate a URL that allows direct access to the object through the provided link. However, if the object is not publicly accessible, generating a URL will not grant access, and users will require appropriate authentication and authorization to access the object.
{{% /notice %}}

To get a object URL, do the following:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- identify the file or folder, which URL you want to get on the *Bucket page*;
- click on the **Actions** icon and select the **Show URL** in the list of available options:
![](../../../assets/images/store/29.png?width=45pc&classes=border,shadow)
- the next opened window will provide your *object URL* and you can save it by clicking on the COPY TO CLIPBOARD button. 

### Make bucket private
You can make your bucket private from both the *Buckets page* and the inside of the selected *Bucket page*.

1. To make your bucket private from the *Buckets page*, follow these steps:

- go to the *Buckets page* in the Cloud Console.
- find the bucket you want to make private;  
- click on the **Actions** icon and select the **Make bucket private** in the list of available options:  
![](../../../assets/images/store/36.png?width=35pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on MAKE PRIVATE button.  

2. To make your bucket private from inside the selected *Bucket page*, follow these steps:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- inside the bucket on the *Panel with Quick Actions*, click an option icon that allows you to change the bucket's access permissions:    
![](../../../assets/images/store/37.png?width=35pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on MAKE PRIVATE button.

After these steps, your bucket will not be publicly available. The access permissions will not allow the public to access the bucket or its contents through any direct URL. The objects within the bucket will remain private and can only be accessed by users with appropriate authentication and authorization.

### Delete bucket
{{% notice note %}}
To avoid any potential data loss during the deletion process, in the Cloud Console, you can only delete a bucket if it is empty.
{{% /notice %}}

You can delete bucket from both the *Buckets page* and the inside of the selected *Bucket page* but before, please ensure that all the objects (files and folders) inside the bucket have been removed or moved to another location.

1. To delete bucket from the *Buckets page*, follow these steps:

- go to the *Buckets page* in the Cloud Console.
- find the bucket you want to delete;  
- click on the **Actions** icon and select the **Delete** in the list of available options:  
![](../../../assets/images/store/38.png?width=35pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on DELETE button.  

2. To delete bucket from inside the *Bucket page*, follow these steps:

- access the *Bucket page* in the Cloud Console by clicking on the **name** of the bucket from the *Buckets page*.
- inside the bucket on the *Panel with Quick Actions*, click an option icon that allows you to delete bucket:    
![](../../../assets/images/store/39.png?width=35pc&classes=border,shadow)
- confirm your action on the next opened *Confirmation window* by clicking on DELETE button.

After these steps, your bucket will be deleted.




















## Use Object Storage with Python API  
Python support is provided through a fork of the *boto3* library with features to make the most of the Cloud Console Object Storage. 
To start use the Object Storage with the Python API, do the following:
- install boto library by running the command:  
  `apt install python3-pip`   
  `pip install boto`    

{{% notice note %}}
As well as Python API you can select other programming languages for using the Object Storage.
{{% /notice %}}

Now let's take a closer look at each block of code to deal with possible interactions with Object Storage via the Python API:

### Create connection
To create a connection for interacting with the server, use next block of code:  
```python
import boto
import boto.s3.connection
s3_access_key = '**your_access_key**'
s3_secret_key = '**your_secret_key**'
s3_host = '**upper-austria.ventuscloud.eu**
conn = boto.connect_s3(
    aws_access_key_id=s3_access_key,
    aws_secret_access_key=s3_secret_key,
    host=s3_host,
    port=8080,
    calling_format=boto.s3.connection.OrdinaryCallingFormat(),
)
```
Remember to replace the *your_access_key* and *your_secret_key* part with your credential information, and, also, check if the s3_host is correct - if it matches the correct Region.

### Create bucket
To create a new Bucket, use the next block of code:
```python
bucket = conn.create_bucket('**1-bucket-using-python**')
print(f"New bucket created:\n{bucket_name}\t{bucket}")
```

The *1-bucket-using-python* is the name of the new bucket, please enter the desired name for your bucket here.

### List buckets
To get a list of Buckets, that you own, use the next block of code:
```python
for bucket in conn.get_all_buckets():
    print ("{name}\t{created}".format(
            name = bucket.name,
            created = bucket.creation\_date,
    ))
```
It, also, prints out the bucket name and creation date of each bucket.

### Create object
To create a new object in the bucket, use the next block of code:
```python
key = bucket.new_key('hello.txt')
key.set_contents_from_string('Hello World!')

key = bucket.new_key('private_info.txt')
key.set_contents_from_filename('/home/usr/private_data.txt')
```

So, it creates a file 'hello.txt' with the string "Hello World!" and a file 'private_info.txt' with the data from the local file.

### List bucket content
To list a bucket's content, use the next block of code:
```python
for key in bucket.list():
    print "{name}\t{size}\t{modified}".format(
            name = key.name,
            size = key.size,
            modified = key.last_modified,
            )
```

It, also, prints out the object name, size and creation date of each object.

### Change object ACL
>ACL = access control lists

To make objects to be publicly readable or to be private, use the next block of code:
```python
hello_key = bucket.get_key('hello.txt')
hello_key.set_canned_acl('public-read')

private_key = bucket.get_key('private_info.txt')
private_key.set_canned_acl('private')
```

So, this code makes the object 'hello.txt' to be publicly readable, and the object 'private_info.txt' to be private.

### Generate object download URL
**For *publicly readable* objects** we can generate an unsigned download URL.   
To do this, use the next block code:
```python
private_key = bucket.get_key('hello.txt')
hello_url = hello_key.generate_url(0, query_auth=False, force_http=False)
print (hello_url)
```

**For *private* objects** we can generate a signed download URL that will work for the time period (when the time period is up, the URL will stop working).   
To do this, use the next block code:
```python
private_key = bucket.get_key('private_data.txt')
private_url = private_key.generate_url(3600, query_auth=True, force_http=False)
print (private_url)
```

Please, notice here, when a client application accesses buckets, it always operates with the credentials of a particular user. As every user belongs to a particular project, therefore, for using this links you should *add your project ID before your bucket name*, and the working links in both examples will look like this:    
**for publicly readable objects** - "https://upper-austria.ventuscloud.eu:8080/**Your_Project_ID:**new-bucket-using-python/hello.txt";   
**for private objects** - "https://upper-austria.ventuscloud.eu:8080/**Your_Project_ID:**new-bucket-using-python/private_info.txt?Signature=XXX&Expires=1316027075&AWSAccessKeyId=XXX"     

Find your Project ID you can:
* on the *Overview page* in the Cloud Console:
![](../../../assets/images/store/6.png?classes=border,shadow) 

* in the link, when you use Cloud Console;

### Delete object
To delete an object from the bucket, use the next code block:
```python
bucket.delete_key('hello.txt')
```

It deletes a file "hello.txt" from the bucket.

Deleting bucket
To delete a whole bucket use the next code block:
```python
conn.delete_bucket("**1-bucket-using-python"**)
```

It deletes the whole bucket called "1-bucket-using-python".

## Use Object Storage with third-party tools
Another way to utilize the Cloud Console Object Storage and manage data stored in it is by using third-party tools.  
Some of these tools include:

- **S3 Browser** - a freeware Windows client that provides a user-friendly interface for interacting with the Cloud Console Object Storage. You can find more information about it at <https://s3browser.com/>.

- **Cyberduck** - a libre server and cloud storage browser available for both Mac and Windows operating systems. It offers seamless integration with the Cloud Console Object Storage and can be accessed at <https://cyberduck.io/>.

In this section, we will explore how to use the **Windows client S3 Browser** to interact with the Cloud Console Object Storage and manage your data effectively.

To download and install it on your computer, go to the next page <https://s3browser.com/>.  

After installation, you can open on your computer **S3 Browser** and see the next interface of this program:
![](../../../assets/images/store/8.png?classes=border,shadow) 

To start work with the Cloud Console Object Storage, provide your credential information, for this do the following:
- on the main *Navigation Panel* go to *Accounts*, choose **Add new account:**
![](../../../assets/images/store/9.png?classes=border,shadow) 
![](../../../assets/images/store/10.png?classes=border,shadow) 
- fill in fields on the following page as shown below press **Add new account**:
![](../../../assets/images/store/11.png?classes=border,shadow)

After these steps, a connection to the Cloud Console Object Storage through the **S3 browser** is established and you can see all owned buckets and to manage them:
- To **add** a new bucket or **delete** a bucket just by clicking on the one of the buttons:
![](../../../assets/images/store/12.png?classes=border,shadow)
- To make bucket **public** or **private** go to **Permissions tab** and select the necessary option:
![](../../../assets/images/store/13.png?classes=border,shadow)

So, as you can see, using the Cloud Console Object Storage through the **S3 Browser** is as easy as using programming languages.

