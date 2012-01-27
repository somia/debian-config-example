This is an example of how to use `debian-config-packaging` for creating
custom Debian/Ubuntu configurations.

The `base` and `igbinary` directories are built into
`packages/example-config-base_1.0-gXXXXXXX_all.deb` and
`packages/example-config-igbinary_1.3-gYYYYYYY_all.deb`.  All directories which
are added to Git (except `debian`) are built.  The package version is deduced
from the current Git commit; the `1` in `1.3` comes from the latest Git tag
name and the `3` comes from the number of successive commits until the latest
commit which has changed the package directory.

### Base package features

- Requires distcc to be installed.
- Replaces `/etc/default/distcc` with a custom version and restarts distccd.
- Un-diverts `/etc/crontab` (as if it had been diverted by an older version of
  this package, but now we want the original).

### Igbinary package features

- Requires PHP and our base configuration to be installed.
- Provides a custom-built version of the igbinary PHP extension.
- Writes a notice to syslog that php5-fpm might need restarting.

### Unused features

- `/usr/share/keyrings/*.gpg` files will be automatically registered with APT.

