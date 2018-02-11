# Linux from scratch

The aim of this project is to build a basic linux ditro using a compiler, linker and shell from an existing linux system, in this case, Ubuntu 16.04.

Firstly, we have to create a partition, where we will build the system. Then we'll create a file system on it and mount it.

For convenience, add an environment variable LFS containing the directory where the linux system would be built. This would make executing commands easier as you don't need to remember the exact directory.

Now, we need to install some packages to help build a basic linux system. Make a directory named 'sources' to download all the packages to one place.

We then use wget(with a [file](wget-list) containing the download URLs as an argument with --input-file) to download all the source packages.

After downloading the packages, make a new folder called tools to store all the temporary tools that will not be a part of the final LFS system. Create a /tools symlink on the host system which will point to the tools directory on the linux(new) partition. The created symlink enables the toolchain to be compiled so that it always refers to /tools, meaning that the compiler, assembler, and linker will work both when we are still using some tools from the host and when we are “chrooted” to the LFS partition.   

When logged in as user root, making a single mistake can damage or destroy a system. Therefore, we will create a new user in a new group using "useradd" and "groupadd" respectively.

After setting a password, giving the new user access to the /tools, we'll login as the new user using the terminal.
