# Merged with official ABS prison PKGBUILD by João, 2021/03/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: zan <zan$420blaze.it>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>
# Contributor: Antonio Rojas

pkgname=prison-git
pkgver=5.80.0_r299.ge2d0c4c
pkgrel=1
pkgdesc="A barcode API to produce QRCode barcodes and DataMatrix barcodes"
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(GPL)
depends=(qt5-base libdmtx qrencode)
makedepends=(git extra-cmake-modules-git doxygen qt5-tools qt5-doc qt5-declarative)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('qt5-declarative: QML bindings')
groups=(kf5-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
