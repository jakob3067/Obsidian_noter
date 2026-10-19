


Overall:
Have Task diagram, state machine and code


Questions about queues, semaphores, mutexes, deadlocks, etc. can easily arise no matter the question area drawn.

* Queues
* Semaphores
* Mutex
* Deadlock


Drawn numbers

1. State machines, Cortex M4, bit manipulation, build process

2. RTCS, concept of tasks, task diagrams, debugging

3. RTOS, FreeRTOS, Preemption, Assembler, reentrancy

4. Final Assignment


# For all exams

## Queues

Queues & Queue objects data structure

### What is a queue?

A **FIFO** (First In, First Out) data structure used to pass data between tasks or between an ISR and a task safely.

Items enter at the back, leave from the front. Think of a printer job queue.

### Queue object

In FreeRTOS a queue is created and represented as a handle:

QueueHandle_t xQueue;
xQueue = xQueueCreate(5, sizeof(int));

// Send (from task)
xQueueSend(xQueue, &val, portMAX_DELAY);

// Receive (blocks until item ready)
xQueueReceive(xQueue, &val, portMAX_DELAY);

The queue _copies_ data, so the sender's variable can be reused immediately.

### Key properties

- Fixed depth (length) set at creation
- Fixed item size set at creation
- Thread-safe — the RTOS handles critical sections internally
- Sending to a full queue blocks (or returns error with timeout 0)
- ISR variants: `xQueueSendFromISR`
## Semaphores

### Concept

A semaphore is a signalling mechanism. It has an integer count. Tasks **Take** (decrement) and **Give** (increment) it.

- **Binary semaphore** — count 0 or 1. Used for task notification / ISR→task sync.
- **Counting semaphore** — count 0…N. Used to track resource availability.

### FreeRTOS example

SemaphoreHandle_t xSem;
xSem = xSemaphoreCreateBinary();

// ISR gives, task takes
void ISR_Handler() {
  xSemaphoreGiveFromISR(xSem, &woken);
}

void vTask(void *p) {
  xSemaphoreTake(xSem, portMAX_DELAY);
  // do work after signal
}

### vs Queue?

Semaphore = signal only (no data payload). Queue = signal + data. Use a semaphore when you just need "did event happen?" and a queue when you also need the event's data. Counting semaphore can replace a queue of flags, but cannot carry data values.


## Mutex

### Purpose

A **Mut**ual **Ex**clusion semaphore. Protects a shared resource so only one task accesses it at a time.

Rule: the task that _takes_ the mutex must be the one that _gives_ it back.

### FreeRTOS example

SemaphoreHandle_t xMutex;
xMutex = xSemaphoreCreateMutex();

void vTask(void *p) {
  xSemaphoreTake(xMutex, portMAX_DELAY);
  // --- critical section ---
  sharedResource++;
  // -----------------------
  xSemaphoreGive(xMutex);
}

### Priority inheritance

FreeRTOS mutexes include **priority inheritance**: if a low-priority task holds a mutex that a high-priority task is waiting for, the low-priority task temporarily inherits the higher priority to finish faster.

Binary semaphores do NOT have priority inheritance — prefer mutex for resource protection.
## Deadlock
### Definition

Two or more tasks are each waiting for a resource held by the other — neither can proceed.

// Task A holds M1, wants M2
// Task B holds M2, wants M1
// → both block forever

### Four necessary conditions

- **Mutual exclusion** — resource can't be shared
- **Hold and wait** — task holds one, waits for another
- **No preemption** — resource not forcibly taken
- **Circular wait** — cycle of dependencies

All four must be present for deadlock. Break any one to prevent it.

### Prevention strategies

- Always acquire mutexes in the **same order** across all tasks
- Use **timeouts** instead of `portMAX_DELAY`
- Use a single mutex to guard multiple resources together
- Detect via watchdog timers in practice




##  1. State machines, Cortex M4, bit manipulation, build process

### State machines

Finite State Machines
Set of states triggered by events and inputs:

- States — what the system is doing now
- Transitions — conditions that change state
- Actions — outputs on entry/exit/transition'

##### *Moore*/*Mealy*
**Moore** - Output is only depended on state

**Mealy** - Output is dependent on input and state, meaning requires less states in a diagram than Moore


Implemented using state variable and condition statements (if, switch)

### Cortex-M4

ARM architecture:
RISC (reduced instruction set computer):
Usally for smartphones
**Pros**
Runs one instruction per cycle
Performance is better because of simplified instruction set
less space on chip
Reduced cost
**cons**
Performance off chip is varied by the code executed


**CISC**
Used for every PC
more complex

#### Registers
* A processor register holds small set of data that are part of computer processor
* ragister holds instruction, storage address or any data (bit sequence)
* Instruction may specify register as part of instruction

