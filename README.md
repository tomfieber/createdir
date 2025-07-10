# CreateDir - Penetration Testing Directory Generator

A Bash script that creates organized directory structures for penetration testing assessments. This tool helps security professionals quickly set up standardized project directories with pre-populated templates for documentation, evidence collection, and reporting.

## Overview

CreateDir automates the creation of comprehensive directory structures for three types of security assessments:

1. **External Network Testing** - For external penetration tests and red team engagements
2. **Internal Network Testing** - For internal network assessments and Active Directory testing  
3. **Web Application Testing** - For web application security assessments

Each assessment type includes:
- ✅ Structured directory hierarchies
- 📝 Pre-populated Markdown templates
- 🔧 Environment variable configuration
- 📋 Comprehensive checklists and methodologies
- 🗂️ Evidence collection frameworks

## Features

- **Interactive Setup**: Guided prompts for assessment type, target IPs, and project naming
- **Comprehensive Templates**: Over 50+ pre-written documentation templates
- **Validation**: Input validation for directory names and IP addresses
- **Environment Integration**: Automatic `.envrc` file creation for direnv support
- **Cross-Platform**: Works on macOS, Linux, and Windows (with Bash support)
- **Organized Structure**: Logical separation of admin, data, evidence, and reporting sections

## Installation

### Prerequisites
- Bash shell (version 4.0 or higher)
- Basic Unix utilities (`mkdir`, `echo`, `read`)

### Quick Install
1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/createdir.git
   cd createdir
   ```

2. **Make the script executable:**
   ```bash
   chmod +x createdir.sh
   ```

3. **Source the script in your shell:**
   ```bash
   source ./createdir.sh
   ```

### Optional: Add to Shell Profile
For permanent access, add the script to your shell profile:

```bash
# Add to ~/.bashrc or ~/.zshrc
source /path/to/createdir/createdir.sh
```

### Optional: direnv Integration
Install [direnv](https://direnv.net/) for automatic environment variable loading:
```bash
# macOS
brew install direnv

# Ubuntu/Debian
sudo apt-get install direnv

# Add to shell profile
echo 'eval "$(direnv hook bash)"' >> ~/.bashrc  # or ~/.zshrc for zsh
```

## Usage

### Basic Usage
Simply run the function from any directory:
```bash
createdir
```

### Interactive Prompts
The script will guide you through:
1. **Assessment Type Selection** (1-3):
   - 1) External Network Test
   - 2) Internal Network Test  
   - 3) Web Application Test

2. **Directory Name**: Enter a name for your project directory

3. **Target IP** (optional): Primary target IP address

4. **Host IP** (optional): Your local/VPN IP address

### Example Session
```bash
$ createdir
Select the assessment type:
1) External Network Test
2) Internal Network Test
3) Web Application Test
Enter your choice (1-3): 2
Enter a name for the directory: 
acme-internal-test
Enter an IP if there is one (useful for labs): 
192.168.1.100
Enter a HOST IP (e.g., a tun0 VPN IP): 
10.10.14.50

📁 Creating directory structure...
📝 Creating note files...
🔧 Creating environment file...
📝 Creating assessment README...
✅ Environment variables configured with direnv

