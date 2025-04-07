# Steps to install Git auto-complete in mac zsh 

---

### 1. **Use the Correct Git Completion Script**

The `git-completion.zsh` script is not designed to be directly sourced. Instead, it should be placed in the `$fpath` directory and renamed as `_git`. Follow these steps:

1. **Create a Directory for Zsh Functions**:

```bash
mkdir -p ~/.zsh/functions
```

2. **Download and Rename the Script**:

```bash
curl -o ~/.zsh/functions/_git https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.zsh
```

3. **Update `$fpath` in `.zshrc`**:
Open your `.zshrc` file:

```bash
nano ~/.zshrc
```

Add the following lines:

```bash
fpath=(~/.zsh/functions $fpath)
autoload -Uz compinit &amp;&amp; compinit
```

4. **Remove Cached Completion Files**:
Clear existing Zsh completion cache to prevent conflicts:

```bash
rm ~/.zcompdump*
```

5. **Reload Zsh Configuration**:
Apply the changes by sourcing `.zshrc`:

```bash
source ~/.zshrc
```


---

### **2. Test Git Autocomplete**

After completing the setup, test Git autocompletion by typing a partial command, such as `git che`, and pressing `TAB`. It should suggest completions like `checkout`.
