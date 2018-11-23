---
layout: post
title: SSH Aliasing
subtitle: How to Handle Multiple Git Accounts
tags: [tutorial, SSH, Git]
---

Here's a quick how-to on handling multiple accounts on github and/or bitbucket, for example.

#### Create keys

For each account create a identity/key pair. Can be one pair per repo or one for each account, etc..
```console
user:~$ ssh-keygen -t rsa
```

When prompted enter a name specific for the account as in `~/.ssh/id_rsa_github`. Use a safe passphrase for each public/private key pair, then upload the public key using web GUI for the respective account.

#### Load keys

Load keys into the agent:
```console
user:~$ ssh-add ~/.ssh/id_rsa_github
```
You can check to see if the keys were loaded:
```console
user:~$ ssh-add -l
```  

#### SSH config file

Create or modify an existing SSH config file. This file should be located at `~/.ssh/config`. Here's an example:
```bash
# Default Bitbucket user
Host bitbucket.org
    User git
    HostName bitbucket.org
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_bitbucket

# Default GitHub user
Host github.com
    User git
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github
```  

#### Modify the Git config file

Check the contents of this file with `$ cat ~/.gitconfig`. Add each account with the following commands:
```console
user:~$ git config --global github.name "username"
user:~$ git config --global github.token xxxx
```

Without the `--global` option, these would create a config file on a per repo basis (presumably, located at `$ REPO_DIRECTORY/.git/config`).

For bitbucket, replace `github` with `user` everywhere.

#### Test that it works!

```console
user:~$ ssh -T github.com
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

More info can be found at these sites:
* [](https://gist.github.com/jexchan/2351996)
* [](http://stackoverflow.com/questions/3225862/multiple-github-accounts-ssh-config)
* [](https://confluence.atlassian.com/pages/viewpage.action?pageId=271943168)

Next up, use SSH config to add other ssh aliases that involve port forwarding ([](http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/)).
