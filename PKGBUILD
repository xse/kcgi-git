# Maintainer: xse <elouan.pignet@gmail.com>
pkgname=kcgi-git
_pkgname=${pkgname%-*}
pkgver=0.10.2.0.gd8ade2b
pkgrel=1
pkgdesc="Minimal CGI and FastCGI library"
arch=("i686" "x86_64" "arm" "armv6h" "armv7h" "aarch64") # tested on i686, x86_64 and armv6h
url="http://kristaps.bsd.lv/kcgi/"
license=("custom:ISC") # included in source
depends=("libbsd") # libbsd depends on glibc and curl is included in base
makedepends=("git")
source=("git+https://github.com/kristapsdz/kcgi.git")
sha512sums=("SKIP")

pkgver() {
  cd "$_pkgname"
  git describe --long --tags | sed 's/^VERSION_//;s/-/./g;s/_/./g'
}

build() {
  cd "$_pkgname"
  ./configure PREFIX="$pkgdir/usr" BINDIR="$pkgdir/usr/bin" SHAREDIR="$pkgdir/usr/share" SBINDIR="$pkgdir/usr/bin"  INCLUDEDIR="$pkgdir/usr/include" LIBDIR="$pkgdir/usr/lib" MANDIR="$pkgdir/usr/share/man"
  make
}

check() {
  cd "$_pkgname"
  make regress
}

package() {
  cd "$_pkgname"
  make install
  install -Dm644 "LICENSE.md" "$pkgdir/usr/share/licenses/$_pkgname/LICENSE"
}
