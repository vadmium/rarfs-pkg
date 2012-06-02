# Contributor: Jacques de Laval <jac.dl@gawab.com>
pkgname=rarfs
pkgver=0.0.10
_fullver="$pkgname-$pkgver"
pkgrel=1
pkgdesc="A Fuse module for mounting uncompressed Rar archives"
arch=('i686' 'x86_64')
url="http://rarfs.sourceforge.net/"
license=('GPL')
depends=(fuse gcc-libs)

# Standard Source Forge integration:
source+=("http://downloads.sourceforge.net/$pkgname/$pkgname-$pkgver.tar.gz")
sha1sums+=(ca9bbe7ca65bd05915a7d4e4f58d00e759b888b9)
md5sums+=(b708df36a7ac276a5189083ba003d37c)

build() {
  cd "$srcdir/$_fullver"
  ./configure --prefix=/usr
  make
}

package() {
  make -C "$srcdir/$_fullver" DESTDIR="$pkgdir" install
}
