# Maintainer: Pier Luigi Fiorini <pierluigi.fiorini@gmail.com>

pkgname=qt5-pim-git
pkgver=v5.0.0.beta1.r156.g18e3d74
pkgrel=2
pkgdesc="A cross-platform application and UI framework (QtPim)"
groups=('qt' 'qt5')
arch=('i686' 'x86_64')
url="http://qt-project.org/"
license=('GPL3' 'LGPL')
depends=('qt5-base' 'qt5-declarative')
makedepends=('git')
replaces=('qt5-qtpim-git')
conflicts=('qt5-pim')
provides=('qt5-pim')
options=('!libtool')
_gitroot="git://code.qt.io/qt/qtpim.git"
_gitname="qt5-pim"
source=(${_gitname}::${_gitroot})
md5sums=('SKIP')

pkgver() {
	cd ${srcdir}/${_gitname}
    ( set -o pipefail
      git describe --long --tags 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
      printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
    )
}

build() {
	cd ${srcdir}/${_gitname}
	qmake
	make
}

package() {
	cd ${srcdir}/${_gitname}
	make INSTALL_ROOT="${pkgdir}" install
}
