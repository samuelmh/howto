# How to use git with multiple SSH keys

```
AUTHOR: Samuel M.H.
DATE: 21-AUG-2021
LICENCE: all rights reserved.
```


## The problem
The problem here is how to tell git and SSH which key to use for a particular domain. We could have two accounts on github, one personal and another for work, but since the two are in the same domain, they will share the same SSH key. 


## SSH config file
The solution is to use alias for hosts in the SSH configuration file `~/.ssh/config`.

```text
# Personal github
Host github.com
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_personal@email.com

# Work github
Host github.com-work
	HostName github.com
	User git
	IdentityFile ~/.ssh/id_rsa_work@email.com
```

This way you can refer to `github.com` and to `github.com-work` as two completely different sites in the context of SSH. You only have to remember to use the alias when working with the remote.

For exmaple:

```
git clone https://github.com-work/<work user>/<work repo>
```


## Resources
* [1] [How to tell git which private key to use?](https://superuser.com/questions/232373/how-to-tell-git-which-private-key-to-use)
* [2] [Connecting to GitHub with SSH](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh)
