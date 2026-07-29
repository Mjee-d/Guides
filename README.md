# Guides

## Setting Up Ubuntu 22.04 on WSL & Installing ROS 2 Humble

This guide walks through setting up **Ubuntu 22.04 LTS** using **Windows Subsystem for Linux (WSL)**, followed by a complete installation of **ROS 2 Humble Hawksbill**.

---

### Prerequisites
* **Windows 10** (Version 2004 or higher) or **Windows 11**.
* Windows Terminal or PowerShell running as **Administrator**.

---

### Step 1: Install Ubuntu 22.04 via WSL

1. Open **PowerShell as Administrator** and ensure WSL is installed:
   ```bash
   wsl --install
    ```
   <img width="471" height="105" alt="image" src="https://github.com/user-attachments/assets/e26514d9-3780-473f-9c8b-553b4a179cd1" />

   then:
   Install Ubuntu 22.04 LTS:
   <img width="443" height="69" alt="image" src="https://github.com/user-attachments/assets/a635a4af-e2f8-41f6-925c-8f285fa4e84f" />

   after that you have to reboot the system

   ### Step 2: Update System Packages
   
   Open your Ubuntu 22.04 terminal and update your package lists to ensure everything is up to date:
 ```bash
  sudo apt update && sudo apt upgrade -y
  ```
<img width="534" height="112" alt="image" src="https://github.com/user-attachments/assets/85a430ca-486f-408b-b0b9-52ffd04f9fe9" />

### Step 3: Set Up ROS 2 Repositories & Security Keys

Install required helper tools:
```bash
  sudo apt install software-properties-common curl -y
  ```
<img width="628" height="97" alt="image" src="https://github.com/user-attachments/assets/83b89727-245c-4102-83df-53e9ffe2451d" />

Add the official ROS 2 GPG key:
 ```bash
 sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
  ```
<img width="1100" height="153" alt="image" src="https://github.com/user-attachments/assets/5f9de2fa-8f18-4f85-8a48-902a278d619b" />

Add the ROS 2 repository to your system sources:
```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  ```
<img width="1099" height="219" alt="image" src="https://github.com/user-attachments/assets/1f091e41-4b4b-4267-adcc-02360f671b97" />

### Step 4: Install ROS 2 Humble

Update package indices to include the new ROS 2 repository:
```bash
sudo apt update
  ```
Install the full Desktop version of ROS 2 Humble (includes ROS, RViz, demos, and tutorials):
```bash
sudo apt install ros-humble-desktop -y
  ```

Step 5: Configure the ROS 2 Environment
```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
  ```
Step 6: Verify the Installation
Check the ROS 2 CLI version:
```bash
ros2 --version
  ```
Verify the active ROS distribution:
```bash
echo $ROS_DISTRO
  ```
<img width="307" height="42" alt="image" src="https://github.com/user-attachments/assets/9d1bf965-fb29-4dab-93a1-f419a720a046" />

