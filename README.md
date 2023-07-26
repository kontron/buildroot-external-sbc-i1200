![Kontron](docs/logo.png)

# Kontron 3.5"-SBC-I1200 Buildroot External

This [external buildroot layer][1] provides a basic support package for the
3.5"-SBC-I1200 board. It is an extenstion to buildroot which is provided
outside of the standard buildroot tree.

## Install System Dependencies

The external is tested on Debian 12. The following system build
dependencies are required (by buildroot itself).

```
apt install which sed make binutils build-essential gcc g++ \
bash patch gzip bzip2 perl tar cpio python unzip rsync file \
bc wget libncurses6-dev git subversion
```

This layer was tested on buildroot version 2023.05.x.

## Build

You have to clone buildroot and this layer. When building, use the
appropriate defconfig in the `buildroot-external-sbc-i1200/configs`
directory.

```
git clone git://git.buildroot.org/buildroot -b 2023.05.1
git clone https://github.com/kontron/buildroot-external-sbc-i1200.git
mkdir build
cd build
make -C ../buildroot BR2_EXTERNAL=../buildroot-external-sbc-i1200 O=`pwd` kontron_sbc_i1200_defconfig
make
```

## Build an image with the orignal Mediatek kernel

You can also build an image with the original Mediatek kernel v5.15.x. For
this use the config `kontron_sbc_i1200_mtk_defconfig`.

Please note that this config uses a GIT branch as a source for the linux
kernel. Buildroot caches the downloads of each package. Unfortunately, this
caching doesn't work correctly with GIT branches and the packages isn't
redownloaded when the branch will have new commits. To circumvent this
buildroot restriction you have to manually delete the downloaded linux
tarballs/git repository from your download directory (`BR2_DL_DIR`),
probably located inside if your base buildroot directory.

```
rm -rf buildroot/dl/linux
```

## License

This project is licensed under the [GPLv2][2] or later with exceptions. See
the `COPYING` file for more information. Buildroot is licensed under the
[GPLv2][2] or later with exceptions.


[1]: https://buildroot.org/downloads/manual/manual.html#outside-br-custom
[2]: https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html
