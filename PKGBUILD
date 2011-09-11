# Maintainer: damir <damir@archlinux.org>

pkgname=dvd+rw-tools
pkgver=7.1
pkgrel=4
pkgdesc="dvd burning tools"
arch=('i686' 'x86_64')
license=('GPL')
url="http://fy.chalmers.se/~appro/linux/DVD+RW"
depends=('cdrkit' 'gcc-libs')
source=("http://fy.chalmers.se/~appro/linux/DVD+RW/tools/${pkgname}-${pkgver}.tar.gz"
        'dvd+rw-tools-7.0-dvddl.patch'
        'dvd+rw-tools-7.0-glibc2.6.90.patch'
        'dvd+rw-tools-7.0-wctomb.patch'
        'dvd+rw-tools-7.0-wexit.patch')
md5sums=('8acb3c885c87f6838704a0025e435871'
         '65d30aa98ff314f256d0a1afb9e3edf6'
         '1be5401035ca850edb7e522f22aead4b'
         '3ba1af063b30f942e1cd2004044702d3'
         'b2c66b6c6243b207fbe4f6ae34fa6cba')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  # patches from Gentoo/Fedora
  # see https://bugs.gentoo.org/257360, https://bugzilla.redhat.com/show_bug.cgi?id=426068
  # and https://bugzilla.redhat.com/show_bug.cgi?id=243036
  patch -p0 -i "${srcdir}/dvd+rw-tools-7.0-dvddl.patch"
  patch -p1 -i "${srcdir}/dvd+rw-tools-7.0-glibc2.6.90.patch"
  patch -p0 -i "${srcdir}/dvd+rw-tools-7.0-wctomb.patch"
  patch -p1 -i "${srcdir}/dvd+rw-tools-7.0-wexit.patch"

  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  install -m755 -d "${pkgdir}/usr/bin"
  install -m755 -d "${pkgdir}/usr/share/man/man1"

  install -m755 growisofs dvd+rw-booktype dvd+rw-format dvd+rw-mediainfo dvd-ram-control "${pkgdir}/usr/bin/"
  install -m644 growisofs.1 ${pkgdir}/usr/share/man/man1/growisofs.1
}
