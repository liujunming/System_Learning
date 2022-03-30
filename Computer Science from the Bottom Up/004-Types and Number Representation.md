## C Standards

Officially this standard is known as ISO/IEC 9899:1999(E), but is more commonly referred to by its shortened name *C99*.

 

It is also important to note what the C standards does *not* define. Most importantly the standard needs to be appropriate for every architecture, both present and future. Consequently it takes care *not* to define areas that are architecture dependent. **The "glue" between the C standard and the underlying architecture is the Application Binary Interface (or ABI)**.In several places the standard will mention that a particular operation or construct has an unspecified or implementation dependent result. Obviously the programmer can not depend on these outcomes if they are to write portable code.

 

### GNU C

 

The GNU C Compiler, more commonly referred to as gcc, almost completely implements the C99 standard. However it also implements a range of extensions to the standard which programmers will often use to gain extra functionality, at the expense of portability to another compiler.

 

## Types

 

The C99 standard purposely only mentions the *smallest* possible size of each of the types defined for C. This is because across different processor architectures and operating systems the best size for types can be wildly different.



To be completely safe programmers need to never assume the size of any of their variables, however a functioning system obviously needs agreements on what sizes types are going to be used in the system. Each architecture and operating system conforms to an *Application Binary Interface* or *ABI*. The ABI for a system fills in the details between the C standard and the requirements of the underlying hardware and operating system. An ABI is written for a specific processor and operating system combination.

![image](https://user-images.githubusercontent.com/11829057/160825460-35416cb9-d8dd-4388-a32c-5455277843f5.png)




You can see that in the LP64 (long-pointer 64) model long values are defined to be 64 bits wide. 

The LP64 model is widely used on UNIX systems.

 

### Type qualifiers

 

Qualifiers are all intended to pass extra information about how the variable will be used to the compiler. This means two things; the compiler can check if you are violating your own rules (e.g. writing to a const value) and it can make optimizations based upon the extra knowledge.

 

### Standard Types

 

C99 realises that all these rules, sizes and portability concerns can become very confusing very quickly. To help, it provides a series of special types which can specify the exact properties of a variable. These are defined in <stdint.h> and have the form qtypes_t where q is a qualifier, type is the base type, s is the width in bits and _t is an extension so you know you are using the C99 defined types.

So for example uint8_t is an unsigned integer exactly 8 bits wide. 
