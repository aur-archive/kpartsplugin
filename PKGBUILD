# Maintainer: birdflesh <antkoul at gmail dot com>
# Contributor: Frikilinux <frikilinux at frikilinux.com.ar>
pkgname=kpartsplugin
pkgver=20110823
pkgrel=2
pkgdesc="This plugin uses KDE's KParts to embed file viewers into non-KDE browsers"
arch=('i686' 'x86_64')
url="http://www.unix-ag.uni-kl.de/~fischer/kpartsplugin/"
license=('GPL3' 'BSD')
depends=('kdelibs')
makedepends=('automoc4' 'cmake')
source=("${url}${pkgname}-${pkgver}.tar.bz2" "LICENSE")
md5sums=('d134198ff2f05ba414719920030ea71b'
         'c4cc811349e40e9f34e77e27b902ad96')

build(){
  sed -i 's/nsbrowser/mozilla/g' ${pkgname}-${pkgver}/CMakeLists.txt
  cd ${srcdir}
  mkdir build
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd ${srcdir}/build
  make DESTDIR=${pkgdir} install
  install -Dm644 "${srcdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENCE"
}