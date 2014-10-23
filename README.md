iplant_upload
=============

A repo detailing commands for moving data from the Berkely FTP server to iPlant Data Store, via Atmosphere. 

This process is somewhat confusing for users who are not familiar with iPlant Atmosphere or FTP. This is my attempt to:
<br>
[1] document what commands I have used and keep track of the most efficient method for moving data to iPlant from the FTP server.
<br>
[2] Hopefully provide a rough guide to other users in the RILAB to aid in transfer of data in the future.

There is a very good duide already written at this [This link](https://www.google.com/url?q=https%3A%2F%2Fgithub.com%2Fmfcovington%2Fucd_plantbio_tutorials%2Fblob%2Fmaster%2Fiplant%2Fiplant_data_store.tutorial.mdown%23bonus-material-mounting-irods-via-atmosphere-instance&sa=D&sntz=1&usg=AFQjCNE4pVn_cv9v8C2rHx4e-JKZIBbBhA).

The following steps are needed before you can proceed with data transfer. 

* Set up an iPlant account [here](http://www.iplantcollaborative.org).
* 
* Request access to Atmosphere [here] (http://www.iplantcollaborative.org/ci/atmosphere).

***Setting up an instance***

* Start an instance of a virtual machine on Atmosphere, a guide can be found [here](https://pods.iplantcollaborative.org/wiki/display/atmman/Stopping+and+Starting+an+Instance). I usually start an Ubuntu VM, as I am familiar with Linux/Unix command line. You can choose what suits you, but the rest of the guide assumes you have chosen a linux/unix VM.

You must create a volume (guide [here](https://pods.iplantcollaborative.org/wiki/display/atmman/Creating+a+Volume)), and then mount (guide [here](https://pods.iplantcollaborative.org/wiki/display/atmman/Creating+a+Volume)). that volume to your Atmosphere instance.

***Logging on to the VM using ssh***

Once the VM is initiallised, this can take 30 mins to 1 hour, you will get an email telling you that the VM is ready. At this point you should:

* Find the IP address of the machine, you can find this on iPlant Atmosphere under the "My Instances" panel, or in the email that iPlant send confriming your instances is running.
* log on from your desktop terminal to the iPlant VM using ssh and a command something like: username@IP.address, your iPlant password is required to log on. 

***Mounting the iPlant Data Store in you home dir***

You should now be connected to your VM via ssh. In order to send data to the iPlant Data Store you need to mount the data store in one of your directories. This is the confusing part and the main point of this guide. I'm sure there are many ways to achieve this but this is what I did to set up the data store in my home directory.

* In the location you like (I picked my home dir) you should set up a folder in which the iPlant Data Store will be mounted.
* Secondly, set up IRODS (a description is [here](https://pods.iplantcollaborative.org/wiki/display/DS/Using+iCommands#UsingiCommands-InitiatingtheiRODSconnectionandconfiguringthesettings%28Onetimeonly%29). iRODS essentially allows you to mount the iPlant Data store and use [iCommands](https://pods.iplantcollaborative.org/wiki/display/DS/Using+iCommands) and must be activated before you can transfer data. You can do this using the iCommand *iinit*, as detailed below.


    bash-3.2$ iinit
    One or more fields in your iRODS environment file (.irodsEnv) are
    missing; please enter them.
    Enter the host name (DNS) of the server to connect to:data.iplantcollaborative.org
    Enter the port number:1247
    Enter your irods user name:username
    Enter your irods zone:iplant
    Those values will be added to your environment file (for use by
    other i-commands) if the login succeeds.
    Enter your current iRODS password:password
    bash-3.2$
    



