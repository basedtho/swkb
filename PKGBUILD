# Maintainer: Alexandr Bogomyakov (ultradesu) <ab@hexor.ru>

pkgname=swkb
pkgver=0.2.0
pkgrel=1
pkgdesc="swkb"
url="https://github.com/house-of-vanity/swkb.git"
arch=($CARCH)
license=(WTFPL custom)
depends=(sway)
makedepends=(cargo git)
source=("git+https://github.com/house-of-vanity/$pkgname")
sha512sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  git describe --long --tags | awk -F '-' '{print $1}'| sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd "$srcdir/$pkgname"
  cargo fetch --target $CARCH-unknown-linux-gnu
}

build() {
  cd "$srcdir/$pkgname"
  cargo build --release --frozen --all-targets --all-features
}

package() {
  cd "$srcdir/$pkgname"
  install -Dt "$pkgdir/usr/bin" target/release/$pkgname
}
