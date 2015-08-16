# Maintainer: Antonio Rojas <nqn1976 @ gmail.com>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Timothée Ravier <tim@siosm.fr>

pkgname=libnm-qt-git
pkgver=r645.c71bc0c
pkgrel=1
pkgdesc='Qt-only wrapper for NetworkManager DBus API'
arch=('i686' 'x86_64')
url='https://projects.kde.org/projects/extragear/libs/libnm-qt'
license=('LGPL')
depends=('qt5-base' 'networkmanager')
makedepends=('extra-cmake-modules' 'git')
conflicts=('libnm-qt5' 'libnm-qt5-git')
provides=('libnm-qt5')
replaces=('libnm-qt5-git')
source=("git://anongit.kde.org/libnm-qt.git")
sha256sums=('SKIP')

pkgver() {
  cd libnm-qt
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../libnm-qt \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
