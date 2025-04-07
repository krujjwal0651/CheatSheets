<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# source ~/.zshrc

e=/etc/bash_completion.d/git
bash_completion=/usr/share/bash-completion/completions/
/Users/ujjwal/.git-completion.zsh:.:48: no such file or directory:
(eval):1: no matches found: *:globbed-files
_tags:comptags:36: can only be called from completion function
_tags:comptry:55: can only be called from completion function
_tags:comptags:60: can only be called from completion function
_tags:comptags:67: can only be called from completion function
ujjwal@Ujjwals-Mac-mini ~ %

The errors you encountered while setting up Git autocomplete in Zsh suggest issues with the `git-completion.zsh` script and its integration into your Zsh environment. Here's how to resolve these problems step-by-step:

---

### **1. Use the Correct Git Completion Script**

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

---

### **3. Troubleshooting Common Errors**

#### **Error: `no such file or directory`**

- Ensure that the `_git` file exists in `~/.zsh/functions`. Verify its presence using:

```bash
ls ~/.zsh/functions/_git
```


#### **Error: `_tags:comptags: can only be called from completion function`**

- This error occurs if the completion system (`compinit`) is not properly initialized. Ensure you have:

```bash
autoload -Uz compinit &amp;&amp; compinit
```

in your `.zshrc`.


#### **Error: `(eval):1: no matches found: *:globbed-files`**

- Add this line to `.zshrc` to disable strict globbing rules:

```bash
setopt no_nomatch
```


#### **Error with Bash Completion Scripts**

If you are trying to use a Bash completion script (`git-completion.bash`) in Zsh, ensure compatibility by adding this line to `.zshrc`:

```bash
zstyle ':completion:*:*:git:*' script ~/.zsh/git-completion.bash
```

However, using the dedicated Zsh script (`git-completion.zsh`) is recommended.

---

### **4. Alternative Solution with Oh-My-Zsh**

If you are using Oh-My-Zsh, simply enable the `git` plugin for Git autocompletion:

1. Open `.zshrc` and add `git` to the plugins list:

```bash
plugins=(git)
```

2. Reload `.zshrc`:

```bash
source ~/.zshrc
```


This approach simplifies Git autocomplete setup and avoids manual script configuration.

---

By following these steps, Git autocompletion should work seamlessly in your Zsh terminal without errors.

<div>⁂</div>

[^1]: https://www.baeldung.com/linux/git-autocompletion

[^2]: https://superuser.com/questions/987132/zsh-git-tab-autocomplete-not-working-if-head-is-next-to-last-word-on-input

[^3]: https://stackoverflow.com/questions/28028740/git-tab-completion-in-zsh-throwing-errors

[^4]: https://stackoverflow.com/questions/67624858/zsh-git-autocomplete-git-find-on-cmdline-error

[^5]: https://unix.stackexchange.com/questions/269791/zsh-tab-completion-for-function-with-git-commands

[^6]: https://unix.stackexchange.com/questions/738745/zsh-autocompletion-for-git-bare-repos

[^7]: https://unix.stackexchange.com/questions/335145/using-zsh-autocompletion-for-alias

[^8]: https://superuser.com/questions/46321/tweaking-zsh-git-autocompletion

[^9]: https://dev.to/rossijonas/how-to-set-up-history-based-autocompletion-in-zsh-k7o

[^10]: https://superuser.com/questions/40529/why-zsh-git-autocompletion-is-not-as-good-as-bash

[^11]: https://superuser.com/questions/1066743/how-to-get-bash-style-autocompletion-in-zsh-for-git-command

[^12]: https://bugzilla.redhat.com/show_bug.cgi?id=2055162

[^13]: https://unix.stackexchange.com/questions/783028/zsh-completion-not-working-for-self-defined-function-based-on-git

[^14]: https://unix.stackexchange.com/questions/120752/zsh-autocompletion-gives-seemingly-random-errors-after-some-time

[^15]: https://github.com/marlonrichert/zsh-autocomplete

[^16]: https://unix.stackexchange.com/questions/590186/zsh-completion-for-git-does-not-autocomplete-absolute-path

[^17]: https://stackoverflow.com/questions/60877052/zsh-autocompletion-appears-to-only-work-with-built-in-commands

[^18]: https://stackoverflow.com/questions/26462667/git-completion-not-working-in-zsh-on-os-x-yosemite-with-homebrew

[^19]: https://unix.stackexchange.com/questions/550559/zsh-file-autocompletion-with-bare-git-repo

[^20]: https://gist.github.com/ctechols/ca1035271ad134841284?permalink_comment_id=3483853

