# $Id$
# Maintainer: Mark Coolen <mark.coolen@gmail.com>
# Contributor: Allan McRae <allan@archlinux.org>
# Contributor: Eric Belanger <eric@archlinux.org>
# Contributor: John Proctor <jproctor@prium.net>

pkgname=pcre-old
pkgver=8.21
pkgrel=3
pkgdesc="A library that implements Perl 5-style regular expressions. Old version for Dansguardian compatibility."
arch=('i686' 'x86_64')
url="http://www.pcre.org/"
license=('BSD')
depends=('gcc-libs')
options=('!libtool')
source=(http://ftp.exim.llorien.org/pcre/pcre-${pkgver}.tar.bz2{,.sig})
md5sums=('0a7b592bea64b7aa7f4011fc7171a730'
         '4768871445dff956e620a9e902b4db55')

build() {
  cd "${srcdir}"/pcre-${pkgver}
  
  [ "${CARCH}" = "x86_64" ] && export CFLAGS="${CFLAGS} -fPIC"
  ./configure --prefix=/opt/pcre-old --enable-jit \
    --enable-utf8 --enable-unicode-properties
  make
}

check() {
  cd "${srcdir}"/pcre-${pkgver}
  make check
}

package() {
  cd "${srcdir}"/pcre-${pkgver}
  make DESTDIR="${pkgdir}" install

  # grep uses pcre, so we need the libs in /lib
  #install -dm755 "${pkgdir}"/lib
  #mv "${pkgdir}"/usr/lib/libpcre.so.* "${pkgdir}"/lib/
  #ln -sf /lib/libpcre.so.0 "${pkgdir}"/usr/lib/libpcre.so
  
  #install -Dm644 LICENCE "${pkgdir}"/usr/share/licenses/pcre/LICENSE
}
