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

## License

This project is licensed under the [GPLv2][2] or later with exceptions. See
the `COPYING` file for more information. Buildroot is licensed under the
[GPLv2][2] or later with exceptions.


[1]: https://buildroot.org/downloads/manual/manual.html#outside-br-custom
[2]: https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html
