pkgname=sdl2-net-hg
pkgver=234
pkgrel=1
pkgdesc="hg build of sdl2_net"
arch=('i686' 'x86_64')
url="http://www.libsdl.org"
license=('MIT')
depends=(sdl2-hg)
makedepends=(mercurial)
optdepends=()
provides=(sdl2_net)
conflicts=(sdl2_net)
options=(!libtool)
source=('sdl2_net::hg+http://hg.libsdl.org/SDL_net')
md5sums=('SKIP')

_hgrepo="sdl2_net"

pkgver() {
  cd "${srcdir}/${_hgrepo}"
  hg identify -n
}

prepare() {
  mkdir "${srcdir}/${_hgrepo}/build"
}

build() {
  cd "${srcdir}/${_hgrepo}/"
  ./autogen.sh
  cd "${srcdir}/${_hgrepo}/build"
  ../configure --disable-static --prefix=/usr
  make
}

package() {
  cd "${srcdir}/${_hgrepo}/build"
  make DESTDIR="${pkgdir}/" install
  install -Dm644 ../COPYING.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
## vim:set ts=2 sw=2 et:
