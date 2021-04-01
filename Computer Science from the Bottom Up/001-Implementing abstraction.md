The name of the function is a pointer; therefore there is no need to take the address of the function (i.e. &say_hello_fn).

 

Starting with descriptors like this is usually the easiest way to begin understanding the various layers of kernel code.

 

Libraries have two roles which illustrate abstraction.

- Allow programmers to      reuse commonly accessed code.
- Act as a *black      box* implementing      functionality for the programmer.

The standard library of a UNIX platform is generically referred to as libc. It provides the basic interface to the system: fundamental calls such as read(), write() and printf(). This API is described in its entirety by a specification called POSIX.