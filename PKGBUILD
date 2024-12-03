# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: l-koehler <lorenz.koehler@posteo.de>

_pkg=cmix
pkgname="${_pkg}"
pkgver=20
pkgrel=1
_pkgdesc=(
  "lossless data compression program aimed"
  "at optimizing compression ratio at the cost"
  "of high CPU/memory usage"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'armv7l'
  'armv6l'
  'mips'
  'powerpc'
  'pentium4'
  'i686'
)
_ns="byronkoll"
url="https://www.${_ns}.com/${_pkg}.html"
license=(
  'GPL-3.0-only'
)
options=(
  !debug
)
depends=()
makedepends=(
  'make'
)
optdepends=(
  'tar: compress multiple files by making a tarball'
)
_http="https://github.com"
_url="${_http}/${_ns}/${_pkg}"
_tar="${_pkg}-${pkgver}"
source=(
  "${_tar}.tar.gz::${_url}/archive/refs/tags/v${pkgver}.tar.gz"
)
sha256sums=(
  SKIP
)

build() {
  cd \
    "${_tar}"
  make
}

package() {
  cd \
    "${_tar}"
  mkdir \
    -p \
    "${pkgdir}/usr/bin"
  mv \
    "./${_pkg}" \
    "${pkgdir}/usr/bin"
}
