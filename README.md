# Pintos Project1: Threads
The functionality of the given minimally functional thread system is extended, with regard to the synchronization problems.

## Requirements

### Alarm Clock
Reimplement timer_sleep(), defined in devices/timer.c. Although a working implementation is provided, it "busy waits," that is, it spins in a loop checking the current time and calling thread_yield() until enough time has gone by. Reimplement it to avoid busy waiting.
- **Function**
```C
void timer_sleep (int64_t ticks)
```
Suspends execution of the calling thread until time has advanced by at least x timer ticks. Unless the system is otherwise idle, the thread need not wake up after exactly x ticks. Just put it on the ready queue after they have waited for the right amount of time.
timer_sleep() is useful for threads that operate in real-time, e.g. for blinking the cursor once per second.

The argument to timer_sleep() is expressed in timer ticks, not in milliseconds or any another unit. There are TIMER_FREQ timer ticks per second, where TIMER_FREQ is a macro defined in devices/timer.h. The default value is 100. We don't recommend changing this value, because any change is likely to cause many of the tests to fail.

### Priority Scheduling
Implement priority scheduling in Pintos. When a thread is added to the ready list that has a higher priority than the currently running thread, the current thread should immediately yield the processor to the new thread. Similarly, when threads are waiting for a lock, semaphore, or condition variable, the highest priority waiting thread should be awakened first. A thread may raise or lower its own priority at any time.
- **Function**
```C
void thread_set_priority (int new_priority)
```
Sets the current thread's priority to new_priority. If the current thread no longer has the highest priority, yields.
```C
int thread_get_priority (void)
```
Returns the current thread's priority. In the presence of priority donation, returns the higher (donated) priority.

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
