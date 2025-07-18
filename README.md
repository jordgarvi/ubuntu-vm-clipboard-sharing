# Ubuntu VM ↔ Windows Clipboard Sharing (VirtualBox)

This is a step-by-step guide to enable **copy & paste** between an Ubuntu virtual machine and a Windows host using VirtualBox. This improves productivity for IT labs, note taking, and scripting.

---

## 🖥️ Environment

- **Host OS**: Windows 11 (24H2)  
- **Guest OS**: Ubuntu 22.04 LTS  
- **Virtualization Platform**: VirtualBox 7.1+

---

## 🎯 Objective

Enable **bidirectional clipboard sharing**, so you can:

- ✅ Copy text from Ubuntu → paste into Windows  
- ✅ Copy text from Windows → paste into Ubuntu

---

## 🛠️ Step-by-Step Instructions

### Step 1: Install Required Packages in Ubuntu

This installs kernel headers and tools needed to compile VirtualBox Guest Additions.

In the Ubuntu terminal, run:

```bash
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
```

![Terminal after installing dependencies](./images/01-packages-installed.png)

---