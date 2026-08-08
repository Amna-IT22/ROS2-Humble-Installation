<img width="973" height="505" alt="جد" src="https://github.com/user-attachments/assets/d60c61c3-bc7f-4367-967b-ddc4fde193ea" />
# ROS 2 Humble Installation and Configuration Report on Ubuntu 22.04 (WSL2)

## 📌 Introduction
This report provides a comprehensive, step-by-step visual documentation of the successful installation and environment configuration of the Robot Operating System (**ROS 2 Humble**) on **Ubuntu 22.04** running via **WSL2** (Windows Subsystem for Linux). This work fulfills the practical project requirements.

---

## 🛠️ Execution Steps and Visual Documentation

### Step 1: Initializing Ubuntu Environment and Creating User Account
The process began with booting up the newly installed Ubuntu 22.04 instance on WSL2 and setting up the default Unix user account credentials.
<img width="969" height="507" alt="u1" src="https://github.com/user-attachments/assets/e8ae3bf4-ca29-499d-b2d2-45b7888270c2" />

---

### Step 2: Updating and Upgrading System Packages
To ensure full system compatibility, stability, and security before installing external repositories, a complete package update and upgrade was executed.
* **Commands Executed**:
  ```bash
  sudo apt update && sudo apt upgrade -y
  ```
<img width="975" height="510" alt="u3" src="https://github.com/user-attachments/assets/9aeedf23-2e31-4c29-a20b-c411413a2550" />
---
<img width="981" height="509" alt="u2" src="https://github.com/user-attachments/assets/845bb35f-2c49-41ff-a34f-d2214f06dd0c" />

### Step 3: Installing Core Software Utilities
The foundational tools required for adding software properties and downloading digital verification keys safely from internet servers were installed.
* **Command Executed**:
  ```bash
  sudo apt install software-properties-common curl -y
  ```
<img width="977" height="512" alt="u4" src="https://github.com/user-attachments/assets/2216cccd-8c9b-4884-902e-1cc2989b9224" />

---

## ⚠️ Technical Challenges & Network Resolution

During the repository configuration, several critical network blocking constraints were encountered, including `NO_PUBKEY F42ED6FBAB17C654` and GitHub host resolution errors due to restrictive local ISP/Wi-Fi firewalls. 

<img width="970" height="508" alt="6u" src="https://github.com/user-attachments/assets/23123206-5382-4b9d-b94f-2b510563fbc6" />
<img width="976" height="511" alt="اخطاء" src="https://github.com/user-attachments/assets/239bf3f8-f354-4812-9e72-af494b71a17f" />

### Resolution Protocol:
1. **Network Swapping**: Switched the laptop connection from the restricted home Wi-Fi to a cellular smartphone hotspot network.
2. **Local Key Injection**: Bypassed the blocked GitHub servers by fetching and authenticating the GPG signature directly via the local package manager architecture using:
   ```bash
   sudo apt-key adv --recv-keys F42ED6FBAB17C654
   ```

---

### Step 4: Adding the Official ROS 2 Package Repository
Once the secure cryptographic key path was verified locally, the explicit ROS 2 package distribution link matching the system architecture (`amd64`) and release name (`jammy`) was injected into the sources list.
* **Command Executed**:
  ```bash
  echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://ros.org jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  ```

---

### Step 5: Executing the ROS 2 Humble Desktop Installation
With the repository successfully attached, a target system update was triggered followed by the installation of the full desktop suite containing graphical tools, simulators, and core communication libraries.

* **Network Interruption Fix**: Due to a temporary cellular network drops during the mass download phase, the structural `--fix-missing` flag was smartly deployed to resume downloads efficiently without restarting from scratch:
  ```bash
  sudo apt install ros-humble-desktop --fix-missing -y
  ```
<img width="983" height="512" alt="الاخير جديد" src="https://github.com/user-attachments/assets/0be8bb3b-6dd5-4664-8b6a-dc41d0f6ab7c" />
<img width="973" height="505" alt="جد" src="https://github.com/user-attachments/assets/7574e539-521c-4987-8570-c4ed7b90ca1e" />

---

### Step 6: Environment Sourcing and Final Verification (The Golden Snapshot)
To eliminate the need for manual configuration on every new terminal launch, the ROS 2 environment script path was dynamically linked directly inside the bash run commands file (`~/.bashrc`). Finally, the system environment variables were checked.
* **Commands Executed**:
  ```bash
  echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
  source ~/.bashrc
  echo \$ROS_DISTRO
  ```
* **Terminal Output Verified**: `humble`
<img width="972" height="509" alt="جدد" src="https://github.com/user-attachments/assets/14240a1c-dff4-4193-9399-c8077531b542" />

## 🎯 Conclusion
The ROS 2 Humble installation has been completed with high technical accuracy. All network filtering barriers were successfully troubleshot and solved locally. The robotics development ecosystem is now fully functional, calibrated, and ready for deployment.
