# How to use git with multiple authors

```
AUTHOR: Samuel M.H.
DATE: 21-AUG-2021
LICENCE: all rights reserved.
```

_NOTE: this howto is based on a Stack Overflow discussion [1]._

## The problem
It happens that one could have several git user accounts on different services like github, bitbucket, etc. For example a one Github account for personal projects and another for working. The problem comes when you want to assign the commits to a specific user. By default, we configure git like this.

```bash
git config --global user.name "Personal Name"
git config --global user.email personal@email.com
```

This creates a `~/.gitconfig` file with a global git configuration.

And all the commits done in the machine will be assigned to that personal user. If we commit on a working repo, the author will be the personal user. How can we change this behavior?


## Configuring by repo
A **manual** solution can be manually configuring the author per repository. That is, you get into the repo directory and type:

```bash
git config user.name "Work Name"
git config user.email work@email.com
```


## Configuring by working directory
There is also another option, and is to tell git what configuration use for a certain directory. For example, repos under `~/work` should take "Work Name" as the author. This is my favourite because it can **automate** a lot.

Edit the `~/.gitconfig` file and use the option `[includeIf "gitdir:<your directory>"]`. The `path` variable sets the configuration file for that directory.

Example of `~/.gitconfig`. The global git configuration.
```text
[user]
	name = Personal Name
	email = personal@email
	
[includeIf "gitdir:~/work/"]
    path = ~/.gitconfig-work
```

Example of `~/.gitconfig-work`. The git configuration for the directory `~/work/`.
```text
[user]
    name = Work Name
    email = work@email.com
```



## References
* [1] [Can I specify multiple users for myself in .gitconfig?](https://stackoverflow.com/questions/4220416/can-i-specify-multiple-users-for-myself-in-gitconfig) - Stack Overflow
