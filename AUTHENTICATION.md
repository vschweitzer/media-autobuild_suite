# Setting up git authentication

Required for any non-public repository.

## Setting up authentication

First, add a SSH key to your git host (such as, probably, github.com)

Create or edit you OpenSSh configuration file
(usually `~/.ssh/config`).

```
Host github.com
  User git
  Hostname github.com
  IdentityFile ~/.ssh/id_rsa
```

`Host` - To who you want to authenticate.
`User` - Usually `git` if using Git(hub).
`Hostname` - Basically just `Host` again.
`IdentityFile` - Path to the private key.

For more details about these options, check [this list](https://www.ssh.com/academy/ssh/config).

## Copying keys to msys2

Start msys2 and copy both your configuration and keys to your
msys2 filesystem. If your configuration matches the one above,
use `cd /c/Users/<username>/.ssh/ && cp id_rsa id_rsa.pub config ~/.ssh/`.