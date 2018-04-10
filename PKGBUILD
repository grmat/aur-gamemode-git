# Maintainer: grmat <grmat@sub.red>

pkgname=gamemode-git
pkgdesc='Optimise Linux system performance on demand'
pkgver=1.0.r0.g4f14c80
pkgrel=1
arch=('x86_64')
url='https://github.com/FeralInteractive/gamemode'
license=('BSD')
depends=('systemd')
builddeps=('meson')

source=("${pkgname}::git+https://github.com/FeralInteractive/gamemode.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname}
  git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
  cd ${srcdir}/${pkgname}
  arch-meson build
  ninja -C build
}

package() {
  DESTDIR=${pkgdir} ninja -C ${srcdir}/${pkgname}/build install
}

