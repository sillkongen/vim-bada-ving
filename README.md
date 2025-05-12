# Vim Setup with Ansible

This Ansible playbook automates the setup of Vim with a modern configuration and useful plugins across different operating systems. It provides a consistent Vim environment whether you're on Windows, macOS, or Linux.

## Features

- Cross-platform support:
  - Windows (using Chocolatey)
  - macOS (using Homebrew)
  - Debian/Ubuntu (using apt)
  - RHEL/CentOS (using yum)
  - Alpine Linux (using apk)
- Automatic installation of vim-plug plugin manager
- Pre-configured with useful plugins:
  - [ALE](https://github.com/dense-analysis/ale) - Asynchronous Lint Engine
  - [NERDTree](https://github.com/preservim/nerdtree) - File tree explorer
  - [vim-fugitive](https://github.com/tpope/vim-fugitive) - Git integration
  - [vim-airline](https://github.com/vim-airline/vim-airline) - Status line enhancement
- Modern Vim configuration with:
  - Syntax highlighting
  - Line numbers
  - Cursor line/column highlighting
  - Smart indentation
  - Search highlighting
  - And more!

## Prerequisites

- Ansible 2.9 or higher
- Python 3.6 or higher
- For Windows:
  - PowerShell 5.1 or higher
  - Chocolatey (will be installed automatically if not present)
- For macOS:
  - Homebrew (will be installed automatically if not present)
- For Linux:
  - Appropriate package manager (apt, yum, or apk)

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/vim-bada-ving.git
   cd vim-bada-ving
   ```

2. Run the playbook:

   For Unix-like systems (Linux/macOS):
   ```bash
   # For current user
   ansible-playbook vimcentvega.yml

   # For specific user
   ansible-playbook vimcentvega.yml -e "user=username"

   # For root user
   sudo ansible-playbook vimcentvega.yml -e "user=root"
   ```

   For Windows:
   ```bash
   # Run in PowerShell as Administrator
   ansible-playbook vimcentvega.yml -e "ansible_connection=local"
   ```

## Customization

### Plugins

The playbook installs several useful plugins by default. You can modify the plugins list in the playbook by editing the `vimrc` content section. Look for the `call plug#begin()` section.

### Vim Configuration

The Vim configuration is defined in the playbook's `vimrc` content section. You can modify settings like:
- Tab width
- Line numbers
- Search behavior
- Color scheme
- And more!

## Troubleshooting

### Common Issues

1. **Plugin Installation Fails**
   - Ensure you have internet connectivity
   - Check if the user has write permissions to the Vim directories
   - Run with `-v` flag for verbose output:
     ```bash
     ansible-playbook vimcentvega.yml -v
     ```

2. **Path Issues on Windows**
   - Ensure you're running PowerShell as Administrator
   - Check if the user paths are correct in the debug output

3. **Permission Issues on Linux/macOS**
   - Use `sudo` when running for root or other users
   - Check directory permissions with `ls -la ~/.vim`

### Debugging

The playbook includes several debug tasks that show:
- Current user and paths
- Vim installation status
- Plugin installation status
- File checksums

Run with increased verbosity for more details:
```bash
ansible-playbook vimcentvega.yml -vvv
```

## Directory Structure

```
vim-bada-ving/
├── vimcentvega.yml    # Main playbook
├── README.md          # This file
└── .gitignore        # Git ignore file
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- [vim-plug](https://github.com/junegunn/vim-plug) - Minimalist Vim Plugin Manager
- All the plugin authors for their amazing work
- The Ansible community for their excellent documentation
