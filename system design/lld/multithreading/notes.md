- Program: A program is an executable file. (For ex. chroma.exe)

- Process: A process is an executing instance of a program. Every instance will have own memory, program counter, system resources.

- Thread: It is the smallest executable unit of a process. Threads are sub-tasks of processes.

- Cores in CPU: It is an individual processing unit inside your CPU - capable of executing instructions independently. Mini CPU inside CPU.

- One thread at a time per core(or more with hyper threading which is intelligent time slicing + resource sharing).

- Context switching is the process where the CPU stops executing one thread/process, save its state, and switches to another.

- When a context switch happens
    - The CPU saves the current thread's context
    - Loads the next thread's context
    - Resumes execution of new thread.

- Switching is managed by the thread scheduler
    - Takes time to save / load state.
    - Performance degradation due to high threads.

- Multithreading is the ability of a program to run multiple threads(independent) concurrently, either truly in parallel(multi cores) or via context switching(single core).
    - Each thread 
        - Runs independently.
        - Shares the same memory space.
        - Performs a specific task.

    - Why use?
        - Better performance.
        - Non blocking
        - Resource sharing
        - Scalability in backend services.

- Concurrency:
    - Means multiple tasks making progress over time, but not necessarily at the same exact time.
    - Can with one core.
    - Tasks appear to run at the same time.
    - Focus is on the structure, on how to do many things.

- Parallelism:
    - Means multiple tasks executing at the exact same time - on multiple cores.
    - Can work with multiple cores.
    - Tasks actually run at the same time.
    - Focus is on the execution, how to finish many things.

- Process
    - Independent program in execution
    - Has its own memory
    - Fully isolated
    - Communication is complex(IPC, sockets)
    - Overhead is heavy
    - One process crash doesn't affect others.
    - Example --> PostgreSQL

- Thread
    - Sub-unit of a process
    - Shares memory with other threads in the process.
    - Not isolated.
    - Easy (shared memory)
    - Overhead is light.
    - One thread crash may affect others.
    - Example --> Chroma tasks, Uber backend.

- Fault Tolerance:
    - It is the ability of the system to continue operating correctly, even when some of the components fail.
    - It detects, contains and recovers from failures without affecting user experience.
    - Read life --> A airplane.
    - Redundancy.
    - Graceful degradation
    - Self-headling
    - Error-containment

- Isolation:
    - It means keeping different components on tasks independently from each other so that actions or failures do not affect each other.
    - Design strategy to ensure that the components are sandboxed from each other.
    - Memory separation, failures containment.
    - Security boundaries, predicatable behaviour.