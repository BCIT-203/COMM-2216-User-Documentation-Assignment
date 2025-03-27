# Installation and Configuration

## Overview

This guide provides detailed steps for installing Git on various operating systems (Windows, macOS, Linux), configuring it for use, and resolving common setup issues.

---

## Installation Instructions

### 1. **Installing Git on Windows**

#### Step-by-Step Instructions

1. **Download Git Installer:**
    1. Visit the official Git website: [https://git-scm.com/download/win](https://git-scm.com/download/win)
    2. The download should start automatically. If not, click on the "Windows" option for the download link.

2. **Run the Installer:**
    1. Once downloaded, double-click the installer `.exe` file to start the installation process.
    2. Click "Next" to proceed through the steps. You can generally accept the default options unless you need to change settings for specific use cases.

3. **Verify Installation:**
    1. Open a command prompt (`cmd`) or Git Bash (installed by default).
    2. Type the following command to verify that Git is installed:

        ```bash
        git --version
        ```

!!! note
    Git Bash is a command-line interface included with Git for Windows. It provides a Unix-like environment for running Git commands.

---

### 2. **Installing Git on macOS**

#### Step-by-Step Instructions

1. **Use Homebrew (Recommended)**:
   1. If you have [Homebrew](https://brew.sh/) installed, you can install Git with the following command:

        ```bash
        brew install git
        ```

2. **Manual Installation (Without Homebrew)**:
   1. Download the Git installer from [https://git-scm.com/download/mac](https://git-scm.com/download/mac).
   2. Open the `.dmg` file and follow the on-screen instructions to complete the installation.

3. **Verify Installation:**
   1. Open the Terminal and type the following command to check if Git is installed:

        ```bash
        git --version
        ```

---

### 3. **Installing Git on Linux**

#### Step-by-Step Instructions (Ubuntu/Debian-based)

1. **Install Git:**
   1. Open a terminal and use the package manager to install Git:

        ```bash
        sudo apt update
        sudo apt install git
        ```

2. **Verify Installation:**
   1. Check the installation by running:

        ```bash
        git --version
        ```

!!! note
    For other Linux distributions, use the respective package manager (`yum`, `dnf`, etc.).

---

## Configuration Instructions

### 1. **Setting Up Git for the First Time**

#### Step-by-Step Instructions

1. **Set Your User Name and Email:**
    Git uses this information to label the commits you make. Run the following commands, replacing "Your Name" and "<your.email@example.com>" with your actual details:

    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```

2. **Verify Configuration:**
    To verify the configuration settings, run:

    ```bash
    git config --list
    ```

!!! note
    The `--global` flag ensures that these settings are applied to all repositories on your system. You can override these settings on a per-repository basis by omitting the `--global` flag.

---

### 2. **Configuring Default Text Editor (Optional)**

#### Step-by-Step Instructions

1. **Set Default Editor:**
   - If you prefer using a different text editor (like VSCode or Sublime), set it using the following command:

     ```bash
     git config --global core.editor "code --wait"  # For VSCode
     ```

2. **Check Default Editor:**
   - You can check your current default editor with:

     ```bash
     git config --global core.editor
     ```

---

## Troubleshooting

### Common Issues and Solutions

1. **Git Command Not Found:**
   - **Solution:** Ensure that Git was added to your system’s `PATH` during installation. Re-run the installation and check the options to add Git to your system’s `PATH`.

2. **Permission Denied When Pushing to Remote:**
   - **Solution:** Ensure you have the correct SSH keys set up for remote repositories, or authenticate with your username/password if using HTTPS.

!!! warning
    **Be Careful with the `--global` Flag**: If you accidentally set the wrong user information globally, you can reset it using the `--global` flag again with the correct values.

---

## Conclusion

Git is an essential tool for version control in modern software development. By following the installation and configuration steps outlined above, you should be ready to start using Git effectively. If you run into any issues, refer to the troubleshooting section for solutions, and don’t hesitate to consult Git’s official documentation for more advanced use cases.

### Additional Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