#### Interrupts
* An interrupt is a signal to the processor indicating a event that needs to run
* An interrupt sets request the processer to suspend activities, saves its state and executing interupt event
* After interrupt process resumes unless a fatal error

#### Counters/Timers
* Meaure elapse time or gets time of event
* Trigger interupt when time reach 0

### Bit manipulations
![[Pasted image 20260602192007.png]]

#### Logic function
A variable can be 1 or 0
NOT function:
![[Pasted image 20260602191651.png]]
OR function:
![[Pasted image 20260602191716.png]]
AND function:
![[Pasted image 20260602191730.png]]
XOR function:
![[Pasted image 20260602191748.png]]

#### Operations in C
![[Pasted image 20260603121122.png]]

**Logical vs bitwise**
• Logical operators operate on bytes and words 
• An expression is true if it is different from 0 
• An expression is false if it is equal to 0 
• The outcome of these operations are 0 or 1

**Bitwise operators** perform logical functions by comparing bits one by one

![[Pasted image 20260603121340.png]]

#### Numeric notation
![[Pasted image 20260603120927.png]]

**Example**
![[Pasted image 20260603121038.png]]

#### Build process
• Hardware specific 

• Compiling on PC but for TIVA controller – cross-compiler 

• Handled by the integrated development environment (IDE – Code Composer Studio) 

• You don’t have to worry about it unless something goes wrong… 

• We are using the IDE and not MAKE, but you can if you like it more

![[Pasted image 20260603121437.png]]

**PreProcess**
* Handles preprocessor directives in your code (starting with #) 
*  #include – copies header files into the source code 
*  #define – replaces the definition with the defined values 
*  #ifndef – if not defined yet, then include otherwise don’t  
* Removes comments 
*  Combines split lines 
* Passes expanded code to compiler

**Compiler**
Human readable code into machine code

Outputs object files
Non executable

**Linker**
* Links the object files together 

* Some internal variable and function references have not yet been resolved

* Resolves all unresolved symbols
* Looks for references in static libaries
* Relocatable output - no memory addresses assigned to code

**Locator**
* Transforms relocated program into executable binary image
* Specic addresses for each code line
* On a PC location is taken care of by the operating system, but not on embedded processors
* somtimes part of linker

## 2. RTCS, concept of tasks, task diagrams, debugging
RTCS & Concept of tasks Exam 2

### RTCS — Real-Time Computing System

A system that must respond to events within a guaranteed time bound (deadline). Two types:

- **Hard real-time** — missing a deadline = system failure (airbag ECU)
- **Soft real-time** — missing a deadline = degraded performance (video stream)

Determinism is the key property — worst-case execution time (WCET) must be known.

### Concept of tasks

A **task** (or thread) is an independent unit of execution with its own:

- Stack
- Program counter
- Priority level
- State (Running / Ready / Blocked / Suspended)

void vMyTask(void *pvParam) {
  for (;;) {
    // task body
    vTaskDelay(pdMS_TO_TICKS(100));
  }
}

### Task states

- **Running** — currently executing on the CPU
- **Ready** — runnable, waiting for CPU
- **Blocked** — waiting for event/time/resource
- **Suspended** — explicitly paused with `vTaskSuspend()`

Only one task runs at a time on a single-core MCU. The scheduler picks which.

Task diagrams Exam 2

### Types you should know

- **State transition diagram** — circles = states, arrows = transitions (Running/Ready/Blocked/Suspended)
- **Timing diagram** — horizontal time axis, shows when each task is running vs blocked
- **Task dependency diagram** — shows which tasks communicate via queues/semaphores

### Reading a timing diagram

- High bar = task is executing (Running)
- Low bar = task is blocked or preempted
- Tick marks = RTOS tick interrupts
- Preemption shows as abrupt switch to higher-priority task

On timing diagrams, a task that's ready but not running is being preempted — it's not blocked.

Debugging embedded systems Exam 2

### Hardware debug (JTAG / SWD)

- SWD (Serial Wire Debug) — 2-wire protocol used on Cortex-M
- Allows breakpoints, single-step, register/memory inspection
- Probe: ST-Link, J-Link, CMSIS-DAP
- IDE: GDB + OpenOCD or Keil uVision

### RTOS-aware debugging

- View task list — name, state, stack high-water mark
- Stack overflow detection: `configCHECK_FOR_STACK_OVERFLOW`
- Trace tools: Percepio Tracealyzer, Segger SystemView
- Printf via SWO/ITM or UART (careful in ISRs)

Stack high-water mark tells you how close you came to overflow — size stacks with margin.

### Common bugs

- Stack overflow → corrupted data or HardFault
- Race condition → non-deterministic behaviour
- Priority inversion → high-priority task starved
- Missed deadlines → watchdog reset
- ISR too long → other ISRs delayed



## 3. RTOS, FreeRTOS, Preemption, Assembler, reentrancy






## 4. Final Assignment

Intertask communication


