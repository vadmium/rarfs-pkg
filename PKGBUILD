# Contributor: Jacques de Laval <jac.dl@gawab.com>
pkgname=rarfs
pkgver=7
pkgrel=1
pkgdesc="RARfs is a fuse module, able to mount non compressed rar archives."
arch=('i686' 'x86_64')
url="http://rarfs.sourceforge.net/"
license=('GPL')
depends=('fuse')
makedepends=('subversion')
source=()
md5sums=()


_svntrunk=https://rarfs.svn.sourceforge.net/svnroot/rarfs/trunk/rarfs/
_svnmod=rarfs

build() {
  cd $startdir/src
  
  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi
                
  msg "SVN checkout done or server timeout"
  msg "Starting make..."
                   
  cd $_svnmod
  
  #update automake links
  ln -sf /usr/share/automake-1.11/install-sh install-sh
  ln -sf /usr/share/automake-1.11/depcomp depcomp
  ln -sf /usr/share/automake-1.11/missing missing
  
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR=$startdir/pkg/ install
                                      
  rm -rf $startdir/src/$_svnmod-build
}
