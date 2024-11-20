# GIT

## 1. How to use different SSH keys for different Bitbucket accounts

### 1.1. Generate SSH keys

```console
ssh-keygen -t rsa -f ~/.ssh/my-new-key
```

### 1.2. Add the new key to the SSH agent

```console
ssh-add ~/.ssh/my-new-key
```

### 1.3. Add the new key to the SSH config

Create config file if it does not exist

```console
touch ~/.ssh/config
```

Open the config file

```console
nano ~/.ssh/config
```

Add the following configuration

```config
# Default Bitbucket account
Host bitbucket.org
    HostName bitbucket.org
    User git
    IdentityFile ~/.ssh/id_rsa

# Second Bitbucket account
Host bitbucket-other
    HostName bitbucket.org
    User git
    IdentityFile ~/.ssh/my-new-key
```

### 1.4. Add the new key to the Bitbucket account

Copy the public key

```console
cat ~/.ssh/my-new-key.pub
```

Add the public key to the Bitbucket account

1. Go to Bitbucket
2. Click on your avatar in the bottom left corner
3. Click on `Bitbucket settings`
4. Click on `SSH keys`
5. Click on `Add key`
6. Paste the public key

### 1.5. Test the new key

```console
ssh -T git@bitbucket-other
```

### 1.6. Clone the repository

```console
git clone git@bitbucket-other:username/repo.git
```