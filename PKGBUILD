# Author: Daniel Kozak <kozzi11@gmail.com>
_pkgver=938c3b2c65061fea562fe382f0e888c69822cc8a
pkgname=mongofill-hhvm
pkgver=938c3b2c65
pkgrel=2
pkgdesc="Mongo extension for HHVM"
arch=('i686' 'x86_64')
url="https://github.com/mongofill/$pkgname"
license=(PHP)
depends=('hhvm' 'libbson')
makedepends=('git' 'cmake' 'libbson')
source=("git+https://github.com/mongofill/$pkgname.git")

pkgver() {
    cd "$srcdir/$pkgname"
    git describe --long --tags | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
    cd "${srcdir}/${pkgname}"
    ./build.sh
}

package() {
    cd "${srcdir}/${pkgname}"
    make DESTDIR="${pkgdir}" install
    mv "$pkgdir"/usr/lib/hhvm/extensions/20150212/mongo.so "$pkgdir"/usr/lib/hhvm/extensions/mongo.so
    rmdir "$pkgdir"/usr/lib/hhvm/extensions/20150212
}

sha256sums=('SKIP')
# vim:set ts=2 sw=2 et:
