# Exception Level

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

#### 🍭 Reset handler would be executing in thread mode


- We can set breakpoint into reset vector --> to check the status register of ARM
- VTOR will be set to some address by Designer/ BootRom writers
- As soon as, cpu is power up. 2 words will be fetched.

![Screenshot from 2023-12-22 22-37-12](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/4c7df70a-67a9-4586-b772-78726ad5cb0e)

![Screenshot from 2023-12-22 22-37-29](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/3315dab4-3fef-4e2e-8b0a-721ecf687cae)

#### How CPU knows what to access?
- 32 bits CPU
- You can use 2^(32) combinations
- 4 GB of combinations out of 32 signals
- **CPU Designer**
- Whenever they want to have certain signals will be manipulated by users
- They provide interface called Registers
- 

