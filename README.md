<p align="center">
#<!--img src="https://i.postimg.cc/3xyYzDS4/About-Phone-Transparent-v2-6.png" --> 

FreakyOS Android 11 2020
==================================================

[![Download FreakyOS](https://img.shields.io/sourceforge/dd/FreakyOS.svg)](https://sourceforge.net/projects/FreakyOS/files/)

Getting Started
==================================================

How to build FreakyOS ROM for your device - Tutorial
--------

>> To get started with the building process, you'll need to get familiar with [Git and Repo](http://source.android.com/source/using-repo.html).

### Build Environment

- Tested and Working on any version of Ubuntu - 14.04,14.10,15.04,16.04,18.04 (64-bit)
- Any other distribution based of the Ubuntu Distro such as Lubuntu, Xubuntu and etc.
- Any form of Terminal
- Decent hardware (minimum of at least a quad core CPU and 16 GB of RAM)
- A storage unit of any kind (We recommend utilizing SSDs as Mechanical HDDs slow down the build proccess drastically and the minimum storage size is 70GB. Having more will be useful with CCache[More on that later])
- Required Packages should have been installed

### Required Packages [this is for ubuntu 16.04, for other variants it may differ]
##### Simply copy and paste this in a terminal window:
>> [Hint: This command updates the Ubuntu Packages List (Install Listing) and install the required version of Java]

```bash
     $ sudo apt-get install openjdk-8-jdk
```

### Let that install and then proceed.

### More copy and paste:
>> [Hint: Running this command installs the other required packages to build android]

```bash
     $ sudo apt-get update && sudo apt-get install bc git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk3.0-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev openjdk-8-jre openjdk-8-jdk pngcrush schedtool libxml2 libxml2-utils xsltproc lzop libc6-dev schedtool g++-multilib lib32z1-dev lib32ncurses5-dev lib32readline6-dev gcc-multilib maven tmux screen w3m ncftp adb fastboot repo python default-jdk
```

### Getting the source
- Making required directories
- Obtaining the repo binary
- Adding repo binary to your path
- Giving the repo binary proper permissions
- Initializing an empty repo
- Syncing the repo

>> Alright, so now we’re getting there. I have outlined the basics of what we’re about to do and broke them down as I know them. This is all pretty much going to be copy/paste so it’ll be fairly difficult to screw this up :)

##### Make directory for the repo binary

```bash
      $ mkdir ~/bin
```

##### Add directory for the repo binary to its path

```bash
      $ PATH=~/bin:$PATH
```

##### Downloading repo binary and placing it in the proper directory

```bash
      $ curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
```

##### Giving the repo binary the proper permissions

```bash
      $ chmod a+x ~/bin/repo
```

##### Creating directory for where the $WORKSPACE repo will be stored and synced

```bash
      $ mkdir ~/$WORKSPACE
      $ cd ~/$WORKSPACE
```

##### Initializing the $WORKSPACE repo and downloading the manifest

```bash
      $  repo init --depth=1 -u https://github.com/FreakyOS/manifest.git -b never_dead
```

##### Syncing the source
>> [Hint: This might take a long time as the source is ~26GB]

```bash
      $  repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags
```

### Building the FreakyOS ROM
- Preparing Required Binaries and Device Drivers
- Setting Up CCache (Optional)
- Building FreakyOS

>> Congratulations on the succesfull build initialization! Now, we shall go ahead and prepare to build for your device!

##### Preparing FreakyOS ROM for devices
- Follow the AOSP Porting Instructions stated here to prepare the proprietary files for building for your device: (http://xda-university.com/as-a-developer/porting-aosp-roms-using-source-code)

##### Setting Up CCache
- CCache is a method of utilizing a specified storage space to speed up building. It can be referred to as the same caching your android device does to speed up application and system boot times. In this case, CCache will help build FreakyOS faster than standard build times (Able to cut-down 50% of time taken to build).
- To set up CCache, follow the following:

```bash
        $ echo "export USE_CCACHE=1" >> ~/.bashrc
```

##### To build FreakyOS ROM

```bash
      $ cd ~/$WORKSPACE
      $ source build/envsetup.sh
      $ lunch freaky_<devicecodename>-userdebug
      $ make bacon -j$(nproc --all)
```

##### Obtaining the zip created from the build process
>> To get the zip file that has been built, navigate to the following directory and find for the zip file:

```bash
      $ cd ~/$WORKSPACE/out/target/product/<devicename>
```

OR

```bash
      $ cd $OUT
```

>> If you found it, then congratulations! If you didn't, try retrying the build process but before doing so, ensure you do the following to make sure your next build is clean;

```bash
      $ cd ~/$WORKSPACE
      $ make clean
      $ repo sync --force-sync
```

>> After doing so, redo everything stated from the Building Section.

##### For those who successfully built FreakyOS

>> Well, Congratulations on your victory! Now, you have a .zip file that flashable to your device! Share it to the internet as you wish but be sure to contribute back and also give credits to the FreakyOS Team and its contributors! Also keep in mind that if an official build exists for a device, no unofficial builds should be released publicly. Do come and build FreakyOS another time as source code is routinely being improved upon. If you wish to contibute, feel free to make a pull request to the FreakyOS Team! See you again builder! Note: If you decide to create a thread on xda, please limit the thread to only one per device. More than one thread will not be allowed per device as it creates confusion amongst users and makes it hard for us to track bug reports.

-----------------------------------------	
Getting Official Maintainership for FreakyOS
==========================================
>> To get Official Maintainership for FreakyOS you should have a stable device source with all the main components working.

>> First make an unofficial build of FreakyOS and post in [**XDA**](xda-developers.com).

>> Then, Ping us on Telegram :- [**bunnyy**](https://t.me/bun_nyy) | [**Niteshkumar**](https://t.me/Niteshkumar15)

>> Join our [**Telegram Channel**](https://t.me/FreakyOS_channel) and our  [**Telegram group**](https://t.me/FreakyOS_official)

>> To publish builds use our Template : [**FreakyOS XDA Template**](https://github.com/FreakyOS/FreakyOS-Template)

----------------------------

Submitting Patches
==================
>> FreakyOS is an open source project thus any patches/contributions are always welcome !

>> To begin with, you need to login to our code review system at [FreakyOS Code Review](http://freakyos.xyz)

>> We support login using Github Oauth provider, which means if you have either of account you can login to gerrit by that account.
It is important that you set the USERNAME in your account on gerrit. If you have logged in using Github account then your Github USERNAME will be used as gerrit USERNAME automatically. Else you can set unique username in `Profile` section of gerrit account Settings.

>> The next step is to add your SSH key to your gerrit account.

>> Refer the Github guide on [how to generate SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)

>> Add the generated SSH key (the contents of id_rsa.pub file) to your gerrit account in `SSH Public Keys` section.


>> You can upload the patches/contributions for review process using following procedure:

- [Always make sure to clone ssh with commit msg-hook]

```bash
      $ git clone "ssh://$USERNAME@freakyos.xyz:29418/FreakyOS/official_devices" && scp -p -P 29418 $USERNAME@freakyos.xyz:hooks/commit-msg "official_devices/.git/hooks/"
```

>> For Example -  git clone "ssh://bunnyy@freakyos.xyz:29418/FreakyOS/official_devices" && scp -p -P 29418 bunnyy@freakyos.xyz:hooks/commit-msg "official_devices/.git/hooks/"

```bash
      $ cd CLONED_DIRECTORY
```

>> Make the changes you wish to add for review and execute following commands,

```bash
      $ git add -A
      $ git commit -m "commit message"
```

>> Commit message should be clear, well written and easy to understand.

>> If you have satisfied with the changes you made then you can upload the patchset to gerrit.

```bash
      $ git push ssh://USERNAME@freakyos.xyz:29418/PROJECT_NAME HEAD:refs/for/never_dead
```

>> Here the PROJECT_NAME is the path to repository on gerrit. You can find the PROJECT_NAME by navigating to the `Projects` section on gerrit.

>> For example - FreakyOS/packages_apps_Settings

>> It is recommended that you commit your several relevent patches in to one single commit.

>> Squash multiple commits using this command:

```bash
      $ git rebase -i HEAD~<# of commits>
```

>> If you are going to make extra changes to an existing patch, Don't start a new patch, instead

```bash
      $ git add .
      $ git commit --amend
```
>> and simply push the changes to gerrit

>> Gerrit will recognize it as a new patchset in an exisiting commit.

>> To view the status of your and/or others patches, visit [FreakyOS Code Review](http://freakyos.xyz)

<p align="center">
#<!--img src="https://i.postimg.cc/3xyYzDS4/About-Phone-Transparent-v2-6.png" --> 

