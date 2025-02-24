Here’s a bash script that installs various penetration testing and ethical hacking tools categorized by their purpose. This script will install the tools using `apt` for Debian-based systems (like Ubuntu). You can save this script as `install_tools.sh` and run it from anywhere after making it executable.

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
tools[recon]="amass sublist3r theHarvester recon-ng spiderfoot shodan"

# Scanning tools
tools[scanning]="nmap masscan nikto openvas qualys arachni"

# Exploitation tools
tools[exploitation]="metasploit-framework sqlmap beef exploitdb searchsploit"

# Post-Exploitation tools
tools[post_exploitation]="empire cobaltstrike mimikatz powersploit pupy"

# Reporting tools
tools[reporting]="dradis-framework pwn-doc"

# Wireless Testing tools
tools[wifi_testing]="aircrack-ng kismet wifite"

# Web Application Testing tools
tools[web_testing]="owasp-zap burp-suite w3af sqlninja"

# Social Engineering tools
tools[social_engineering]="set gophish"

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
This script will automate the installation of various penetration testing and ethical hacking tools categorized by their purpose. Make sure to run it with appropriate permissions and ensure that your system is compatible with the tools being installed.