Here’s an updated version of the bash script that organizes the installation of penetration testing and ethical hacking tools into specific categories. Each category is clearly defined, making it easier to understand which tools belong to which section.

```bash
#!/bin/bash

# Update and upgrade the system
echo "Updating and upgrading the system..."
sudo apt update && sudo apt upgrade -y

# Function to install tools
install_tools() {
    echo "Installing $1 tools..."
    for tool in "${!2}"; do
        echo "Installing $tool..."
        sudo apt install -y "$tool"
    done
}

# Define tools by category
declare -A tools

# Reconnaissance tools
tools[Reconnaissance]="amass sublist3r theHarvester recon-ng spiderfoot shodan"

# Scanning tools
tools[Scanning]="nmap masscan nikto openvas"

# Exploitation tools
tools[Exploitation]="metasploit-framework sqlmap beef exploitdb searchsploit"

# Post-Exploitation tools
tools[Post_Exploitation]="empire cobaltstrike mimikatz powersploit pupy"

# Reporting tools
tools[Reporting]="dradis-framework pwn-doc"

# Wireless Testing tools
tools[Wireless_Testing]="aircrack-ng kismet wifite"

# Web Application Testing tools
tools[Web_Application_Testing]="owasp-zap burp-suite w3af sqlninja"

# Social Engineering tools
tools[Social_Engineering]="set gophish"

# Install each category of tools
for category in "${!tools[@]}"; do
    install_tools "$category" "tools[$category]"
done

echo "All tools installed successfully!"

# Clean up
sudo apt autoremove -y
echo "Cleanup completed."
```

### **Instructions to Use the Script**

1. **Create the Script File:**
   Open your terminal and create a new file:
   ```bash
   nano install_tools.sh
   ```

2. **Copy and Paste the Script:**
   Copy the above script and paste it into the `install_tools.sh` file.

3. **Make the Script Executable:**
   Save the file and exit the editor. Then, make the script executable:
   ```bash
   chmod +x install_tools.sh
   ```

4. **Run the Script:**
   You can now run the script from anywhere:
   ```bash
   ./install_tools.sh
   ```

### **Conclusion**
This script organizes the installation of various penetration testing and ethical hacking tools into clearly defined categories. Each category is labeled, making it easier to identify the purpose of each tool being installed. Make sure to run the script with appropriate permissions and ensure that your system is compatible with the tools being installed.