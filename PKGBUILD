# Maintainer: Boqun Feng <boqun.feng@gmail.com>

pkgname=beignet-git
_gitname=beignet
pkgver=b140444
pkgrel=5
pkgdesc="OpenCL Implemenation for Intel IvyBridge*"
arch=('i686' 'x86_64')
url="http://cgit.freedesktop.org/beignet/"
license=('LGPL')
groups=()
depends=('clang>=3.3' 'llvm>=3.3' 'ncurses' 'ocl-icd')
makedepends=('git' 'cmake>=2.6' 'llvm>=3.3' 'python2' 'ocl-icd')

#provides and conflicts with libcl since ICD loader is not support now
provides=('opencl-intel')
conflicts=('opencl-intel')
source=('beignet::git://anongit.freedesktop.org/beignet')
md5sums=('SKIP')

pkgver() {
  cd "${srcdir}/${_gitname}"
  git describe --always | sed 's|-|.|g'
}

build() {
  cd "${srcdir}/${_gitname}"
  sed -i '/install/d' "${srcdir}/${_gitname}/include/CMakeLists.txt"
  cmake -DCMAKE_BUILD_TYPE=Release -DPYTHON_EXECUTABLE:FILEPATH=/usr/bin/python2 -DCMAKE_INSTALL_PREFIX=/usr .
  make
}

package() {
  cd "${srcdir}/${_gitname}"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
