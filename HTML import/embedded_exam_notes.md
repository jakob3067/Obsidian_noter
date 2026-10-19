## Embedded systems exam revision notes

All exams (common)

Exam 1

Exam 2

Exam 3

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

Semaphores synchronisation

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

Semaphore = signal only (no data payload). Queue = signal + data. Use a semaphore when you just need "did event happen?" and a queue when you also need the event's data.

Counting semaphore can replace a queue of flags, but cannot carry data values.

Mutex mutual exclusion

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

Deadlock hazard

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

State machines Exam 1

### FSM basics

A **Finite State Machine** models a system as a set of states with transitions triggered by events/inputs.

- States — what the system is doing now
- Transitions — conditions that change state
- Actions — outputs on entry/exit/transition

Moore machine: output depends on state only. Mealy machine: output depends on state + input.

### C implementation

typedef enum { IDLE, RUNNING, FAULT } State;
State state = IDLE;

void update(Event e) {
  switch (state) {
    case IDLE:
      if (e == START) state = RUNNING;
      break;
    case RUNNING:
      if (e == ERROR) state = FAULT;
      if (e == STOP)  state = IDLE;
      break;
    case FAULT:
      if (e == RESET) state = IDLE;
      break;
  }
}

Cortex-M4 Exam 1

### Key features

- 32-bit ARM core, Harvard-ish architecture
- Thumb-2 instruction set (mix of 16/32-bit)
- 16 general-purpose registers R0–R15
- R13 = SP (stack pointer), R14 = LR, R15 = PC
- FPU (single precision float)
- Nested Vectored Interrupt Controller (NVIC)
- SysTick timer — used by RTOS for tick interrupt

### Memory map regions

- `0x00000000` — Code (Flash)
- `0x20000000` — SRAM
- `0x40000000` — Peripherals
- `0xE0000000` — Private peripheral bus (NVIC, SysTick)

Peripheral registers are memory-mapped — accessed like normal variables via pointers.

### Exception/interrupt model

- Vector table at start of Flash — each entry is a handler address
- Priority levels 0 (highest) to 255 (lowest)
- Automatic context save (R0–R3, R12, LR, PC, xPSR) on entry
- Return via special EXC_RETURN value in LR

Bit manipulation Exam 1

### Core operations

uint32_t reg = GPIOA->ODR;

// Set bit 5
reg |=  (1U << 5);

// Clear bit 5
reg &= ~(1U << 5);

// Toggle bit 5
reg ^=  (1U << 5);

// Test bit 5
if (reg & (1U << 5)) { ... }

// Read field [7:4]
uint8_t field = (reg >> 4) & 0x0F;

### Bit masks — common patterns

- Set multiple bits: `reg |= 0x0F` (set lower nibble)
- Clear and set field: `reg = (reg & ~mask) | val`
- `1U` not `1` — prevents sign-extension on 32-bit shift

Always use unsigned types for bit operations to avoid undefined behaviour on signed shift.

### Peripheral register example (STM32)

// Enable GPIOA clock (RCC AHB1ENR bit 0)
RCC->AHB1ENR |= (1U << 0);

// Set PA5 as output (MODER bits [11:10] = 01)
GPIOA->MODER &= ~(3U << 10);
GPIOA->MODER |=  (1U << 10);

// Toggle PA5
GPIOA->ODR ^= (1U << 5);

Build process Exam 1

### Stages

- **Pre-processing** — expands `#include`, `#define`, macros → `.i` file
- **Compilation** — C → assembly → `.s` file
- **Assembly** — assembler → object file `.o`
- **Linking** — combines `.o` files + libraries → `.elf` / `.bin`
- **Locating** — linker script maps sections to addresses (Flash / SRAM)

### Linker script key sections

- `.text` — executable code (Flash)
- `.rodata` — read-only data / const (Flash)
- `.data` — initialised globals (copied Flash→SRAM at startup)
- `.bss` — uninitialised globals (zeroed in SRAM)
- `.stack` / `.heap` — runtime memory (SRAM)

