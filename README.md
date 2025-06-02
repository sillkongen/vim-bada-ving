# Vim Setup with Ansible

This Ansible playbook automates the setup of Vim with a modern configuration and useful plugins for Unix-like operating systems. It provides a consistent Vim environment on macOS and Linux.

## Features

- Platform support:
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
- For macOS:
  - Homebrew (will be installed automatically if not present)
- For Linux:
  - Appropriate package manager (apt, yum, or apk)

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/sillkongen/vim-bada-ving.git
   cd vim-bada-ving
   ```

2. Configure the user (optional):
   The playbook uses variables to determine which user to configure Vim for:
   - `user`: The username for whom to install and configure Vim (defaults to current user)
   - `user_home`: The home directory of the user (automatically determined)
   
   You can set these variables in several ways:
   - Using command line: `-e "user=username"`
   - Using an inventory file
   - Using group_vars or host_vars
   - Using an external variables file

3. Run the playbook:

   ```bash
   # For current user (default)
   ansible-playbook vimcentvega.yml

   # For specific user
   ansible-playbook vimcentvega.yml -e "user=username"

   # For root user
   sudo ansible-playbook vimcentvega.yml -e "user=root"
   ```

## User Configuration

The playbook handles user configuration in the following ways:

- **Default Behavior**: If no user is specified, the playbook configures Vim for the current user
- **Specific User**: You can target a specific user by setting the `user` variable
- **Multiple Users**: To configure Vim for multiple users, run the playbook multiple times with different user variables
- **Root User**: Special care is taken when configuring for the root user to ensure proper permissions

Example configurations:
```bash
# Configure for a specific user with custom settings
ansible-playbook vimcentvega.yml -e "user=developer"

# Configure for root with specific settings
sudo ansible-playbook vimcentvega.yml -e "user=root"

# Configure for current user with debug output
ansible-playbook vimcentvega.yml -v
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

2. **Permission Issues on Linux/macOS**
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
