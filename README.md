# Arm-Architecture

## Aarch64 
- 64 bits
- v8.0 ( onwards)
- It is used in Mobile Chipset, M1 in laptop
- It was introduced in 2011. It also provides the backward compatibility as Aarch32


**Qualcomm X Elite**  `( This is a core) ` : This one is based on ARMv8.0 Cortex-ASeries
 
Both for Desktop and Data Center

**Microsoft Insight** : ARM cortex-A based server 

Used in Azure

## ELx
- Previously in early 2000, only chip makers wrote the code.
- Each ELx, has its address Translation.
- **EL0 Applications** : User Process created using Linux Commands, `cat, ls, pwd`


## Hypervisor
- It saves forms the Foundation of Cloud Computing
- It saves from attackting all the website

![Screenshot from 2023-12-20 08-21-21](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/7ac0b605-e4e0-4fe3-8ce6-5d646e47c0fe)

- EL1 switches the context among multiple processes
- EL2 switches the context among mulitple HLOS
- EL3 switches the context between 2 worlds i.e. NS & S.
- **ELx limits your ISA access**
- **S (`trustzone`) & NS limit your hardware access**
- You can't even take the Screenshot of Amazon Prime or Netflix video as there are present in Secure Memory area
- We keep sensitive data in S EL0 as chip manufactor does not know how many such data like ( fringer print sensor ) will be there. So EL3 has limited memory with limited feature.
  
![Screenshot from 2023-12-20 08-41-36](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/8a4bcafc-4419-45f1-a3f5-f6264c8ab68c)


![Screenshot from 2023-12-19 23-10-20](https://github.com/PranabNandy/Arm-Architecture/assets/34576104/47158bac-0917-429d-ae89-913177450b67)
