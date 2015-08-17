# Maintainer: Dylan <dylan@hashflo.net>

pkgname='potcoin-daemon'
pkgver=0.8.6.4
pkgrel=2
arch=('i686' 'x86_64')
url="http://potcoin.info/"
makedepends=('boost' 'miniupnpc')
license=('MIT')
source=("https://github.com/potcoin/potcoin/archive/master.tar.gz"
        "potcoind@.service"
)

sha256sums=('SKIP'
            'b7dd336530976ae43ad77b9c60aa32595ed5ad02edb5a72716a0fe4025103e87')

pkgdesc="Peer-to-peer network based digital 420 currency (daemon)."
depends=(boost-libs miniupnpc openssl)
conflicts=(potcoin)

build() {
  cd "$srcdir/potcoin-master"
  CXXFLAGS="$CXXFLAGS -DBOOST_VARIANT_USE_RELAXED_GET_BY_DEFAULT=1"
  make -f makefile.unix -C src CXXFLAGS="$CXXFLAGS" USE_UPNP=1
}

package() {
  install -Dm644 potcoind@.service "$pkgdir/usr/lib/systemd/system/potcoind@.service"
  cd "$srcdir/potcoin-master"
  install -Dm755 src/potcoind "$pkgdir"/usr/bin/potcoind
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

