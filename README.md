curlbash: locally save and checksum/review before curl|bash-ing installers

# curlbash

Installing things by curling them to a shell probably isn't a great
practice security-wise, but several things can make it a little better.
This script caches the curl'd installer, can optionally verify a
checksum, and give the user a chance to review what was downloaded.

Consider it harm reduction for the command line.

curlbash is distributed under the ISC license.

# Dependencies

curlbash uses SHA-256 for hashing. It will check for `sha256` or
`sha256sum`, and use whichever is in the path. It also requires `curl`.

# Usage

    Usage: curlbash [-c] [-e SHA256] [-h] [-v] URL
      -c           ignore cache
      -e SHA256    expect this SHA256, or exit
      -h           print this help and exit
      -v           increase verbosity

# Examples

    $ curlbash -h

Print help.

    $ curlbash -e HASH URL

Download `URL`, and verify the SHA-256 hash for the downloaded file matches `HASH`.

    $ curlbash -c URL

Re-fetch `URL` (ignoring a locally cached copy).

# Portability

Despite the name, curlbash is targeted at `/bin/sh` for portability
reasons. A reasonable effort is made to test it with `bash`, `mksh`, `pdksh`,
`dash`, and other common shells that attempt to be POSIX-compliant /
compatible with the Bourne shell.

In other words, bash-isms are bugs.
