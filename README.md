# JNachos-Multiprogramming

Currently JNachos only supports running a single program at a time. The entire contents of that program’s address space
are loaded into main memory contiguously. The result is that physical address space and virtual address space are always
equal, and the OS does no conversion. This implies that only a single process can run (since both Process A and Process B
can’t have their 0th virtual page mapped to the same physical page.) You may work in pairs for this assignment, no groups
of three will be permitted.

Running Multiprogramming in JNachos:

User programs in JNachos are written in C language and compiled into the MIPS assembly language. The executable files can 
then be run on our emulated MIPS JNachos processor.Adding the following flag -x /..path../testfile should run one of
the user programs.
(Goal - To run multiple files or multiple user programs)

Description of Implementation:

1)I got the basic idea from the existing code(main.java) which is taking care of running a single user program only by calling
processTest() which implements voidFunctionPtr and call fork() which is passing a voidFunctionPtr to JNachos startProcess() 
function to run user program. It invokes call() to invoke the startProcess().Now this function has machine.run() which 
never returns.

2)The bottleneck in the code is to invoke startProcess() or simply machine.run() for each argument. However, this function 
never returns once invoked, and I need it multiple times for execution of each user program.

3) I cannot pass multiple arguments to it because, it never returns.so, for this, I have called the startProcess() itself 
separately for each argument with separate argument in newly created class(Multiprogramme.java).

4)The first thing is to separate the two filenames so that we can pass it further as anargument to further functions. So, I 
have taken the arguments(args) one by one by using for loop and storing it as string(fname).

5)Since, I need to separate two files, I need to find the location of “,” in an argument forthat I am checking using an if 
condition, and if it encounters comma, it will take the filename till (fname.length()-1) in order to leave comma.

6)Then I am strong this string in name so that I will pass it as an argument now.

7)Once we get first filename, I need to create a process for it, so I have called NachosProcess() function.

8)the next step is call fork() which is taking the voidFunctionPtr to Jnachos startProcess()and the object(file argument) 
itself.

9)This will go to newly created class which is implementing voidFunctionPtr where we are calling call() to invoke the start 
process.

I have given comments in the code for more details.
















   
