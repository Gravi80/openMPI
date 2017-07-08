**Setup**
=========
###### Mac
    $ brew install open-mpi
    $ env MPICC=/usr/local/bin/mpicc pip install mpi4py

**Check Version Installed**
--
 `$ python`
	>>> from mpi4py import MPI
	>>> MPI.Get_version()
			Gives the version of the standard to which the MPI library conforms; 					 major/minor versions
OR
`$ ompi_info --version`				   																								http://manpages.ubuntu.com/manpages/precise/man1/ompi_info.1.html


##**Commandline Tools**
	$ mpicc   
> mpicc is a convenience wrappers for the underlying C compiler. It passes its arguments to the underlying C compiler along with the -I, -L and -l options required by Open MPI programs.
**mpicc -showme** gives the full list of options that the wrapper passes on to the backend compiler.

> Open MPI is comprised of three software layers: 
1. OPAL (Open Portable Access Layer)
2. ORTE (Open Run-Time Environment)
3. OMPI (Open MPI). 
There are wrapper compilers for each layer; each layer's wrapper only links in the libraries relevant for that layer. Specifically, each layer provides the following wrapper compilers:
- OPAL
		opalcc
		opalc++
- ORTE
		ortecc
		ortec++
- OMPI
		mpicc 
		mpic++ 
		mpicxx 
		mpiCC (only on systems with case-senstive file systems)
		mpifort (and its legacy/deprecated names mpif77 and mpif90). 

Note that mpic++, mpicxx, and mpiCC all invoke the same underlying C++ compiler with the same options. 

	$ mpirun
	$ mpiexec
	$ orterun
mpirun, mpiexec, and orterun are all synonyms for each other. Using any of the names will produce the same behavior.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; mpirun
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; --------
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;mpirun uses the Open Run-Time Environment (ORTE) to launch jobs.  When you issue the mpirun command, you specify the name of the hostfile or host list on the command line; otherwise, mpirun executes all the copies of the program on the local host, in round-robin sequence by CPU slot. 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MPI does the initial scheduling, but for more than one process per node, or just in general (since there are a number of other processes running in the background too),the Linux kernel scheduler takes over.


##**CPU Information**
https://www.cyberciti.biz/faq/lscpu-command-find-out-cpu-architecture-information/
**Linux :**
		$ cat /proc/cpuinfo
		$ grep flags /proc/cpuinfo
		$ lscpu
**OSX :**
Menu bar > Apple > About This Mac > System Report > Hardware
**Finding Processor Details & CPU Speed**
`$ sysctl -n machdep.cpu.brand_string`
	Chip Brand — Processor Type and Chip Model — CPU Speed
**CPU Processor Details**
` $ system_profiler | grep Processor`
**Logical Cores**
`$ sysctl hw.logicalcpu`
Hyperthreading technology makes each physical core appear as two logical cores. This lets each core handle two execution threads.
**Physical Cores**
`$ sysctl hw.logicalcpu`
*hw.physicalcpu* - The number of physical processors available in the current power management mode.
*hw.physicalcpu_max* - The maximum number of physical processors that could be available this boot.
*hw.logicalcpu* - The number of logical processors available in the current power management mode.
*hw.logicalcpu_max* - The maximum number of logical processors that could be available this boot.

> Cores process one thread of program code at a time (unless they are hyperthreaded, in which case they process two threads at a time).
The higher the clock speed, the faster the cores will be. Clock speed is measured in GHz (gigahertz), a higher number means a faster clock speed.
If one CPU has a bit width of 32 bits and a speed of 3.93 GHz, that means it can process almost (4,000,000,000)4 billion units of 32 bits of data per second.