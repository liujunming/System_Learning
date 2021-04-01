 the file descriptor is the gateway into the kernel's abstractions of underlying hardware.

 

In the simplified example above, we can see the drivers provide a read and write function that will be called in response to the analogous operations on the file descriptor. The device driver knows how to convert these generic requests into specific requests or commands for a particular device.

 

Physical devices on the host are represented by a file in a special file system such as /dev. 

In UNIX-like systems, so-called *device-nodes* have what are termed a *major* and a *minor* number, which allow the kernel to associate particular nodes with their underlying driver. 

 

In a broad sense, what happens when a file is opened is that the kernel is using the path information to map the file descriptor with something that provides an appropriate read and write, etc., API. When this open is for a device (/dev/sr0 above), the major and minor number of the opened device node provides the information the kernel needs to find the correct device driver and complete the mapping. The kernel will then know how to route further calls such as read to the underlying functions provided by the device driver.

 

There are indeed many other layers that complicate the picture in real-life. For example, the kernel will go to great efforts to cache as much data from disks as possible in otherwise-free memory; this provides many speed advantages. It will also try to organise device access in the most efficient ways possible; for example trying to order disk-access to ensure data stored physically close together is retrieved together, even if the requests did not arrive in sequential order. Further, many devices are of a more generic class such as USB or SCSI devices which provide their own abstraction layers to write to. Thus, rather than writing directly to devices, file systems will go through these many layers. Understanding the kernel is to understand how these many APIs interrelate and coexist.

 

**The Shell**

The shell is the gateway to interacting with the operating system. Be it bash, zsh, csh or any of the many other shells, they all fundamentally have only one major task — to allow you to execute programs.

 

But shells do much more than allow you to simply execute a program. They have powerful abilities to redirect files, allow you to execute multiple programs simultaneously and script complete programs.

 

**Implementing pipe**

If a process reads an empty pipe, it will by default *block* or be put into hibernation until there is some data available. Thus two processes may use a pipe to communicate that some action has been taken just by writing a byte of data; rather than the actual data being important, the mere presence of *any* data in the pipe can signal a message. 