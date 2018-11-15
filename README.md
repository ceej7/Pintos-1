# Pintos Project1: Threads
The functionality of the given minimally functional thread system is extended, with regard to the synchronization problems.

## Implements

### Alarm Clock
Reimplement timer_sleep(), defined in devices/timer.c. Although a working implementation is provided, it "busy waits," that is, it spins in a loop checking the current time and calling thread_yield() until enough time has gone by. Implement it to avoid busy waiting.
- **Function**
```C
void timer_sleep (int64_t ticks)
```

### Priority Scheduling
Implement priority scheduling in Pintos. When a thread is added to the ready list that has a higher priority than the currently running thread, the current thread should immediately yield the processor to the new thread. Similarly, when threads are waiting for a lock, semaphore, or condition variable, the highest priority waiting thread should be awakened first. A thread may raise or lower its own priority at any time.
- **Function**
```C
void thread_set_priority (int new_priority)

int thread_get_priority (void)
```

### Advanced Scheduler
Implement a multilevel feedback queue scheduler similar to the BSD scheduler to reduce the average response time for running jobs on your system.

## Build
First, cd into the threads directory. Then, issue the make command. This will create a build directory under threads, populate it with a Makefile and a few subdirectories, and then build the kernel inside.
```bash
./src/threads/make
```
## Testing
A script scores the output as "pass" or "fail" and writes the verdict to t.result.
```bash
./src/threads/make check
```

## Result
Tests: 27/27 pass

## Reference
Provide the [Pintos Gudie](https://web.stanford.edu/class/cs140/projects/pintos/pintos_2.html#SEC15):+1:
