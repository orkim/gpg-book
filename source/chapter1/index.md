# GPG Key Lifecycle

## Introduction

- Create a key, with a limited lifetime.
- Update that key when the time comes.
- How to fix a key ring for `offline master key` use.

## GPG Lifecycle - Initial keypair

### Create a new master keypair

```
$ gpg --expert --full-generate-key
```

This command will generate a new keypair while prompting for the needed input. It also creates a UID, and an encryption
subkey.

- Select the kind of key you want: RSA and RSA
- What keysize do you want? 4096
- Key is valid for? 0 (key does not expire)
- Real name: 5 chars or more; cannot start with a digit
- Email address: needs 1 or more characters followed by @, followed by 1 or more characters
- Comment: (optional) describes key use
- Passphrase: complex passphrase

### Create a new (expiring) signing subkey

Now we will add a new subkey that has an expiration date. This is not foolproof, but the key will need to be cycled
every year (while keeping the master secret key offline) to help minimize damage should the secret key get compromised.

```
$ gpg --edit-key user@key.com
gpg> addkey
select what kind of key you want: (4) RSA (sign only)
what keysize do you want? 4096
key is valid for? 2023-01-01

gpg> quit
save changes? y
```

### Generate a revocation certificate for the master keypair

This can be used in case the master secret key is compromised. **Store this offline**.

```
$ gpg --generate-revocation --output user@key.com-revocation-cert.gpg
```

### Export master public/private keypair

This is the master public AND PRIVATE keypair. **Store this offline**.

```
$ gpg --export --armor --output user@key.com-public.gpg
$ gpg --export-secret-keys --armor --output user@key.com-private.gpg
```

### Delete the master secret key

This step is going to remove the master secret key from the keyring (located in `~/.gnupg/`) so that in case the keyring
is compromised damage can be minimized. The subkey will be used for the next year to do the commit/tag signing.

We can always reimport the master secret key (with a complex passphrase), and indeed we will need to do so once per
year to generate a new valid signing key. This was exported in the step above.

GPG doesn't make this particularly easy, but the following is the new 'quick way' of accomplishing this task. Make sure
to use the keygrip of the `sec` key ('Secret Key'; listed on top) which is the master keypair secret key used for
certification purposes.

```
$ gpg --list-secret-keys --with-keygrip
$ gpg-connect-agent "DELETE_KEY <keygrip>" /bye
```

````{note}
Alternatively, you can remove the file directly via:
```shell
$ rm ~/.gnupg/private-keys-v1.d/<keygrip>.key
```
````
Ensure that the secret key is gone by listing them again. It will be denoted as `sec#` now.

```
$ gpg --list-secret-keys
```

## GPG Lifecycle - Yearly updates

Every year you need to import the master keypair secret key, generate a new subkey, and then remove the master secret
key again.

```
$ gpg --import user@key-private.gpg
```

Generate a new subkey.

```
$ gpg --edit-key user@key.com
gpg> addkey
select what kind of key you want: (4) RSA (sign only)
what keysize do you want? 4096
key is valid for? 2024-01-01

gpg> quit
save changes? y
```

Now export our keys once again to update our offline backup. These new files should overwrite our old files. We do not
need to keep the older files (generated last year) around any longer. **Store this offline**.

```
$ gpg --export --armor --output user@key.com-public.gpg
$ gpg --export-secret-keys --armor --output user@key.com-private.gpg
```

And finally remove our master secret key from the keyring (see more detailed description above).

```
$ gpg --list-secret-keys --with-keygrip
$ gpg-connect-agent "DELETE_KEY <keygrip>" /bye
```

## GPG Lifecycle - Import a public key

Obtain the public key from a trusted source. Then import it to your keyring.

```
$ gpg --import user@key-public.gpg
```

Now that the public key is in your GPG keyring you can verify signatures.

```{toctree}
:caption: Chapter 1

section1
section2
```
