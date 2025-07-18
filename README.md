# Ubuntu VM ↔ Windows Clipboard Sharing (VirtualBox)

This is a step-by-step guide to enable **copy & paste** between an Ubuntu virtual machine and a Windows host using VirtualBox. This improves productivity for IT labs, note taking, and scripting.

---

## Environment

- **Host OS**: Windows 11 (24H2)  
- **Guest OS**: Ubuntu 22.04 LTS  
- **Virtualization Platform**: VirtualBox 7.1+

---

## Objective

Enable **bidirectional clipboard sharing**, so you can:

- ✅ Copy text from Ubuntu → paste into Windows  
- ✅ Copy text from Windows → paste into Ubuntu

---

## Step-by-Step Instructions

### Step 1: Install Required Packages in Ubuntu

This installs kernel headers and tools needed to compile VirtualBox Guest Additions.

In the Ubuntu terminal, run:

```bash
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
```

![Terminal after installing dependencies](./images/01-packages-installed.png)

---

### Step 2: Insert Guest Additions CD

In the **VirtualBox VM window**:

1. Click on `Devices → Insert Guest Additions CD image...`
2. Wait a few seconds for Ubuntu to detect and mount the disk
3. If it doesn’t auto-mount, mount it manually:

```bash
sudo mkdir /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom
```

📸 **Screenshot of manual mount:**  
![Mounted Guest Additions manually](./images/03-cd-mounted-terminal.png)


📸 **Screenshot of menu option:**  
![VirtualBox Devices menu showing CD option](./images/02-insert-guest-additions.png)

---

### Step 3: Verify Guest Additions Is Active

I attempted to run the Guest Additions installer manually:

```bash
sudo /mnt/cdrom/VBoxLinuxAdditions.run
```

However, it returned the following error:

```bash
sudo: /mnt/cdrom/VBoxLinuxAdditions.run: command not found
```

📸 **Screenshot of VBoxLinux Additions error:**  
![Screenshot showing an error during VBoxLinuxAdditions installation](./images/VBoxLinuxAdditions-error.png)

---

Instead, I verified the installation using:

```bash
lsmod | grep vbox
```

Output shows `vboxguest`, `vboxsf`, or `vboxvideo` modules are loaded, confirming Guest Additions is active.


📸 **Screenshot showing verification of Guest Additions:**  
![guest-additions-running.png](../images/guest-additions-running.png)
---

### Step 5: Enable Bidirectional Clipboard in VirtualBox

After the reboot:

1. Go to the VM window → `Devices → Shared Clipboard → Bidirectional`
2. (Optional) Also enable `Drag and Drop → Bidirectional`

📸 **Screenshot showing VirtualBox Devices menu:**  
![Enabled Bidirectional Clipboard](./images/05-devices-menu.png)

---
