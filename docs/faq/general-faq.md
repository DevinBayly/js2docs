#Jetstream2 FAQ Home

For specific FAQs, see the following pages:

* [Early Operations FAQ](js2-earlyops-faq.md)
* [Allocations FAQ](alloc.md)
* [Troubleshooting](trouble.md)
* [Security FAQ](security.md)
* [Software FAQ](software.md)
* [Gateways FAQ](gateways.md)

---
## General FAQs

### How do I cite Jetstream2 ?

The Jetstream2 team requests that all researchers using Jetstream2 cite us in any publications that utilize results that were computed or created on Jetstream2. We keep the most up to date citation information here - [Jetstream2 Citation Information](https://jetstream-cloud.org/research/index.html#cite-jetstream){target=_blank} 

### I need a root disk larger than the maximum size for Jetstream2 instances. Can you create a custom flavor for me?

In OpenStack, flavors define the compute, memory, and storage capacity of instances. We may also refer to it in support tickets or documentation as the VM's size.

We won't create custom flavors, but there are ways to get larger root disks. You can [review the flavors](../general/vmsizes.md) and see if moving up from one of the smaller VMs to a slightly larger one would yield a larger root disk. The other option is to use a custom sized root disk using what Openstack calls "boot from volume", or a "volume-backed" instance. What this means is that instead of an ephemeral boot disk for the instance, a volume is used to be the root disk.

There are several upsides to this:

* You can have a root disk large enough to fit your needs
* The disk becomes reusable as a volume if necessary
* Shelving the instance is extremely fast compared to shelving a typical instance

The downside is that using boot from volume will count against your Jetstream2-Storage allocation whereas root disks do not.

Instructions for using boot from volume are here:

* [Exosphere: Choose a Root Disk Size](https://docs.jetstream-cloud.org/ui/exo/create_instance/#configure-instance)
* Cacao (link coming)
* Horizon (link coming)
* CLI (link coming)

---

### How do I get access to one of the Jetstream2 regional clouds?

The regional clouds of Jetstream2 (Arizona State University, Cornell University, University of Hawai'i, and Texas Advanced Computing Center) are available via invitation only. They have limited resources and the local PIs have discretion as to which projects may run there.

All allocations gain access to the primary Jetstream2 cloud at Indiana University. If you have an allocation and wish to have it added to a regional cloud, you can [request access using this form](https://jetstream-cloud.org/contact/index.html){target=_blank}

*As the regional clouds have autonomy over their access and because resources are limited, it's important to note that not all requests may be accommodated.*

---

### Will there be Microsoft Windows support on Jetstream2 ?

Microsoft Windows is not officially supported on Jetstream2. We will be making a limited number of images available for experimental use.

It is not known at this time whether GPUs will work on Microsoft-based instances. We will test this as time permits.

More information may be found on the [Microsoft Windows on Jetstream2](../general/windows.md) page.

---

### How do I share a volume between virtual machines?


You can’t easily share volumes in OpenStack without deploying a Shared File System service. However, the native Openstack Manila filesystems-as-a-service option is available.

Instructions for using manila on Jetstream2 are here - [Manila - Filesystems-as-a-service - on Jetstream2](https://docs.jetstream-cloud.org/general/manila/)

Please note, there are different quotas for block storage (volumes) and shares. There will be a self-service tool for managing those quotas soon, but for now, if you need to have your Jetstream2 Storage quota adjusted between block and share storage, please [contact us via the Jetstream2 contact form](https://jetstream-cloud.org/contact/index.html){target=_blank} with the amount you wish to move between the storage types.

---

### Can I set the password for a user on my virtual machine?

We generally don't recommend using password authentication on Jetstream2, recommending that you use SSH keys for access. That said, if you need to set a password for console access or for some other reason, you can do it like this:

    sudo passwd *username*
