# Oppgave3.22-module3

Oppgavetekst:
In Exercise 3.21, the child process must output the sequence of numbersgenerated from the algorithm specified by the Collatz conjecture because the par-ent and child have their own copies of the data. Another approach to designingthis program is to establish a shared-memory object between the parent and childprocesses. This technique allows the child to write the contents of the sequence tothe shared-memory object. The parent can then output the sequence when thechild completes. Because the memory is shared, any changes the child makes willbe reflected in the parent process as well. Mariam 

This program will be structured using POSIX shared memory as de-scribed in Section 3.5.1. The parent process will progress through the fol-lowing steps: 

1. Establish the shared-memory object (shm_open(),ftruncate(),and mmap()). 

2. Create the child process and wait for it to terminate. 

3. Output the contents of shared memory. 

4. Remove the shared-memory object. 

One area of concern with cooperating processes involves synchronizationissues. In this exercise, the parent and child processes must be coordinat-ed so that the parent does not output the sequence until the child finishesexecution. These two processes will be synchronized using the wait()system call: the parent process will invoke wait(), which will suspendit until the child process exits. 

example: 
input: 35 
output is: 35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1 
