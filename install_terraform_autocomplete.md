# Steps to install terraform autocomplete in zsh

Here are the steps to install and enable Terraform autocompletion for Zsh:

### 1. **Ensure Prerequisites**

- **Zsh Installation**: Verify that Zsh is installed. Use the command:

```bash
zsh --version
```

If not installed, follow these commands based on your OS:
    - Ubuntu/Debian: `sudo apt update &amp;&amp; sudo apt install zsh`
    - macOS (with Homebrew): `brew install zsh`
- **Oh-My-Zsh Installation (Optional)**: Install Oh-My-Zsh for enhanced Zsh configuration:

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- **Terraform Installation**: Install Terraform using your preferred method (e.g., Homebrew on macOS or package managers on Linux).


### 2. **Enable Terraform Autocompletion**

- Run the following command to install Terraform autocompletion:

```bash
terraform -install-autocomplete
```

This will configure autocompletion for Zsh by adding necessary configurations to your `.zshrc` file.


### 3. **Verify `.zshrc` File**

- Ensure that a `.zshrc` file exists in your home directory (`~/.zshrc`). If it doesn't, create one:

```bash
touch ~/.zshrc
```


### 4. **Apply Changes**

- Restart your terminal or source the `.zshrc` file to apply the changes:

```bash
source ~/.zshrc
```


### 5. **Test Autocompletion**

- Open a new terminal session and type a partial Terraform command (e.g., `terraform pla`) followed by pressing `TAB`. You should see autocompletion suggestions.
