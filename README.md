# GPG_GitHub
### 0. Prerequisite

Run the commands below in ***Git Bash*** if you are using Windows operation system.

***

### 1. Enabling vigilant mode

**Settings** -> **SSH and GPG keys** ->(Vigilant mode) **Flag unsigned commits as unverified**

***

### 2. Existing GPG keys

```(bash)
gpg --list-secret-keys --keyid-format=long
```

Output:
```(bash)
sec   rsa4096/[secKeyID]
```

***

### 3. Generating a GPG key

```(bash)
gpg --full-generate-key
```
> Notes
> 1. Your key must be at least 4096 bits.
> 2. Key's `Real name` must be same as GitHub account's username.
> 3. Key's `Email address` must be your GitHub-provided `no-reply` email address which is based on `@users.noreply.github.com` suffix.
> 4. Key's `Passphrase` could be empty.

***

### 4.Exporting `sec` key

```(bash)
gpg --armor --export [secKeyID]
```

***

### 5. Copy exported ASCII GPG key into GitHub settings

***

### 6. Git settings

Observe

```(bash)
git config --global -l
```

Set

```(bash)
git config --global --add user.name [GitHubAccountUsername]
git config --global --add user.email [GitHubNoReplyEmail]
git config --global --add user.signingkey [secKeyID]
git config --global --add commit.gpgsign true
git config --global http.proxy http://[IP | domain]:[port]/
```

Unset
```
git config --global --unset [gitConfigOption]
```

***

### 7.Migrate GPG Keys to other device

Copy the entire `.gnupg` directory from current user's home directory to another's.
