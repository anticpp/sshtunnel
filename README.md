Proxying TCP connections using ssh tunnel. Only support `SOCK5` now.

## Preparation

You must have a remote linux server. And the local machine must be ssh-authorized to remote server, so that we can ssh to remote server without interacting a password.

However, how to authorized is beyond our topics.

Here is some illusions:

1. Generate key

Run `ssh-keygen` at local machine.
After this, you can find your public key and private key in `~/.ssh/`.

2. Authorize

Copy content line of `~/.ssh/id_rsa.pub` at local machine, then add it to a new line at remote server's `~/.ssh/authorized_keys`. If `~/.ssh/authorized_keys` doesn't exists, create a new one.

3. Check

`ssh <user>@<address>` to check if it's ok.

## Environment

```
echo "## SSH TUNNEL" >> ~/.bash_profile
echo "export SSH_TUNNEL_REMOTE_SERVER=<ssh-tunnel-remote-server>" >> ~/.bash_profile
echo "export SSH_TUNNEL_REMOTE_USER=<ssh-tunnel-remote-user>" >> ~/.bash_profile
source ~/.bash_profile
```
> ssh-tunnel-remote-server: Address of remote server.
>
> ssh-tunnel-remote-user: Login user of remote server.

## Install

1. Clone
```
git clone <repo> sshtunnel
sh install <install-path>
```

> repo: This repository.
>
> install-path: Binary will be copied to this path.

2. PATH

```
echo "" >> ~/.bash_profile
echo "export PATH=$PATH:<install-path>" >> ~/.bash_profile
source ~/.bash_profile
```

> install-path: Make it as a default PATH to run binary everywhere.

## Run

```
sshtunnel &
```

## Web proxying

You can configure with `SOCK5` proxy of port `8800` for your web browser.

Example, as in `Chrome`, you can configure with `SwitchySharp`.

Although, how to configure all browsers is beyond our topics.
