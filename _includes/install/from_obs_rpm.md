## Official Crystal rpm repository

To install latest stable Crystal release from the official Crystal repository hosted on the [Open Build Service](https://build.opensuse.org) run in your command line:

```bash
curl -fsSL https://crystal-lang.org/install.sh | sudo bash
```

The install script accepts optional arguments to install or update to a release of another channel.

- `--version` with `major.minor` or `latest` values
- `--channel` with `stable`, `unstable`, or `nightly` value

```bash
curl -fsSL https://crystal-lang.org/install.sh | sudo bash -s -- --channel=nightly
```

You can find more detailed information at the [announcement post](/2021/04/30/new-apt-and-rpm-repositories/).

### Manual setup

Insert your distribution name and release as `{REPOSITORY}` in the following script and you are all set.
You can find available options on the [installation page at OBS](https://software.opensuse.org/download.html?project=devel%3Alanguages%3Acrystal&package=crystal).

```bash
cat > /etc/yum.repos.d/crystal.repo <<END
[crystal]
name=Crystal
type=rpm-md
baseurl=https://download.opensuse.org/repositories/devel:languages:crystal/{REPOSITORY}/
gpgcheck=1
gpgkey=https://download.opensuse.org/repositories/devel:languages:crystal/{REPOSITORY}/repodata/repomd.xml.key
enabled=1
END

```

Once the repository is configured you're ready to install Crystal:

```bash
sudo yum install crystal
```

When a new Crystal version is released you can upgrade your system using:

```bash
sudo yum update crystal
```
