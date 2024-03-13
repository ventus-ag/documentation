---
title: IaC Pulumi
weight: 30
---
___
On this page, you can find essential steps and code for starting with Pulumi and Cloud, from installation to advanced deployment scenarios, highlighting the benefits of infrastructure as a code (IaaC) for simplifying and automating cloud infrastructure management.

# Table of contents
- [Table of contents](#table-of-contents)
	- [Prerequisites](#prerequisites)
	- [Basic virtual machine setup](#basic-virtual-machine-setup)
	- [Complex virtual machine setup](#complex-virtual-machine-setup)
	- [Basic Kubernetes setup](#basic-kubernetes-setup)


## Prerequisites

- **Pulumi installation** - https://www.pulumi.com/docs/install
- **Create CLI user** - https://docs.ventuscloud.eu/products/security/cli-users
- **Save credentials in Pulumi secrets** - In our scenario, we utilize the Pulumi CLI to securely store credentials. More detailed info https://www.pulumi.com/docs/concepts/secrets

{{% notice note %}}
The Pulumi CLI never transmits your cloud credentials to Pulumi Cloud.
{{% /notice %}}

Before proceeding with the examples, it's necessary to execute the following Pulumi CLI commands to securely store credentials locally. You can obtain all the credential data from the "rc" file that was downloaded after creating the OpenStack CLI user.

```bash
pulumi config set authUrl $OS_AUTH_URL
pulumi config set --secret userName $OS_USERNAME
pulumi config set --secret passWord $OS_PASSWORD
pulumi config set tenantId $OS_PROJECT_DOMAIN_ID
pulumi config set domainName $OS_USER_DOMAIN_NAME
```

Create project and run Pulumi stack:

```bash
mkdir ventus && cd ventus
pulumi new ventus-dev
```
{{% notice note %}}
"If you're using pulumi new or any other pulumi command for the first time, you might need to log in to Pulumi Cloud. Pulumi CLI and Pulumi Cloud work together to provide a reliable experience. It's free for personal use, offers features for teams, and there are also self-managed options available. Pressing Enter at the prompt will open a browser for you to sign in or sign up."
{{% /notice %}}

Place the code example within the "ventus" directory and run:

```bash
pulumi up
```

## Basic virtual machine setup

The Go code snippet provided below defines an infrastructure deployment using Pulumi for managing resources on the Cloud. Here's a breakdown of what it does:

1. Imports necessary packages from Pulumi and the Pulumi OpenStack SDK.
2. Sets up the main function to execute the Pulumi program.
3. Reads configuration values for authentication details from Pulumi configuration.
4. Initializes the OpenStack provider with the authentication details.
5. Creates a new SSH key pair for accessing instances.
6. Defines a security group to allow SSH access.
7. Adds a security group rule to permit inbound SSH connections.
8. Specifies the configuration for launching a new virtual machine (VM), including its flavor, image, networks, SSH key pair, and security groups.
9. Deploys the VM instance.
10. Exports the IP address of the deployed VM.

This code can be used to provision resources on the cloud, including creating VM instances with SSH access configured via key pairs and security groups. Adjustments can be made to customize the deployment according to specific requirements.

```go
package main

import (
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack"
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack/compute"
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack/networking"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi/config"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {

		cfg := config.New(ctx, "")

		openstackProvider, err := openstack.NewProvider(ctx, "openstack", &openstack.ProviderArgs{
			AuthUrl:    pulumi.String(cfg.Require("authUrl")),
			UserName:   pulumi.String(cfg.Require("userName")),
			Password:   pulumi.String(cfg.Require("passWord")),
			TenantId:   pulumi.String(cfg.Require("tenantId")),
			DomainName: pulumi.String(cfg.Require("domainName")),
		})
		if err != nil {
			return err
		}

		// Create a new key pair for SSH access
		keyPair, err := compute.NewKeypair(ctx, "keyPair", &compute.KeypairArgs{
			Name: pulumi.String("my-keypair"),
			// Public key would be string contents of your public key for SSH access
			PublicKey: pulumi.String("PUBLIC KEY"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Define the security group to allow SSH access
		secGroup, err := networking.NewSecGroup(ctx, "secGroup", &networking.SecGroupArgs{
			Name:        pulumi.String("ssh"),
			Description: pulumi.String("Allow SSH"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Add a security group rule to allow inbound SSH connections
		_, err = networking.NewSecGroupRule(ctx, "ssh", &networking.SecGroupRuleArgs{
			Direction:       pulumi.String("ingress"),
			Ethertype:       pulumi.String("IPv4"),
			PortRangeMin:    pulumi.Int(22),
			PortRangeMax:    pulumi.Int(22),
			Protocol:        pulumi.String("tcp"),
			SecurityGroupId: secGroup.ID(),
			RemoteIpPrefix:  pulumi.String("0.0.0.0/0"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Create a new OpenStack VM
		vm, err := compute.NewInstance(ctx, "vm", &compute.InstanceArgs{
			FlavorName: pulumi.String("VC-2"),
			ImageName:  pulumi.String("ubuntu-server-22.04-LTS-20240110"),
			Name:       pulumi.String("example-vm"),
			Networks: compute.InstanceNetworkArray{
				&compute.InstanceNetworkArgs{Name: pulumi.String("public")},
			},
			KeyPair:        keyPair.Name,
			SecurityGroups: pulumi.StringArray{secGroup.Name},
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}
		// Export the IP address of the VM

		ctx.Export("ip", vm.AccessIpV4)

		return nil
	})
}

```

## Complex virtual machine setup

The Go code snippet provided below defines an infrastructure deployment using Pulumi for managing resources on the Cloud. Here's a breakdown of what it does:

1. Imports necessary packages from Pulumi and the Pulumi OpenStack SDK.
2. Sets up the main function to execute the Pulumi program.
3. Reads configuration values for authentication details from Pulumi configuration.
4. Initializes the OpenStack provider with the authentication details.
5. Creates a new SSH key pair for accessing instances.
6. Defines a security group to allow SSH and web access.
7. Adds security group rules to permit inbound SSH (port 22) and web (ports 80 and 443) connections.
8. Specifies the configuration for launching a new virtual machine (VM), including its flavor, image, networks, SSH key pair, security groups, and user data script.
9. Deploys the VM instance with the specified configuration.
10. Exports the IP address of the deployed VM.

The userDataScript variable contains a shell script that is executed as UserData to configure the VM. It installs nginx and starts the service.

This code can be used to provision resources on the Cloud, including creating VM instances with SSH and Web access configured via key pairs and security groups. Adjustments can be made to customize the deployment according to specific requirements.

```go
package main

import (
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack"
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack/compute"
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack/networking"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi/config"
)

func main() {
	pulumi.Run(func(ctx *pulumi.Context) error {

		cfg := config.New(ctx, "")

		openstackProvider, err := openstack.NewProvider(ctx, "openstack", &openstack.ProviderArgs{
			AuthUrl:    pulumi.String(cfg.Require("authUrl")),
			UserName:   pulumi.String(cfg.Require("userName")),
			Password:   pulumi.String(cfg.Require("passWord")),
			TenantId:   pulumi.String(cfg.Require("tenantId")),
			DomainName: pulumi.String(cfg.Require("domainName")),
		})
		if err != nil {
			return err
		}

		// Create a new key pair for SSH access
		keyPair, err := compute.NewKeypair(ctx, "keyPair", &compute.KeypairArgs{
			Name: pulumi.String("my-keypair"),
			// Public key would be string contents of your public key for SSH access
			PublicKey: pulumi.String("PUBLIC KEY"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Define the security group to allow SSH access
		secGroup, err := networking.NewSecGroup(ctx, "secGroup", &networking.SecGroupArgs{
			Name:        pulumi.String("sshandweb"),
			Description: pulumi.String("Allow SSH access and Web access"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Add a security group rule to allow inbound SSH connections
		_, err = networking.NewSecGroupRule(ctx, "ssh-access-80", &networking.SecGroupRuleArgs{
			Direction:       pulumi.String("ingress"),
			Ethertype:       pulumi.String("IPv4"),
			PortRangeMin:    pulumi.Int(22),
			PortRangeMax:    pulumi.Int(22),
			Protocol:        pulumi.String("tcp"),
			SecurityGroupId: secGroup.ID(),
			RemoteIpPrefix:  pulumi.String("0.0.0.0/0"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Add a security group rule to allow inbound WEB connections
		_, err = networking.NewSecGroupRule(ctx, "web-access-443", &networking.SecGroupRuleArgs{
			Direction:       pulumi.String("ingress"),
			Ethertype:       pulumi.String("IPv4"),
			PortRangeMin:    pulumi.Int(80),
			PortRangeMax:    pulumi.Int(80),
			Protocol:        pulumi.String("tcp"),
			SecurityGroupId: secGroup.ID(),
			RemoteIpPrefix:  pulumi.String("0.0.0.0/0"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Add a security group rule to allow inbound WEB connections
		_, err = networking.NewSecGroupRule(ctx, "web-access", &networking.SecGroupRuleArgs{
			Direction:       pulumi.String("ingress"),
			Ethertype:       pulumi.String("IPv4"),
			PortRangeMin:    pulumi.Int(443),
			PortRangeMax:    pulumi.Int(443),
			Protocol:        pulumi.String("tcp"),
			SecurityGroupId: secGroup.ID(),
			RemoteIpPrefix:  pulumi.String("0.0.0.0/0"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}

		// Create a new OpenStack VM
		vm, err := compute.NewInstance(ctx, "vm", &compute.InstanceArgs{
			FlavorName: pulumi.String("VC-2"),
			ImageName:  pulumi.String("ubuntu-server-22.04-LTS-20240110"),
			Name:       pulumi.String("example-vm"),
			Networks: compute.InstanceNetworkArray{
				&compute.InstanceNetworkArgs{Name: pulumi.String("public")},
			},
			KeyPair:        keyPair.Name,
			SecurityGroups: pulumi.StringArray{secGroup.Name},
			UserData:       pulumi.String(userDataScript),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}
		// Export the IP address of the VM

		ctx.Export("ip", vm.AccessIpV4)

		return nil
	})
}

// userDataScript contains the shell script to be executed as UserData.
var userDataScript = `
#cloud-config

apt:
  preserve_sources_list: true
  sources:
    - sourceline: "deb http://archive.ubuntu.com/ubuntu focal main universe"

package_upgrade: true

packages:
  - nginx

runcmd:
  - systemctl start nginx

`

```



## Basic Kubernetes setup
The Go code snippet provided below sets up an kubernetes cluster scenario using Pulumi to manage resources on the Cloud. Here's a breakdown of its functionality:

1. It imports necessary packages from Pulumi and the Pulumi OpenStack SDK.
2. Configuration values for authentication details are retrieved from Pulumi configuration.
3. An OpenStack provider is initialized with the authentication details.
4. A new SSH key pair is created for accessing instances.
5. Using the container infrastructure API, a Kubernetes cluster is created.

The cluster configuration includes parameters such as the cluster template ID, key pair for authentication, master and node counts, and flavor of the VM instances.

The kubeconfig for the provisioned Kubernetes cluster is exported to Pulumi config as a secret.


```go
package main

import (
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack"
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack/compute"
	"github.com/pulumi/pulumi-openstack/sdk/v3/go/openstack/containerinfra"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi"
	"github.com/pulumi/pulumi/sdk/v3/go/pulumi/config"
)

func main() {

	pulumi.Run(func(ctx *pulumi.Context) error {

		cfg := config.New(ctx, "")

		openstackProvider, err := openstack.NewProvider(ctx, "openstack", &openstack.ProviderArgs{
			AuthUrl:    pulumi.String(cfg.Require("authUrl")),
			UserName:   pulumi.String(cfg.Require("userName")),
			Password:   pulumi.String(cfg.Require("passWord")),
			TenantId:   pulumi.String(cfg.Require("tenantId")),
			DomainName: pulumi.String(cfg.Require("domainName")),
		})
		if err != nil {
			return err
		}

		// Create a new key pair for SSH access
		_, err = compute.NewKeypair(ctx, "keyPair", &compute.KeypairArgs{
			Name: pulumi.String("my-keypair"),
			// Public key would be string contents of your public key for SSH access
			PublicKey: pulumi.String("PUBLIC KEY"),
		}, pulumi.Provider(openstackProvider))
		if err != nil {
			return err
		}
		//create k8s cluster
		k8s, err := containerinfra.NewCluster(ctx, "k8s1", &containerinfra.ClusterArgs{
			ClusterTemplateId: pulumi.String("ID"), //openstack coe cluster template list
			Keypair:           pulumi.String("my-keypair"),
			MasterCount:       pulumi.Int(1),
			NodeCount:         pulumi.Int(1),
			Flavor:            pulumi.String("VC-2"),
			MasterFlavor:      pulumi.String("VC-2"),
		}, pulumi.Provider(openstackProvider))

		if err != nil {
			return err
		}

		// Export the kubeconfig to pulumi config in secret
		ctx.Export("kubeconfig", k8s.Kubeconfig)

		return nil
	})

}
```





