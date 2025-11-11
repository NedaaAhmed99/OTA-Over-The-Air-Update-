# OTA (Over-The-Air) Update Framework

This framework describes the process for performing OTA (Over-The-Air) software updates for embedded systems, including Linux-based IVI devices and QNX virtual machines.

---

## Components

### **PC**
- Acts as the source of software update files.  
- Provides update files for **Linux Kernel**, **U-Boot**, and **QT Applications**.  
- Sends files to **QNX** using **FTP (File Transfer Protocol)**.  

### **VM-QNX**
- Receives update files from **PC** via **FTP**.  
- Performs **CRC integrity check** to ensure data validity.  
- Sends verified data to **Linux RPI2** using **V-SOME/IP protocol**.  

### **Linux-RPI (Yocto)**
- Operates as the **In-Vehicle Infotainment (IVI)** system.  
- Receives the update package via **SOME/IP** from **QNX**.  
- Applies the software update (**OTA process**).  

---

## Workflow

1. **PC → VM-QNX:** Update files are sent via FTP.  
2. **VM-QNX:** Performs CRC validation to ensure file integrity.  
3. **VM-QNX → Linux-RPI:** Verified files are sent via V-SOME/IP.  
4. **Linux-RPI:** Receives the update package and applies the OTA update.  

---

## Summary Diagram 

PC ──FTP──▶ VM-QNX ──V-SOME/IP──▶ Linux-RPI (Yocto)
              │
          CRC Check 
