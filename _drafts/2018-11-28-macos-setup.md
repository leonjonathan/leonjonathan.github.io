1. Fresh install Mojave 14.1
2. Login to iCloud and Merge iCloud Docs
3. Install SublimeText?  
   * https://realpython.com/setting-up-sublime-text-3-for-full-stack-python-development/
   
   * ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl

4. Customize Terminal App
5. Create Bash profile with aliases
6. Install Homebrew
   `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`  
   This automatically installs command line tools. Check with Xcode-select -p if installed.
7. Install VS Code  
   https://www.kennethreitz.org/essays/why-you-should-use-vs-code-if-youre-a-python-developer
   http://howtopython.org/en/latest/editor/

8. Install pyenv  
   * `Brew install pyenv`  
     Enable autocomplete:  
     `$ echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bash_profile`

   * install python
   * Issue with Mojave 10.14.1 where zlib is missing. I   think home-brew needs to fix  
     ```
     $ sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
     ```
     ```console
     pyenv install 3.6.7
     Installed Python-3.6.7 to  /Users/jonathanleon/.pyenv/versions/3.6.7
     pyenv global 3.6.7
     ```
     ```console
     $ pyenv versions
     system
     * 3.6.7 (set by /Users/jonathanleon/.pyenv/version)
     ```

9. Install Pipenv
   ```console
   $ pip install --user pipenv
   ```
   ```bash
   # Add user base's binary directory to path
   export PATH="${HOME}/.local/bin:${PATH}"
   ```

10. Brew install git  
    https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control 
    Setup ~/.gitconfig to use vs code as default editor:
    ```console
    $ git config --global core.editor "code --wait"
    ```

11. Brew install bash-completions

12. Setup dev directory structure
    https://www.stuartellis.name/articles/mac-setup/#setting-up-a-directory-structure-for-projects

13. Finalize .dot file setup:  
    Borrowed some from:  
    * https://github.com/mathiasbynens
    * https://hackernoon.com/personal-macos-workspace-setup-adf61869cd79