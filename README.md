# Arm-Architecture

## Aarch64 🔑
- 64 bits
- v8.0 ( onwards)
- It is used in Mobile Chipset, M1 in laptop
- It was introduced in 2011. It also provides the backward compatibility as Aarch32


**Qualcomm X Elite**  `( This is a core) ` : This one is based on ARMv8.0 Cortex-A Series
 
Both for Desktop and Data Center

**Microsoft Insight** : ARM cortex-A based server 

Used in Azure

## ELx 🛠
- Previously in early 2000, only chip makers wrote the code.
- Each ELx, has its address Translation.
- **EL0 Applications** : User Process created using Linux Commands, `cat, ls, pwd` 💣


## Hypervisor 🏹
- It saves forms the Foundation of Cloud Computing
- It saves from attackting all the website

![Screenshot from 2023-12-20 08-21-21](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/7ac0b605-e4e0-4fe3-8ce6-5d646e47c0fe)

- EL1 switches the context among multiple processes
- EL2 switches the context among mulitple HLOS
- EL3 switches the context between 2 worlds i.e. NS & S.
- 💠 **ELx limits your ISA access** 📡 
- 💠 **S (`trustzone`) & NS limit your hardware access** 🔬 
- 🟢 You can't even take the Screenshot of Amazon Prime or Netflix video as there are present in Secure Memory area 
- 🟢 We keep sensitive data in S EL0 as chip manufactor does not know how many such data like ( fringer print sensor ) will be there. So EL3 has limited memory with limited feature.  
- 🧷 EL3 -- `vendor-specific` code 
- 🧷 EL1/ EL0 - `OEM specific` code -- Not high features -- only secure apps 
  
![Screenshot from 2023-12-20 08-41-36](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/8a4bcafc-4419-45f1-a3f5-f6264c8ab68c)


![Screenshot from 2023-12-19 23-10-20](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/47158bac-0917-429d-ae89-913177450b67)


## Aarch64
**Programmers Model**

- 💉 Exception Model ( IRQ, FIQ)
- 💉 Memory Model
- 💉 Debug Model
- 💉 ISA

**Peripherals are also important** 
- MMU, GIC, Timers, Caches, Synchronization, Interconnect ( Coherent{AXI,ACE} & Non-coherent )

**3 Important Documents of ARM**

- ARM Cortex A Reference Manual { It explains about `Architecture`}
- ARM A-55( A-78) TRM { It explains about `micro architecture` i.e. how the core should behave }
- ARM A-Series PG ( Programmers Guide) { It contains how to write code as a Programmer }


![Screenshot from 2023-12-21 06-27-24](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/d3926d78-f2e3-4022-bdbf-f9605feaa62d)

### Programmers Guide 😃

- For the SW doc
- Most of the part is generic
- ARM allows OEM to have their own instructions
  - Need to change to compilers to support new instructions
  - Qualcomm X Elite
  - Apple M1        ✅ These are micro-architecture

- Here in Chapter 3, they define what they are, but not why they are

### Exception Model 🔱
- 💊 Exception Level : EL0, EL1, EL2, EL3
- 💊 Exception States : S, NS
- 💊 Execution Mode : 64 bits (Aarch64), 32 bits( Aarch32)

All these are controlled by registers. Some special instruction which works on Special Registers to govern the flow. These all defined the processor state. 

Due to hypervisor, we have IPA( Intermediate PA)

***[CPU]*** `---- VA---->` ***[HYP]*** `----IPA--->` ***[MMU]*** `---- PA--->`

🔍 We enforce the out-of-order execution behavior based on barrier { `for critical sections` }

**Bus Protocol & Cache Coherent Interconnect**
- ACE, AXI

💡 There are 2 types of cluster
- Homo-geneious cluster
- Hetero-geneious cluster { Based on big.Little Technology }

🖌 Debug
- Pause the CPU
- go and check the different registers and memory

📝 Fast Model
- Software Block Model { It includes ETM, CTI }
