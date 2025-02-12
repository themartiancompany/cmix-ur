# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
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
_ns="byronknoll"
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
  'a95b0d7430d61b558731e7627f41e170cb7802d1a8a862f38628f8d921dc61b2'
)

_cxx_get() {
  local \
    _cxx \
    _ccxs=()
  _cxxs=(
    "cxx"
    "g++"
    "clang++"
  ) 
  _cxx="$( \
    command \
      -v \
      "${_cxxs[@]}" | \
      awk \
        '{print $1}')"
  echo \
    "${_cxx}"
}

prepare() {
  local \
    _cxx
  _cxx="$( \
    _cxx_get)"
  sed \
    -i \
    "s%clang++-17%${_cxx}%"  \
    "${srcdir}/${_tar}/makefile"
}

build() {
  local \
    _cxx
  _ccx="$( \
    _cxx_get)"
  cd \
    "${_tar}"
  export \
    CC="${_cxx}" \
    CXX="${_cxx}"
  CC="${_cxx}" \
  CXX="${_cxx}" \
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
