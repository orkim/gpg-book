# git integration

## Before we begin

A private (secret) key must be present in your GPG keyring. If you don't have your keyring setup, see the
[GPG Key Lifecycle](../chapter1/index) to generate a new key.

## Configure git

First, find the secret subkey key long (16 character) keyid using the following command.

```shell
$ gpg --list-secret-keys --keyid-format=long
```

Force git to use the signing key that we say (the subkey). Notice that we put a trailing '!' on the key when setting the
key. This option is passed unchanged to gpg’s --local-user parameter, so you may specify a key using any method that gpg
supports.

```shell
$ git config --local user.signingkey "0123456789ABCD!"
```

## Signing by default

Set a **local repository** to sign commits automatically:

```shell
git config --local commit.gpgsign true
```

Or **globally** set git to sign commits automatically:

```shell
git config --global commit.gpgsign true
```

## Verifying signatures

Use the `--show-signature` argument to pass signatures to gpg for validation.

```shell
git log --show-signature
```

This will work with any alias you might use as well.

```shell
git alias
```

```{toctree}
:caption: Chapter 2

section1
section2
```
