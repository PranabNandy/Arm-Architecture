

## 🎃  ARM = Advance RISC Machine

🍡 RISC and CISC 
- Two different ideologies to design the ISA of process
- **ISA** : Agreement between software and Processor
  - It tells if software respect XYZ instruction, ABC operation will be performed by the processor
- RISC ---> MIPS/SPARC ---> came from partnership of IBM, Standford & Barkley
![Screenshot from 2023-12-21 07-59-34](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/afd12b05-5945-4abd-a3bd-b6d447764feb)


SW | 🍔 | 
--- | --- | 
ISA | Actual Contact | 
HW |        💻💻💻  | 


**A** : 
- Phone, server, Laptop

**R** : 
- Realtime
- determinism
- GIC ( Trap Mechanism)

**M** : 
- Little application
- Interrupt driver
- Simple State machine
- Vecorted Interrupt

**Cortex-X** :
- It introdues from v9.0. Smart Phone, sensor
![Screenshot from 2023-12-21 08-00-08](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/670f9846-2fe7-40a5-81c1-9cbf33a31c4d)



🎯 CISC : 
- Hardware breakdown the complexity
- So HW is complex

🥊 RISC : 
- Complexity of the instruction has reduced.
- Compiler breakdown the complexity
- HW is simple
- Leads to low power usuage
  
![Screenshot from 2023-12-21 07-52-06](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/59653804-271b-4689-8b7c-8030ed6bd0af)


🥎 No MMU, VA in Cortex R
  
🏉 **DSP/ SIMD** :
- Matrix Multiplication
- 1 32 bits register is performing operation for 8 bit each in 4 times.....
- 1 32 bits instr, carries 4 different info 8 bits each ( Single Instr but multiple data)
  
![Screenshot from 2023-12-21 07-56-48](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/0768c380-c95d-4561-bdb5-8a0fc162f3b1)
![Screenshot from 2023-12-21 08-00-31](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/760e7df2-073d-43d6-b2d6-61060d2484bf)


# Cortex-M (STM32F4XXXX) 🦀

- It is not just a CPU 😈
- v7.0 + single Precision FPU
- **M4F** : FPU capable
- 💥 NVIC : Nested Vectored Interrupt Controller
- 🧠 WIC : Wakeup Interrupt Controller
  - When CPU is in LPM, then it helps to wake up from the system if and only if new INT came to WIC block
- 🐳 ETM : Embedded Trace macro-sell
  - debug /trace instruction
- 🦠 JTAG : SWD ( Serial wire debugger in ARM)
- 🦋 MPU : Divide the memory into multiple priviledges
![Screenshot from 2023-12-21 08-06-11](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/6c1836f8-e13a-4606-b409-5b9f77556ac2)


  
