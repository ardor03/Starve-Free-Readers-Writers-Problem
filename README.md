# Starve Free Readers-Writers Problem

The Starve-Free Readers Writers Problem is a synchronization problem where multiple threads compete for access to a shared resource. In this particular problem, there are multiple reader threads and writer threads that want to access a shared resource, such as a file or a database.

The problem arises when multiple threads attempt to access the shared resource simultaneously, leading to issues such as data corruption, race conditions, and thread starvation. The goal of the Starve-Free Readers Writers Problem is to ensure that all threads are able to access the shared resource fairly and without starvation.

# Solution

The pseudo code in readersFirst.txt is the classical solution to the Readers-Writers problem. In it the synchronization is achieved using semaphore wrt, mutex and a variable read. The read variable represents the number of readers currently accessing the critical section. wrt is used to maintain access to the critical section. The mutex is used to provide write-access to the read variable. Any reader that enters or exits the critical section has to acquire this mutex.

As you can see the problem with the above implementation is that the writers may starve while waiting for access to the critical section. This would happen if readers keep coming one after other, thus the writers would never get a chance to acquire wrt, thus being starved.

The starve-free solution starveFreeSolution.txt describes how the issue can be solved.

The problem if starvation is tackled by using another semaphore(entry). This is first required to be obained before anyone (the reader or the writer) accesses the wrt or before anyone (any reader) enters the critcal section directly. This solves the problem of starvation as if readers keep coming one after another, then this won't starve the writers as it used to above. Here, if a writer comes in between some readers, and even if some readers are still present in the critical section, the next reader if it comes after a writer, the writer would have already acquired the entry and thus the reader can't acquire it. Now the writer can enter the critical section and the same process would repeat.

This solution ensures that all threads are able to access the shared resource fairly and without starvation.

# Usage

To use this solution in your program, you can implement the logic described above in your thread synchronization code.

# Conclusion

The Starve-Free Readers Writers Problem is a common synchronization problem that arises when multiple threads compete for access to a shared resource. By using the above solution, it is possible to ensure that all threads are able to access the resource fairly and without starvation.
