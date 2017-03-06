Title: Desktop Virtualization, Solid Edge style (revisited)
Published: 6/6/2011
Image: /images/background-1920x1080.png
Tags:
  - Solid Edge
---

This is a follow up to my original post Desktop Virtualization, Solid Edge style. It seems that I created more questions than I answered so I will try to address those questions here.

**Host machine**

Many wanted to know what setup I was running all of this on. Below are some screenshots showing some of the details.  Please keep in mind that these are not good specifications for a typical CAD machine but is adequate for the type of work that I do.

* [Windows 7 Enterprise](http://www.microsoft.com/windows/enterprise/products/windows-7/default.aspx) x64 Service Pack 1
* [EVGA® P55 SLI Motherboard](http://www.evga.com/products/moreInfo.asp?pn=132-LF-E655-KR&family=Motherboard%20Family&series=Intel%20P55%20Series%20Family&sw=5)
* [Intel® Core™ i7-875K Processor](http://ark.intel.com/Product.aspx?id=48499) (Overclocked to 4 GHz)
* [ADATA XPG Gaming Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800)](http://www.newegg.com/Product/Product.aspx?Item=N82E16820211409) (16GB Total)
* [SAPPHIRE 100282SR Radeon HD 5850 1GB 256-bit GDDR5 PCI Express 2.0 x16](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102857)
* Western Digital Caviar Black WD1501FASS 1.5TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive (OS and Data)
* Western Digital Caviar Black WD2001FASS 2TB 7200 RPM 64MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive (Backups)
* SAMSUNG F1R RAID-Class HE103UJ 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Hard Drive (Virtual machines)

This screenshot shows the details of my processor.  The Intel 875K has a clock speed of 2.93 GHz but can easily be overclocked to 4 GHz on air!  I have run this setup for a long time with no problems at all.

![](http://blob.jasonnewell.net/blog/2011-06-06_1.png "Intel 875K overclocked to 4 GHz")

I am a programmer in the purest sense but I do have a background in hardware.  Still to this day, I get all gitty when I get all of the components in and start building.

![](http://blob.jasonnewell.net/blog/2011-06-06_2.png "Custom built Intel 875K")

This screenshot shows my drive configuration.  I like to keep things separate for several reasons.  Performance is one, isolation is the other.

![](http://blob.jasonnewell.net/blog/2011-06-06_3.png "Host machine drives")

**VMWare Workstation Snapshots and licensing**  
There was confusion over this screenshot in the previous blog.  What you are actually seeing here is a **single** VM (instance) with snapshots.  After creating the virtual machine, I installed Windows, Windows updates and anything else that I wanted in the Baseline snapshot.  It is important to note that once a snapshot is taken, it is literally locked in time and cannot be directly modified.  You can branch off of a snapshot and create a new snapshot though.  Once I had the Baseline defined, I installed Solid Edge V16 and took another snapshot.  Service packs followed in the same manner.  When I was ready to install Solid Edge V17, I reverted back to the Baseline snapshot and installed from that point in time.  The process repeats for each version of Solid Edge.

![](http://blob.jasonnewell.net/blog/2011-06-06_4.png "Single instance of Solid Edge VM with snapshots")

In this scenario, I need one license for Windows and one license for Solid Edge.  The Solid Edge license in use is node locked to the volume id of the virtual machines hard drive.  This is exactly the same as having a physical computer but with benefits.  Since Solid Edge licenses expire and snapshots are locked in time, you may have to update your selicense.dat ([obtained from GTAC](http://support.industrysoftware.automation.siemens.com/gtac.shtml)) when reverting to an older snapshot.  
This works well for someone like me who does development work or just wants to go back to a previous version of Solid Edge to test particular features.  This setup is great for what I'm using it for but depending on your needs, may not be the best approach.  For instance, if you're wanting to test hardware for Solid Edge, you would want a dedicated physical machine.  
**VMWare Workstation settings**  
You have many options when configuring virtual machines.  The following screenshots shows how you can allocate hardware from your physical host to your virtual machine.  Regarding performance for Solid Edge in a virtual machine, I would say that it really depends on a lot of factors.  Host hardware is the most important.  You need a fast machine with a lot of capacity.  From there, Virtual machine settings dictate how much of the hosts hardware can be allocated to the virtual machine.  Past that, you really just need to try it for yourself and see if it's fast enough for your needs.  VMWare does offer a [guide on performance tuning](http://www.vmware.com/pdf/ws7_performance.pdf).  One thing I found interesting is that the Windows 7 [Windows Experience Index](http://windows.microsoft.com/en-US/windows-vista/What-is-the-Windows-Experience-Index) for the primary hard disk of the virtual machine scored better than in my host!  Definitely a what the hell moment.  I can only assume that it has something to do with how VMWare implemented their virtual disk technology.

![](http://blob.jasonnewell.net/blog/2011-06-06_5.png "VMWare Workstaion Settings - Memory")

![](http://blob.jasonnewell.net/blog/2011-06-06_6.png "VMWare Workstaion Settings - Processors")

![](http://blob.jasonnewell.net/blog/2011-06-06_7.png "VMWare Workstaion Settings - Disks")

![](http://blob.jasonnewell.net/blog/2011-06-06_8.png "VMWare Workstaion Options - General")