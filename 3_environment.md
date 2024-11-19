WSL SetUp

1. **Enable WSL and Virtual Machine Platform**:
   - Open **PowerShell** as an administrator. You can do this by right-clicking the Start button and selecting **Windows Terminal (Admin)**.
   - Run the following command to enable WSL and the Virtual Machine Platform:
     ```powershell
     wsl --install
     ```
   - This command will install the necessary components and the default Linux distribution (usually Ubuntu). If you prefer a different distribution, you can specify it later.

2. **Restart Your Computer**:
   - After the installation completes, restart your computer to apply the changes.

3. **Set WSL 2 as the Default Version**:
   - Open **PowerShell** as an administrator again and run:
     ```powershell
     wsl --set-default-version 2
     ```
   - This ensures that any new Linux distributions installed will use WSL 2 by default, which offers better performance and full system call compatibility.

4. **Install a Linux Distribution**:
   - Open the **Microsoft Store**, search for your preferred Linux distribution (e.g., Ubuntu, Debian, Kali Linux), and click **Install**.
   - Once installed, launch the distribution from the Start menu.

5. **Set Up Your Linux Environment**:
   - When you launch the Linux distribution for the first time, you’ll be prompted to create a new user account and set up your environment.
   - Follow the on-screen instructions to complete the setup.

6. **Update Your Linux Distribution**:
   - Open your Linux terminal and run the following commands to update your system:
     ```bash
     sudo apt update
     sudo apt upgrade
     ```

After completing these steps, you’ll have a fully functional WSL setup on your Windows 11 system. You can now run Linux commands, install software, and enjoy the best of both worlds right from your Windows desktop[1](https://learn.microsoft.com/en-us/windows/wsl/install)[2](https://www.solveyourtech.com/how-to-install-wsl2-on-windows-11-a-step-by-step-guide-for-beginners/)[3](https://pureinfotech.com/install-wsl-windows-11/).

If you have any specific questions or run into issues, feel free to ask!