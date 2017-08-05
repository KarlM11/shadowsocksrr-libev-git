pkgname=shadowsocksrr-libev-git
pkgver=2.4.1.366.g035d4b9-1
pkgrel=1
pkgdesc='A fork of ShadowsocksR. May different from original version.'
arch=('i686' 'x86_64')
url='https://github.com/shadowsocksrr/shadowsocksr-libev'
license=('GPL')
depends=('libcap' 'mbedtls' 'libev' 'libsodium'
         'udns' 'pcre' 'libcorkipset' 'libbloom')
makedepends=('git' 'gcc' 'autoconf' 'libtool' 'automake' 'make' 'zlib' 'openssl' 'asciidoc' 'xmlto')
options=('docs' '!strip')
conflicts=('shadowsocksr-libev')
source=('git+https://github.com/shadowsocksrr/shadowsocksr-libev.git'
        shadowsocksr-libev-redir@.service
        shadowsocksr-libev-server@.service
        shadowsocksr-libev-tunnel@.service
        shadowsocksr-libev@.service
        )
sha1sums=('SKIP'
          'SKIP'
          'SKIP'
          'SKIP'
          'SKIP')


_gitname='shadowsocksr-libev'

pkgver() {
  cd "$_gitname"
  git describe --tags | sed 's/-/./g'
}

build() {
  cd "$_gitname"
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR="$pkgdir/" install
  install -Dm644 "$srcdir/shadowsocks-libev-redir@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev-redir@.service"
  install -Dm644 "$srcdir/shadowsocks-libev-server@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev-server@.service"
  install -Dm644 "$srcdir/shadowsocks-libev-tunnel@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev-tunnel@.service"
  install -Dm644 "$srcdir/shadowsocks-libev@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev@.service"
}