✅ Project directory 'acme-internal-test' created successfully!
📋 Assessment Type: Internal Network Test
📍 Current location: /Users/tester/acme-internal-test
🌐 Target IP: 192.168.1.100
🏠 Host IP: 10.10.14.50
```

## Directory Structure

### External Network Test
```
project-name/
├── 01-Admin/                    # Project administration
│   ├── 1-Admin Information.md
│   ├── 2-Scope.md
│   ├── 3-Questions.md
│   ├── 4-Clean-Up.md
│   └── 5-TODO.md
├── 02-Data/                     # Data collection
│   ├── 1-Users List.md
│   ├── 2-Listening Services.md
│   └── 3-Count of Listening Service.md
├── 03-Evidence/                 # Evidence and documentation
│   ├── 1-Notes/
│   │   ├── 1-OSINT/            # Open source intelligence
│   │   ├── 2-Hostname Enumeration/
│   │   ├── 3-Scans/            # Port and vulnerability scans
│   │   ├── 4-Services/         # Service enumeration
│   │   └── 5-Web App Testing/
│   ├── 2-Findings/             # Security findings
│   ├── 3-Logging_Output/       # Tool outputs
│   ├── 4-Misc. Files/         # Additional files
│   └── 5-Screenshots/          # Evidence screenshots
├── 04-Retest/                  # Retest documentation
├── .envrc                      # Environment variables
└── README.md                   # Project overview
```

### Internal Network Test
```
project-name/
├── 01-Admin/                    # Project administration
├── 02-Data/                     # Data collection
├── 03-Evidence/
│   ├── 1-Notes/
│   │   ├── 1-Unauthenticated/  # Pre-credential testing
│   │   ├── 2-SMB/              # SMB enumeration
│   │   ├── 3-LDAP/             # LDAP enumeration
│   │   ├── 4-Poisoning/        # Network poisoning attacks
│   │   ├── 5-User Compromise/  # User-level attacks
│   │   ├── 6-ADCS/             # Active Directory Certificate Services
│   │   ├── 7-Machine Compromise/ # System-level compromise
│   │   ├── 8-MSSQL/            # SQL Server testing
│   │   ├── 9-Internal Services/ # Service enumeration
│   │   └── 10-Internal Web Services/
│   └── [Additional evidence directories]
└── [Standard files]
```

### Web Application Test
```
project-name/
├── 01-Admin/                    # Project administration
├── 02-OSINT/                    # Open source intelligence
├── 03-Evidence/
│   ├── Findings/               # Security findings
│   ├── Notes/                  # Testing notes
│   ├── Scans/                  # Automated scan results
│   │   ├── Web Scans/
│   │   ├── API Testing/
│   │   └── Burp Output/
│   ├── Tools/                  # Tool configurations
│   │   ├── Burp Project/
│   │   └── Custom Scripts/
│   └── [Additional directories]
└── [Standard files]
```

## Templates Included

### Administrative Templates
- **Admin Information**: Project details, contacts, timelines
- **Scope**: Testing scope, rules of engagement, exclusions
- **Questions**: Client questions and clarifications needed
- **Clean-Up**: Remediation activities and evidence collection
- **TODO**: Comprehensive testing checklists

### Technical Templates
- **OSINT**: Repository searching, Google dorking, username enumeration
- **Scanning**: Port scans, vulnerability assessments, service enumeration
- **Web Testing**: Authentication testing, input validation, session management
- **Active Directory**: LDAP enumeration, BloodHound analysis, privilege escalation
- **Network Services**: SMB shares, MSSQL testing, internal applications

## Environment Variables

The script automatically creates a `.envrc` file with project variables:

```bash
export name='project-name'
export assessment_type='External Network Test'
export ip='192.168.1.100'
export lhost='10.10.14.50'
```

These variables can be used in your tools and scripts throughout the assessment.

## Input Validation

The script includes robust input validation:
- **Directory Names**: Alphanumeric characters, dots, hyphens, underscores only
- **IP Addresses**: Valid IPv4 format validation (0-255 for each octet)
- **Assessment Types**: Must be 1, 2, or 3
- **Overwrite Protection**: Warns before overwriting existing directories

## Error Handling

- Validates all user inputs before processing
- Checks directory creation permissions
- Reports failed file creation attempts
- Provides meaningful error messages
- Graceful handling of existing directories

## Customization

The script can be easily customized by modifying the helper functions:
- `_create_external_files()` - External network templates
- `_create_internal_files()` - Internal network templates  
- `_create_webapp_files()` - Web application templates
- `_create_assessment_dirs()` - Directory structures

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

If you encounter any issues or have questions:
- Check the existing issues on GitHub
- Create a new issue with detailed information
- Include your OS and Bash version
- Provide steps to reproduce any problems

## Changelog

### v1.0.0
- Initial release
- Support for three assessment types
- Comprehensive template library
- Input validation and error handling
- direnv integration
