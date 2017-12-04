> 04 déc. 2017 09:19:30

# Git

----------------------------

## Désindexer fichiers sans les supprimer

```sh
git rm --cached
```

----------------------------

## Annuler un ou des commits

Désindexe les derniers fichiers en laissent les dernières modifications et 
le(s) dernier(s) commit(s):

```sh
git reset HEAD^ <fichier(s)>
```

Désindexe les derniers fichiers en laissent les dernières modifications et en supprimant le(s) dernier(s) commit(s):

```sh
git reset --soft HEAD^ <fichier(s)>
```

Désindexe les derniers fichiers en supprimant les dernières modifications et 
le(s) dernier(s) commit(s):

```sh
git reset --soft HEAD^ <fichier(s)>
```

----------------------------

## Effacer un tag distant

L'effacer en 1er lieu localement: `git tag -d <tag>`
Puis: `git push origin :refs/tags/<tag>`

----------------------------

## Annuler un commit

Avec `git reset` qui peut accepter:

* `--mixed`: Revenir en arrière dans l'historique, garder ses modifs et enlever les marques des commits (Par défaut).
* `--soft`: Revenir en arrière, garder ses modifs et garder les marques.
* `--hard`: Tout annuler.

e.g  
```sh
git reset --hard HEAD~2
```

----------------------------

## Forker a repo

1. Clone your forked repo
2. Add the original repo as an upstream remote: `git remote add upstream https://original...git`
3. Fetch the last commits: `git fetch upstream`

**N.B**:
After fetching your local version you should merge it before pushing to your online fork:

```sh
git merge upstream/master
git push (-u)? origin master
```

----------------------------

## Puller une branche

```sh
git pull origin remotebranch:localbranch
git fetch upstream remotebranch:localbranch
```

----------------------------

## Use ssh

### 1. Check for existing SSH keys

```
ls -al ~/.ssh
```

Public keys should be:  
* id_dsa.pub
* id_ecdsa.pub
* id_ed25519.pub
* id_rsa.pub

### 2. Generate a new SSH key

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
 # Enter for the file, use default location.
 # Type a passphrase
```

### 3. Add the SSH key to your github account

Use the `id_rsa.pub`.

### 4. Test the SSH connection

```sh
ssh -T git@github.com
```

You may see:

```
The authenticity of host 'github.com (192.30.252.1)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?

 # Or

The authenticity of host 'github.com (192.30.252.1)' can't be established.
RSA key fingerprint is nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)?
```

Type yes and your passphrase if needed.  
If everything is ok:

```
Hi username! You've successfully authenticated, but GitHub does not
provide shell access.
```

### 5. Update remote repository URLs

To switch from `https` to `ssh`:

```sh
git remote set-url {remote name} {remote URL}
```

e.g.

```sh
git remote set-url origin git@github.com:kabbamine/repo.git
```

**N.B:**

* The `.git` is mandatory.
* Use `https://github.com/USERNAME/REPO.git` to switch from `ssh` to `https`.

----------------------------

## Remove a gitmodule

```sh
# My need deinit -f
git submodule deinit mysubmod
git rm mysubmod
git push
rm -rf .git/modules/mysubmod
```

Verify that `git config --local -l` do not contain mysubmod.

----------------------------