### Cross-compilation toolchain

- `arm-none-eabi-gcc` — cross compiler
- `arm-none-eabi-ld` — linker
- `arm-none-eabi-objcopy` — ELF → binary/hex
- `arm-none-eabi-size` — section sizes
- `make` / `CMake` — build automation

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

RTOS & FreeRTOS Exam 3

### What an RTOS provides

- Scheduler (decides which task runs)
- Inter-task communication (queues, semaphores, mutexes, event groups)
- Timing services (`vTaskDelay`, `xTaskGetTickCount`)
- Memory management (`pvPortMalloc`)

### FreeRTOS specifics

- Open source, widely used on Cortex-M
- Config in `FreeRTOSConfig.h`
- Tick rate set by `configTICK_RATE_HZ`
- Heap schemes: heap_1 (no free) … heap_5 (fragmented RAM)
- Task priority: 0 = lowest, `configMAX_PRIORITIES-1` = highest

The idle task always runs when nothing else is ready — never starve it (keep priority 0).

### Scheduler algorithms

- **Preemptive** — highest ready task always runs (default FreeRTOS)
- **Cooperative** — task yields voluntarily
- **Round-robin** — equal-priority tasks share time in slices

With preemption on, any task can be interrupted at any tick — protect shared data with mutexes!

Preemption Exam 3

### How it works

At each RTOS tick (or when a higher-priority task becomes ready), the scheduler checks if the current task should continue.

- If a higher-priority task is ready → context switch occurs immediately
- Current task's registers saved to its TCB stack
- New task's registers restored

### Context switch

Saves: R0–R12, LR, PC, xPSR, (FPU registers if used)

Triggered by:

- SysTick ISR (time slice expiry)
- Task calling blocking API (`xQueueReceive` etc.)
- Higher-priority task unblocked from ISR

Assembler Exam 3

### ARM Thumb-2 essentials

; Load / Store
LDR R0, =0x20000000  ; load address
LDR R1, [R0]         ; load word from address
STR R1, [R0, #4]     ; store word at address+4

; Arithmetic
ADD R0, R1, R2       ; R0 = R1 + R2
SUB R0, R0, #1       ; R0 = R0 - 1
MUL R0, R1, R2       ; R0 = R1 * R2

; Branch
CMP R0, #0
BEQ done             ; branch if equal (zero flag)
B   loop             ; unconditional branch

; Stack
PUSH {R4-R7, LR}
POP  {R4-R7, PC}     ; return by popping into PC

### Calling convention (AAPCS)

- R0–R3: arguments / return value
- R4–R11: callee-saved (must preserve)
- R12 (IP): intra-procedure scratch
- R13 (SP): stack pointer
- R14 (LR): link register (return address)
- R15 (PC): program counter

If your function uses R4–R11, PUSH them at entry and POP at exit.

### Inline assembler in C (GCC)

// Disable interrupts
__asm volatile ("cpsid i");

// Enable interrupts
__asm volatile ("cpsie i");

// No-op / cycle waste
__asm volatile ("nop");

// Memory barrier
__asm volatile ("dsb");
__asm volatile ("isb");

Reentrancy Exam 3

### What is a reentrant function?

A function that can be safely called by multiple tasks (or interrupted and called again) simultaneously without corrupting results.

Reentrant functions use only local variables (stack-allocated), no static or global state.

### Non-reentrant example

// BAD — static variable shared
int counter(void) {
  static int count = 0;  // ← shared state!
  return ++count;
}

// GOOD — reentrant version
int counter(int *count) {
  return ++(*count);  // caller owns state
}

### Common non-reentrant pitfalls

- Static local variables
- Global variables written without mutex
- Non-reentrant library functions: `strtok`, `printf` (some implementations)
- Hardware registers accessed without critical section

Standard C `malloc` / `free` are NOT reentrant — use FreeRTOS `pvPortMalloc` in tasks.