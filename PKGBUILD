# Maintainer: Sandro Dias Pinto Vitenti <sandro@isoftware.com.br>

pkgname=numcosmo
pkgver0=0.12.0
pkgver=0.12.0rc5
pkgrel=1
pkgdesc="Numerical Cosmology - NumCosmo"
url="https://savannah.nongnu.org/projects/numcosmo/"
arch=('i686' 'x86_64')
license=('GPL')
depends=('glib2' 'gsl' 'gmp' 'mpfr' 'sundials' 'sqlite3' 'fftw' 'nlopt' 'cfitsio' 'gtk-doc' 'libcuba' 'gobject-introspection')
optdepends=('atlas-lapack' 'levmar-atlas')
provides=('numcosmo')
conflicts=('numcosmo')
source=("http://download.savannah.gnu.org/releases/numcosmo/$pkgname-$pkgver.tar.gz")
md5sums=("02c23c521fb0e28adb906815e0f6ab45")

build() {
  NCPU=`grep processor /proc/cpuinfo | wc -l`

  mkdir -p $srcdir/$pkgname-$pkgver-build
  cd $srcdir/$pkgname-$pkgver-build
  
  msg "Configuring ..."
  $srcdir/$pkgname-$pkgver0/configure --prefix=/usr --enable-shared --with-thread-pool-max=$NCPU
  make
}

package() {
  cd $srcdir/$pkgname-$pkgver-build
  make DESTDIR=$pkgdir install
}
