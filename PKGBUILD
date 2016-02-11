# Maintainer: Michael Williams <michael@mgwsoftware.com>
pkgname=libucl
pkgver=0.7.3
pkgrel=1
epoch=
pkgdesc="Universal configuration library parser"
arch=('i686' 'x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/vstakhov/libucl"
license=('BSD')
groups=()
depends=('curl')
makedepends=('autoconf' 'automake' 'libtool' 'lua')
checkdepends=()
optdepends=('lua: Lua bindings')
install=
changelog=
source=("https://github.com/vstakhov/libucl/archive/$pkgver.tar.gz"
	"ucl-conflict.patch")
md5sums=('1fb6850cb2172b3388eb53191e2fcd4e'
	'2a3f475638be29d9b95117e36e9c4ace')

prepare() {
	cd "${srcdir}"/${pkgname}-${pkgver}
	patch -Np1 -i $srcdir/ucl-conflict.patch
}

build() {
	cd "$pkgname-$pkgver"
	./autogen.sh
	./configure --prefix=/usr --enable-urls --enable-lua --enable-utils --enable-signatures
	make
}

check() {
	cd "$pkgname-$pkgver"
	make -k check
}

package() {
	cd "$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install
	install -D -m644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
