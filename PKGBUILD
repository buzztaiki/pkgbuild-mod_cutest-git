# $Id: pkgbuild-mode.el,v 1.23 2007/10/20 16:02:14 juergen Exp $
# Maintainer: Taiki Sugawara <sugawara_t@ariel-networks.com>
_pkgname=mod_cutest
pkgname=$_pkgname-git
pkgver=0.r30.405f14a
pkgrel=1
pkgdesc="CuTest integration for Apache module development"
arch=('i686' 'x86_64')
url="https://github.com/oasynnoum/mod_cutest"
license=('custom')
depends=('apache' 'libapreq2')
makedepends=('git')
source=("$_pkgname::git+https://github.com/oasynnoum/mod_cutest.git")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  # Use number of revisions since beginning of the history
  printf "0.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  cd $srcdir/$_pkgname

  patch -p1 < $startdir/Makefile.patch
}

build() {
  cd $srcdir/$_pkgname

  ./configure --prefix=/usr
  make
}

package() {

  cd $srcdir/$_pkgname

  make DESTDIR=$pkgdir/ install

  install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE
}

# vim:set ts=2 sw=2 et:
