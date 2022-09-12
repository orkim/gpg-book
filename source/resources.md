# Resources

## Documentation

The [official documentation](https://www.gnupg.org/gph/en/manual.html) for [GnuPG](https://www.gnupg.org)

The [GnuPG Blog](https://www.gnupg.org/blog/index.html) is a good place to check for new posts.

The [offical mailing lists](https://www.gnupg.org/documentation/mailing-lists.html) (especially the `gnupg-users` list)
is a good place to read or participate in discussions.

The specification is [RFC-4880](https://datatracker.ietf.org/doc/html/rfc4880) and is worth a read for all the details.

[Configuration options](https://www.gnupg.org/documentation/manuals/gnupg/GPG-Configuration-Options.html) for GnuPG

[Esoteric options](https://www.gnupg.org/documentation/manuals/gnupg/GPG-Esoteric-Options.html) for GnuPG

## Third Party Resources

[The Call of the Open Sidewalk](https://articles.59.ca/doku.php?id=pgpfan:index) has a full section called `PGP FAN`
with many interesting and informational articles.

## Books

O'Reilly published [PGP: Pretty Good Privacy](https://www.amazon.com/PGP-Pretty-Privacy-Simson-Garfinkel/dp/1565920988)
in 1995. (ISBN-10: 1565920988 / ISBN-13: 978-1565920989)

No Starch Press
published [PGP & GPG: Email for the Practical Paranoid](https://www.amazon.com/PGP-GPG-Email-Practical-Paranoid/dp/1593270712)
in 2006. ( ISBN-10: 1593270712 / ISBN-13: 978-1593270711 )

## Guides

The [Debian Wiki](https://wiki.debian.org/GnuPG) entry on GnuPG offers some good advice. There are additional pages on
[subkeys](https://wiki.debian.org/Subkeys) and [offline master keys](https://wiki.debian.org/OfflineMasterKey) worth
reading.

Alex Cabal has a guide called [Creating the Perfect GPG Keypair](https://alexcabal.com/creating-the-perfect-gpg-keypair)
that is a great starting point.

The [drduh YubiKey Guide](https://github.com/drduh/YubiKey-Guide) is a great resource for hardware keys. Some
recommended settings are now default in more recent versions of GnuPG.

**DEPRECATED** -
riseup.net [OpenPGP Best Practices](https://riseup.net/en/security/message-security/openpgp/gpg-best-practices)

[Signing keys](https://carouth.com/articles/signing-pgp-keys/) guide with single/multiple UIDs.

## Importing signatures from Keyservers (SKS)

```{note}
[WKD](https://wiki.gnupg.org/WKD) is now suggested for hosting your own key pairs.
```

It's broke. Basically, see the
[stackexchange](https://security.stackexchange.com/questions/219844/why-is-debian-not-showing-the-gpg-signatures-on-keys-that-arch-linux-is)
question here and the follow-up answers.  [GnuPG release 2.2.17](https://lwn.net/Articles/793288/) ignores all
key-signatures received from keyservers. There are some distributions that have patched this out.

Use something along the lines of the following to override if it hasn't been patched out on your distribution:

```shell
$ gpg2 --keyserver-options no-self-sigs-only,no-import-clean --keyserver hkp://keyserver.ubuntu.com --recv-keys 0xDEADBEEFCAFEBABE
```

## Keyservers

- http://keys.gnupg.net
- https://keys.openpgp.org
- https://keyserver.ubuntu.com
- https://pgp.mit.edu
- https://keybase.io
- https://keyoxide.org

## The GnuPG Book Links

These are useful links when authoring content for `The GnuPG Book` and has nothing to do with GnuPG.

- [Sphinx Documentation](https://www.sphinx-doc.org/en/master/)
- [MyST Parser](https://myst-parser.readthedocs.io/en/v0.15.1/index.html) used to process Markdown
- [sphinx-book-theme](https://sphinx-book-theme.readthedocs.io/en/stable/index.html) theme for Sphinx