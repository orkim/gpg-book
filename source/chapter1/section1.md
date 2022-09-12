# Faketime

If trying to guard privacy, it might be desirable to adjust the `create date and time` when generating a new
certificate or subkey. This could also be true to override the date and time of when a message is encrypted or signed
(say to the nearest day) to help "leak" information. Below is a quick discussion on how several of the commands in the
previous section could make use of the `faketime` command.

Using `faketime` (on *nix OS's) will allow overriding the current time as presented to a process. We can use this to
present a time of our choosing to GnuPG to override the `create date` time on our generated certificates. In addition,
we can override the TZ environment variable (Linux shell) for overriding the system-wide timezone (i.e. to use UTC
instead).

The following is an example of how to modify the commands, if desired:

```
$ TZ=UTC faketime -f "2022-01-01 00:00:00" <command>
```

Where `<command>` would be `gpg --expert --full-generate-key` or similar.
