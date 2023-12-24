# 🚦 Exception Level

- Usage Fault may happen during Execution by Cortex M4
- Final Loc of Fault/Interrupt Handler = Base Addr(VTOR) + Index of Usage Fault in Vector Table
- Here Bootloader development does not relies on Application & Application development does not relies on Bootloader
- Default value of **VTOR** is decided by **Boot ROM**
- Generally `VTOR-->0x0` } but is not always true

 Vector Table | 🍔 | 
--- | --- | 
Application Vector Table | VTOR-->X , Diff loc for usage fault | 
Bootloader Vector Table |  VTOR-->Y , Diff loc for usage fault |  

🍎 You generally place the VTOR at the place where you want to execute the code. 

Like for STM32, at the start of Flash memory
![Screenshot from 2023-12-22 22-36-07](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/40676b5e-4ae5-43f6-84d7-7eb2ea652716)

![Screenshot from 2023-12-22 22-36-45](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/f2b294bd-f578-4cf8-9b16-e5c90d1f68b2)

🍟 **ARM Core** look up vector table & read 2 words from vector table.
- PC --> sets to Reset Handler
- this PC address comes from Vector Table
- Till this point, whatever control flow the hardware has, now completed
- Now the control flow is in the hand of programmer
- All the computation / Applications run from the reset handler

Mode | 🍔 | 
--- | --- | 
Thread Mode | It is more restricted ( PSP - Process SP ) | 
Handler Mode | High Priority ( MSP - Main SP ) | 

### 🍭 Reset handler would be executing in thread mode


- We can set breakpoint into reset vector --> to check the status register of ARM
- VTOR will be set to some address by Designer/ BootRom writers
- As soon as, cpu is power up. 2 words will be fetched.



### 🚨 How CPU knows what to access?
- 32 bits CPU
- You can use 2^(32) combinations
- 4 GB of combinations out of 32 signals
- 🪂 **CPU Designer**
  - Whenever they want to have certain signals will be manipulated by users
  - They provide an interface called Registers
![Screenshot from 2023-12-23 12-33-28](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/c124df6e-e516-445a-937e-0756fccc17aa)

### 🌏 This example also called memory mapped IO
- Here Each interface is deciding based on the MSB value
- Memory is nothing but a signal trapped in Flip Flop
- 🏛 **ARM** comes up with the a Memory Map
  - If you respect this memory map then system will run smoothly
  - Designer should follow this map i.e should respect this map
     
![Screenshot from 2023-12-22 22-37-12](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/4c7df70a-67a9-4586-b772-78726ad5cb0e)

![Screenshot from 2023-12-22 22-37-29](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/3315dab4-3fef-4e2e-8b0a-721ecf687cae)

### ⌛ Private Peripheral Bus
- **ARM RTL** would have NVIC, Systick, MPU, SCB
- **MPU** related to external device and external RAM
- SRAM = Read & Write Data Register
- 🛰 ARM specific Address
- 🚀 Vendor Specific Address (`Qualcomm, Broadcomm`)
-  **VTOR** : Vector Table Address Register

### 🔥 Handler 💧
- It is nothing but a function without any parameter & return value
- vendor will tell you which slots stands for which peripheral
- In VTOR table, size of each entry is 4B
- **31th IRQ** = `(16(fixed one)*4 + 31*4) + Base of VTOR`
![Screenshot from 2023-12-22 22-37-55](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/0ed0bbae-439e-4e42-b721-a9d16a138a06)

### ⛱ Timers
- Timers --- generates IRQ --> NVIC --- Sends 31 th IRQ number---> CPU
- **CPU** 🌪
  - CPU might execute PSP (process SP)
  - will switch to MSP (main SP)
  - Then calculate the new address of the Timer Handler
  - Then Pushes the 8 register in MSP
  - Rest of the register will be taken by Handler
 
#### Return address & LR 🧶
- Return address is usefull for function inside a function
- [ MSP | PSP ]
-  r13(SP) : one of these

### 🔊 Reset Handler
- Reset loads the system to known state.
- It sets all the register and memory to a initial value
- This helps to ensure a **clean and predictable state** for the processor **to start from**
- Other exceptions, on the other hand may leave the process in an unknown state or corrupted condition
- Reset Handler sets the processor in Known state
- It executes in thead mode
![Screenshot from 2023-12-22 22-38-19](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/2381a24b-e9f5-4096-849b-4c24e674fc0b)


# 🇨🇦 🇦🇺 🇨🇳 🇮🇳 🇯🇵

### GCC 🐶
- It has its own **assembler (as)**, **linker (ld)** 
- It internally usage these tools
- 🕸 In application, main() is the the first function
- 🕸 In Embedded, first `start up` function calls the `main()` or any other funciton
- In abstraction, program has `.txt, .bss, .data` section in the memory
- 🍀 Special Note: **.S** has gone through Preprocessor and **.s** does not go through the preprocessing stage
- 🍉 **.o :** relocatable object file
- 🫐 linker : generates elf
![Screenshot from 2023-12-24 19-08-42](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/f784e51c-8dd4-4b76-a5cd-8da00e09ee6b)

### startup file 🥗
- sets bss section to 0
- `.bin `= .txt, .data, `.bss`
  - `.bss`: start up program only take start addr and size during startup time, we just initialize to 0
- **`.a`** : collections of .o files
- **KEEP(*(.vector))** 🫖
  - retain even if there is no reference to it in the program
- **logs of linker:** map file 🧊
  - when there is a crash in the system due to some address
  - take that address & check in map file which variable it is
![Screenshot from 2023-12-24 19-13-21](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/a3ae4c6d-0493-4b46-b28e-f5e998ee042f)
![Screenshot from 2023-12-24 19-09-34](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/4044130b-e422-4c0f-a8dd-3deadeba4601)
![Screenshot from 2023-12-24 19-11-52](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/338ed803-39ac-4cf1-bf51-2f4653fc2ee7)

### map file 🏥
- **&_stack_top** : this value is coming from .map file i.e after linking
- **vector table** : It is a collections of void pointers
```
// this is how we can add any function to a particular section
__attibute(used,.section(.text))
void foo(void){
    // some code
}
```
- **flash**: It is byte writeable ⛩
  - 1 --> 0  easy
  - 0 --> 1 expensible process
```
.bss(NOLOAD)
{
// It means don't load it during loading time
// reset handler will take care of it
}
```
```
.data
{
// some code
} > ram AT >flash
```
- Initially, `.data` variables are available in **flash**
- Later in the code, when we modify it, it will copy all `.data` to **ram** & modify their value

