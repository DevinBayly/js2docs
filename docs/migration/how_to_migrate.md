## How to Migrate

### Overview
In order to migrate from Jetstream1 (JS1) to Jetstream2 (JS2) you'll need to understand:

!!! Migration Concepts ""

    * [Allocations](#Allocations)
    * [How to move data](#MoveData)
    * [Where to find help](#GetHelp)

---

### Allocations <a name="Allocations"></a>

Just as in JS1, you'll need an allocation of compute (`normal`, `large memory`, `GPU`) and `storage` resources, awarded by NSF and currently managed by [XSEDE](https://portal.xsede.org).
The allocation process is described here: [Allocation Overivew](/alloc/overview/)

You can take one of two approaches:

1. A [supplement](#Supplement) or renewal to a current research allocation -OR-
2. A completely [new allocation](#NewAllocation)

!!! note "New allocations vs renewals"

     By XSEDE policy, a PI may only have one startup allocation. If you have a valid allocation, consider renewing your startup, education, or champion allocation rather than trying to get a new allocation. Research allocations may be extended within reason but extensions are no substitute for the renewal process in general.</br>

### Supplement Allocation <a name="Supplement"></a>

If you already have a JS1 allocation, then we encourage you to request a supplement at a **[STARTUP](/alloc/startup/)** amount of resources for the `compute`, `large-memory-compute`, `GPU`, and `storage` resources on JS2. This will enable you to create the **Code, Performance, & Scaling** estimates you'll need for a successful project renewal on JS2.

If your startup or champion allocation is set to expire in June or July and is a NOT a research allocation **AND** is below the [normal startup limits on JS2](/general/resources/), you may also choose to renew it instead. Please ONLY look at extending allocations if you have a research allocation that won't be able to be reviewed at XRAC prior to Jetstream1 going offline.

[Education allocations](/alloc/education/) may also be renewed without restriction as long as there is proper justification.

* [Supplement](/alloc/supplement/)
* [Renewal](/alloc/renew-extend/)

!!! warning "Campus Champions"

    Please note that we will **NOT** be automatically adding [Campus Champions](https://www.xsede.org/community-engagement/campus-champions) allocations to Jetstream2. You will explicitly need to get a [supplement](/alloc/supplement/) for it.

### New Allocation <a name="NewAllocation"></a>

Of course, if your research will be changing, you can always apply for a new allocation of resources on JS2. We recommend you still start with a Startup level in order to create the **Code, Performance, & Scaling** estimates you'll need later for a Research allocation.

* [Allocation Overview](/alloc/overview/)
* [Startup Allocation](/alloc/startup)

---

### How to move your data <a name="MoveData"></a>

If you've already been using JS1, you'll likely wish to retain your old VMs and data, found within both VMs and in external volumes.
Below, we provide instructions for moving your VMs. As time permits, we anticipate the development of tools to help facilitate and partially automate migration.
Volumes on JS1 do not persist on JS2 because they are completely separate systems and do not share storage.

!!! note "Data volumes and VM transfers"

     As we note below, it is highly preferable to recreate resources on Jetstream2. Volume data, especially larger volumes, may be difficult to transfer easily. The Jetstream team can help with volume transfers and will discuss potentially helping with VM snapshots/transfers, though we highly encourage recreating VMs on Jetstream2. Please use the [contact form](https://jetstream-cloud.org/contact/index.html){target=_blank} and include your allocation number, resource names and UUIDs that you wish to discuss migrating.

#### Three approaches
There are essentially three approaches to accomplish data retention:

1. **Recreate your work** (STAFF RECOMMENDED)</br>
In order to get you going the fastest, take advantage of all the new features of JS2, and avoid any legacy configuration differences, it’s often advisable to simply create new VMs and bring in fresh software and data.</br>

    * Information about creating new VMs can be found for each type of user interface: [General Instance Management](/general/instancemgt) </br>
    * Instructions for tansfering files from external locations to JS2 VMs can be found here: [File Transfer](/general/filetransfer)</br></br>

2. **Copy your JS1 work**</br>
Similar to recreating your work, you can save some steps after [starting new VMs](/general/instancemgt) by copying your existing software from your current VM on JS1: [File Transfer](/general/filetransfer) </br>

!!! caution "CAUTION::JS1-compatibility"

     Network configurations and any instance management tools and scripts you’ve used previously will likely require updating to current values appropriate for JS2.</br>


!!! note "INFO::transfer speeds"

     Copying data from JS1 to JS2, particularly from within the same regional provider, will generally have good performance relative to a transfers across the internet.</br>

3. **Transfer your work** </br>
You can create snapshots of your existing JS1 VMs and request the [Help Desk Support](mailto:help@jetstream-cloud.org) team copy these snapshots as well as data volumes to Jetstream2.<br>

    * **Data volumes**:</br>
  This is fairly straightforward and is described below: [How to preserve JS1 VMs and data](#SaveData)</br>
    * **VMs**:</br>
  You can also follow the steps at [How to preserve JS1 VMs and data](#SaveData)</br>

!!! caution "CAUTION::JS1-compatibility"

     Please be aware that configurational differences between JS1 and JS2 generally prevent straight forward re-deployment of a JS1 VM on JS2. It may be more advisable to transfer the VM and mount the snapshot as a external volume on a new JS2 VM.</br>

!!! warning "EXOSPHERE::JS1 compatibility"

    If the VM you wish to transfer is not `Ubuntu 20` or higher or `Rocky 8` or higher, ***THE VM WILL NOT WORK WITH THE EXOSPHERE WEB DESKTOP***</br>


### How to preserve Jetstream1 VMs and data <a name="SaveData"></a>

- Identify if your VM or volume used the Atmosphere or API/CLI interface

!!! note Atmosphere-steps "Atmosphere"

    * **Atmosphere**:</br>
      * VMs:
        1. ***STAFF RECOMMENDED but not required***:: Contact staff and request a staff ssh-key to add to your VM to more easily allow staff to prepare the image for transfer.
        2. Follow the instructions here to [update and image your VM](/archive/atmosphere/Customizing+and+saving+a+VM) </br> **NOTE**: It is strongly recommended that users upgrade the operating system before imaging. </br> For CentOS based systems, it's `sudo yum update` <br/>For Ubuntu based systems, do `sudo apt-get update` and then `sudo apt-get upgrade`
        3. Next
            * Go to the **IMAGES** tab
            * Click on the Image you created
            * Click on the Version you want
            * Click on **COPY** for either IU or TACC to grab the UUID of the image
            * Submit a ticket with your **USERNAME**, VM **PROJECT FOLDER**, and VM **UUID** to [help@jetstream-cloud.org](mailto:help@jetstream-cloud.org) to ask staff to copy your image to Jetstream2. </br>
      * Volumes:
        1. Click on the **PROJECTS** tab
        2. Click on the Project Folder
        3. Scroll down to **VOLUMES** and click on the desired volume
        4. Click on **COPY** to grab the UUID of the image.
        5. Submit a ticket with that VUID to [help@jetstream-cloud.org](mailto:help@jetstream-cloud.org) to ask staff to copy your volume to Jetstream2.</br>


!!! note "API"

    * **API**:
      * VMs:
        1. ***STAFF RECOMMENDED but not required***: Contact staff and request a staff ssh-key to add to your VM to more easily allow staff to prepare the image for transfer.
        2. Follow the instructions here to [create a snapshot of your instance](/ui/cli/snapshot-image)</br>
        3. Make note of the VM UUID
        4. Submit a ticket with that UUID to [help@jetstream-cloud.org](mailto:help@jetstream-cloud.org) to ask staff to copy your image to Jetstream2.</br>
      * Volumes:
        1. Use the command: `openstack volume list`
        2. Note the Volume UID
        3. Submit a ticket with that VUID to [help@jetstream-cloud.org](mailto:help@jetstream-cloud.org) to ask staff to copy your image to Jetstream2.

---

### Where to find help documentation <a name="GetHelp"></a>

* **JS1**:</br>Documentation for JS1 will temporarily remain during the summer of 2022 at [https://wiki.jetstream-cloud.org](https://wiki.jetstream-cloud.org) </br>

    !!! warning ""
        This documentation will likely **NOT** be updated.

* **JS2**:</br>The latest JS2 documentation will be maintained at [docs.jetsteam-cloud.org](https://docs.jetsteam-cloud.org)

* **NEWS**: Announcements will be made at the [XSEDE User News : https://www.xsede.org/news/user-news site ](https://www.xsede.org/news/user-news) </br> To ensure that you are receiving all updates to your inbox, login to the page to manage your XSEDE User News subscriptions. All Jetstream users should be added when they are placed on an allocation, but you may wish to verify so that you don't miss any important migration updates.

!!! example "LIVE UPDATES"

    Updates will all be made [Jetstream2 System Status and Information](overview/status/) and shared via [XSEDE User News : https://www.xsede.org/news/user-news site ](https://www.xsede.org/news/user-news).
