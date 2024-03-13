---
title: IaC Terraform
weight: 31
---
___
On this page, you can find essential steps and code for starting with Terraform and Cloud, from installation to advanced deployment scenarios, highlighting the benefits of infrastructure as code (IaC) for simplifying and automating cloud infrastructure management.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Prepare Terraform environment](#prepare-terraform-environment)
  - [Basic virtual machine setup](#basic-virtual-machine-setup)
  - [Complex virtual machine setup](#complex-virtual-machine-setup)
  - [Basic Kubernetes setup](#basic-kubernetes-setup)

## Prerequisites

- **Terraform installation** - https://developer.hashicorp.com/terraform/install
- **Create CLI user** - https://docs.ventuscloud.eu/products/security/cli-users
- **Install CLI client** - https://docs.ventuscloud.eu/tutorials-advanced/installation-openstack-cli/

## Prepare Terraform environment
1. Set Up Your Environment
Once Terraform is installed, create a new directory for your Terraform configurations. This directory will hold all your Terraform files for a specific project:

```bash
mkdir terraform_basic_vm
cd terraform_basic_vm
```
2. Create file provider.tf in terraform_basic_vm folder and add following code:

```tf
terraform {
required_version = ">= 0.14.0"
  required_providers {
    openstack = {
      source  = "terraform-provider-openstack/openstack"
      version = "~> 1.53.0"
    }
  }
}
```

This is a configuration block for Terraform, an infrastructure as code tool used for building, changing, and versioning infrastructure safely and efficiently. We will use it in all our examples.

In this specific block:

- `required_version`: Specifies the minimum version of Terraform required to run this configuration. In this case, it requires version 0.14.0 or newer.

- `required_providers`: Specifies the providers required by this configuration. Providers are plugins that Terraform uses to interact with different infrastructure APIs. In this block:

  - `openstack`: Specifies the provider for OpenStack, a cloud computing platform. It includes:
    - `source`: Specifies where Terraform can find the provider plugin. In this case, it's hosted on the official Terraform registry under the namespace `terraform-provider-openstack/openstack`.
    - `version`: Specifies the version constraint for the provider. In this case, it requires version 1.53.0 or newer, but not version 2.0.0.

Overall, this configuration ensures that when you run Terraform commands against this project, Terraform will check that it's using at least version 0.14.0 and that it has the required OpenStack provider version installed to manage the OpenStack infrastructure.

3. Create file outputs.tf in terraform_basic_vm folder and add following code. We will use it on first and second examples.

```tf
output "instance_ip" {
  value = openstack_compute_instance_v2.example_instance.access_ip_v4
}
```

- `output "instance_ip"`: This line declares an output variable named "instance_ip". Outputs in Terraform allow you to extract and display specific information from your infrastructure after it's been created or modified.

- `value = openstack_compute_instance_v2.example_instance.access_ip_v4`: This line specifies the value of the output variable. It retrieves the IPv4 address (`access_ip_v4`) of an OpenStack compute instance named `example_instance`. The `openstack_compute_instance_v2` is a Terraform resource type that represents an OpenStack compute instance.

Overall, this output configuration retrieves and displays the IPv4 address of an OpenStack compute instance named `example_instance`. After applying the Terraform configuration, you can use the `terraform output` command to view the value of the "instance_ip" output variable.


4. First set the required environment variables for the OpenStack provider by sourcing the credentials file. (see https://docs.ventuscloud.eu/products/security/cli-users) 

```bash
source openrc
```

5. Create a new file named main.tf in terraform_basic_vm folder. This file will contain your Terraform configuration. You can use code from first example.

6. Create id_rsa.pub file and put inside public key (it can be created  in another path, do not forger define path in public_key = file("/path_to_file/id_rsa.pub") )

{{% notice note %}}
Before we start:
The first two examples imply that all 6 steps have been completed; in the third example, you need to skip the third one, since all the necessary information for connecting to the k8s cluster will be saved to a file.
{{% /notice %}}

7. Initialize Terraform
Before applying the configuration, you need to initialize Terraform in your project directory. This step downloads the necessary plugins and initializes your working directory.
```bash
terraform init
```

8. After initializing add code in main.tf and create an execution plan and apply your Terraform configuration.
```bash
terraform plan
```
This command generates an execution plan based on your configuration files. It outlines what actions Terraform will take to achieve the desired state.

9. Next command applies the execution plan generated by terraform plan. Terraform will prompt you to confirm the action. Type yes and press Enter to proceed.
```bash
terraform apply
```
1. Clean Up (Optional)
```bash
terraform destroy
```
{{% /note %}}


## Basic virtual machine setup

1. SSH Key Pair Creation
   - A SSH key pair named "example-keypair" is created using the `openstack_compute_keypair_v2` resource.
   - The public key is fetched from the file "./id_rsa.pub".

2. Security Group Creation
   - A security group named "sec_group" is created using the `openstack_networking_secgroup_v2` resource.
   - This security group will control inbound and outbound traffic for instances associated with it.

3. Ingress Rules Configuration
   - Two ingress rules are added to the "sec_group" security group using `openstack_networking_secgroup_rule_v2` resources:
     - The first rule allows SSH (TCP port 22) traffic from any IP address (0.0.0.0/0).
     - The second rule allows ICMP (ping) traffic from any IP address (0.0.0.0/0).

4. Instance Creation
   - An OpenStack compute instance named "example-instance" is created using the `openstack_compute_instance_v2` resource.
   - The instance is launched from the "ubuntu-server-22.04-LTS-20240110" image and uses the "VC-2" flavor.
   - It is associated with the "public" network.
   - The SSH key pair "example-keypair" and the security group "sec_group" are attached to the instance, allowing SSH access and controlling inbound and outbound traffic.

This code can be used to provision resources on an Ventus cloud, including creating VM instance with SSH access configured via key pairs and security groups. Adjustments can be made to customize the deployment according to specific requirements.

```tf
// Add ssh public key
resource "openstack_compute_keypair_v2" "example_keypair" {
  name = "example-keypair"
  public_key = file("./id_rsa.pub") // or can be public_key =("ssh-rsa AAAAB3.......")
}

//Create security group with name sec_group
resource "openstack_networking_secgroup_v2" "sec_group" {
  name        = "sec_group"
  description = "Master sec group"
}

//Add ingress rule ssh in security group with name sec_group
resource "openstack_networking_secgroup_rule_v2" "allow_ssh" {
  direction         = "ingress"
  ethertype         = "IPv4"
  protocol          = "tcp"
  port_range_min    = 22
  port_range_max    = 22
  remote_ip_prefix  = "0.0.0.0/0" //For more secure add your IP/32
  security_group_id = "${openstack_networking_secgroup_v2.sec_group.id}"
}

//Add ingress rule ICMP all options in security group with name sec_group
resource "openstack_networking_secgroup_rule_v2" "allow_icmp" {
  direction         = "ingress"
  ethertype         = "IPv4"
  protocol          = "icmp"
  remote_ip_prefix  = "0.0.0.0/0" //For more secure add your IP/32
  security_group_id = "${openstack_networking_secgroup_v2.sec_group.id}"
}

//Create instance with name example_instance in public network with ssh key and security group
resource "openstack_compute_instance_v2" "example_instance" {
  name        = "example-instance"
  image_name  = "ubuntu-server-22.04-LTS-20240110"
  flavor_name = "VC-2"
  key_pair    = openstack_compute_keypair_v2.example_keypair.name
  security_groups = [openstack_networking_secgroup_v2.sec_group.name]
  network {
    name = "public"
  }
}
```

## Complex virtual machine setup

1. SSH Key Pair Creation
   - A SSH key pair named "example-keypair" is created using the `openstack_compute_keypair_v2` resource.
   - The public key is fetched from the file "./id_rsa.pub".

2. Security Group Creation
   - A security group named "sec_group" is created using the `openstack_networking_secgroup_v2` resource.
   - This security group will control inbound and outbound traffic for instances associated with it.

3. Ingress Rules Configuration
   - Three ingress rules are added to the "sec_group" security group using `openstack_networking_secgroup_rule_v2` resources:
     - The first rule allows SSH (TCP port 22) traffic from any IP address (0.0.0.0/0).
     - The second rule allows HTTP (TCP port 80) traffic from any IP address (0.0.0.0/0).
     - The third rule allows HTTPS (TCP port 443) traffic from any IP address (0.0.0.0/0).
   - Additionally, an ingress rule allows ICMP (ping) traffic from any IP address (0.0.0.0/0).

4. Instance Creation
   - An OpenStack compute instance named "example-instance" is created using the `openstack_compute_instance_v2` resource.
   - The instance is launched from the "ubuntu-server-22.04-LTS-20240110" image and uses the "VC-2" flavor.
   - It is associated with the "public" network.
   - The SSH key pair "example-keypair" and the security group "sec_group" are attached to the instance, allowing SSH access and controlling inbound and outbound traffic.
   - Cloud-init configuration is provided via the `user_data` attribute, which installs Nginx and enables unattended upgrades.


This code can be used to provision resources in the cloud, including creating VM instance with SSH and Web access configured via key pairs and security groups. Adjustments can be made to customize the deployment according to specific requirements.

```tf
//Extended VM creation (cloud init + couple rules in sec group)
resource "openstack_compute_keypair_v2" "example_keypair" {
  name       = "example-keypair"
  public_key = file("./id_rsa.pub")
}

//Create security group with name sec_group
resource "openstack_networking_secgroup_v2" "sec_group" {
  name        = "sec_group"
  description = "Master sec group"
}

//Add ingress rule ssh in security group with name sec_group
resource "openstack_networking_secgroup_rule_v2" "allow_ssh" {
  direction         = "ingress"
  ethertype         = "IPv4"
  protocol          = "tcp"
  port_range_min    = 22
  port_range_max    = 22
  remote_ip_prefix  = "0.0.0.0/0" //For more secure add your IP/32
  security_group_id = "${openstack_networking_secgroup_v2.sec_group.id}"
}

//Add ingress rule ssh in security group with name sec_group
resource "openstack_networking_secgroup_rule_v2" "allow_http" {
  direction         = "ingress"
  ethertype         = "IPv4"
  protocol          = "tcp"
  port_range_min    = 80
  port_range_max    = 80
  remote_ip_prefix  = "0.0.0.0/0" //For more secure add your IP/32
  security_group_id = "${openstack_networking_secgroup_v2.sec_group.id}"
}

//Add ingress rule ssh in security group with name sec_group
resource "openstack_networking_secgroup_rule_v2" "allow_https" {
  direction         = "ingress"
  ethertype         = "IPv4"
  protocol          = "tcp"
  port_range_min    = 443
  port_range_max    = 443
  remote_ip_prefix  = "0.0.0.0/0" //For more secure add your IP/32
  security_group_id = "${openstack_networking_secgroup_v2.sec_group.id}"
}

//Add ingress rule ICMP all options in security group with name sec_group
resource "openstack_networking_secgroup_rule_v2" "allow_icmp" {
  direction         = "ingress"
  ethertype         = "IPv4"
  protocol          = "icmp"
  remote_ip_prefix  = "0.0.0.0/0" //For more secure add your IP/32
  security_group_id = "${openstack_networking_secgroup_v2.sec_group.id}"
}

resource "openstack_compute_instance_v2" "example_instance" {
  name        = "example-instance"
  image_name  = "ubuntu-server-22.04-LTS-20240110"
  flavor_name = "VC-2"
  key_pair    = openstack_compute_keypair_v2.example_keypair.name
  security_groups = [openstack_compute_secgroup_v2.sec_group.name]

  network {
     name = "public"
  }

  user_data = <<-EOF
              #cloud-config
              packages:
                - nginx
                - unattended-upgrades
              package_update: true
              package_upgrade: true
              EOF
}

```

## Basic Kubernetes setup

1. Keypair Creation:
An OpenStack compute SSH key pair named "example-keypair" is created using the `openstack_compute_keypair_v2` resource.
   - The name of the key pair is set to "example-keypair".
   - The public key is read from the file "./id_rsa.pub".

2. Kubernetes Cluster Creation:
An OpenStack Container Infrastructure (COI) cluster named "cluster_1" is created using the `openstack_containerinfra_cluster_v1` resource.
   - The name of the cluster is set to "cluster_1".
   - It is based on the cluster template with ID "v1.28.4".
   - One master node and one worker node are provisioned.
   - The SSH key pair "example-keypair" is used for authentication.
   - The master node is configured with flavor "VC-4" and the worker node with flavor "VC-2".
   - Floating IP is enabled for the cluster.

3. Get Kubernetes Configuration
A null resource named "get_kubeconfig" is used to execute a local command to retrieve the Kubernetes configuration.
   - It depends on the creation of the Kubernetes cluster resource.
   - The command executed is "mkdir -p ./kubeconfig && openstack coe cluster config ${openstack_containerinfra_cluster_v1.cluster_1.name} --dir ./kubeconfig", which creates a directory for the Kubernetes configuration and fetches it using the OpenStack client.

This code can be used to provision resources in the cloud, including creating k8s cluster. Adjustments can be made to customize the deployment according to specific requirements.

```tf
#Keypair
resource "openstack_compute_keypair_v2" "example_keypair" {
  name = "example-keypair"
  public_key = file("./id_rsa.pub")
}

#Create k8s cluster
resource "openstack_containerinfra_cluster_v1" "cluster_1" {
  name                = "cluster_1"
  cluster_template_id = "v1.28.4"
  master_count        = 1
  node_count          = 1
  keypair             = "example-keypair"
  master_flavor = "VC-4"
  flavor = "VC-2"
  floating_ip_enabled = true
}

//Get configuration
resource "null_resource" "get_kubeconfig" {
  depends_on = [openstack_containerinfra_cluster_v1.cluster_1]
  
  provisioner "local-exec" {
    command = "mkdir -p ./kubeconfig && openstack coe cluster config ${openstack_containerinfra_cluster_v1.cluster_1.name} --dir ./kubeconfig"
  }
}
```





