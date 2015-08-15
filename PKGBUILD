# Maintainer: speps <speps at aur dot archlinux dot org>

_name=freemedforms
pkgname=freediams
pkgver=0.8.2.1
_pkgver=0.8.2
pkgrel=1
pkgdesc="The FreeMedForms Pharmaceutical Drugs Prescriber"
arch=(i686 x86_64)
url="http://www.freemedforms.com/en/"
license=('GPL')
depends=('qt5-base')
makedepends=('qt5-svg')
install="$pkgname.install"
source=("http://freemedforms.googlecode.com/files/${_name}fullsources-$pkgver.tgz")
md5sums=('1a5103f95ab2ee536a5e471015cf98d1')

build() {
  cd "$srcdir/$_name-$_pkgver"

  qmake freediams.pro -r -config release \
    "CONFIG+=LINUX_INTEGRATED" \
    "INSTALL_ROOT_PATH=$pkgdir/usr/" \
    "LOWERED_APPNAME=freediams"

  make
}

package() {
  cd "$srcdir/$_name-$_pkgver"
  make install

  # fix doc directories exec bit
  chmod a+x "$pkgdir/usr/share/doc/$_name-project/$pkgname/"{en,fr}/{html,}
  chmod a+x "$pkgdir/usr/share/$pkgname/forms"{,/subforms/emergencies}
}

# vim:set ts=2 sw=2 et:
