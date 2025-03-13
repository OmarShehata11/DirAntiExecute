# DirAntiExecute

## Overview
DirAntiExecute is a Windows mini-filter kernel driver designed to prevent the execution of executable files (`.exe`) stored in a specific directory. This project is particularly useful for malware analysts who store uncompressed malware samples on their main machine and want to ensure that these files cannot be accidentally executed.

## Features
- **Prevents Execution:** Blocks any execution attempt of `.exe` files within a specified directory.
- **Applies to All Users:** The execution block applies even to administrators.
- **Allows Read/Write Operations:** Files within the directory can still be read and modified, making it practical for analysis and research purposes.

## Motivation
As a malware analyst, I store various malware samples on my machine. Some of these samples are in an executable format and not compressed. To mitigate the risk of accidental execution, I developed this mini-filter driver to monitor file access with EXECUTE permission on `.exe` files under a designated directory. This ensures safety while still allowing analysis and modifications when needed.

## Installation & Usage
### Prerequisites
- Windows operating system
- Windows Driver Kit (WDK) installed
- Admin privileges to install and manage drivers

### Building the Driver
1. Clone the repository:
   ```bash
   git clone https://github.com/OmarShehata11/DirAntiExecute.git
   ```
2. Open the project in Visual Studio with the WDK installed.
3. Build the project in Release mode ( or in debug mode if you want to see the debug output).

### Installing the Driver
1. install the driver using the INF file within the compiled code
2. Start the driver:
   ```bash
   sc start MalwareAntiExecuteFinal
   ```
> NOTE: you can change the service name by modifying the INF file, for me I named it MalwareAntiExecuteFinal.

### Uninstalling the Driver
1. Stop the driver:
   ```bash
   sc stop MalwareAntiExecuteFinal
   ```
2. Delete the driver service:
   ```bash
   sc delete MalwareAntiExecuteFinal
   ```

## Configuration
- The directory to be monitored is specified in the code. Modify the source code as needed to change the monitored directory.
- By default, the driver allows read and write operations but blocks execution.

## Disclaimer
Use this driver at your own risk. Modifying system-level file access can have unintended consequences. Ensure you understand how kernel drivers work before deploying them on a critical system.

## Contributing
Feel free to contribute to this project by submitting pull requests or opening issues.

## Author
**Omar Shehata**  
GitHub: [OmarShehata11](https://github.com/OmarShehata11)

---
Enjoy using the project! 🚀

