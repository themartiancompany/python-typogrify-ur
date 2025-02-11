# Maintainer: Jiachen Yang <farseerfc@gmail.com>
# AUR Maintainer: Chris Warrick <aur@chriswarrick.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=typogrify
pkgname="${_py}-${_pkg}"
pkgver=2.0.7
pkgrel=16
_pkgdesc=(
  'Filters to make caring'
  'about typography on the'
  'web a bit easier.'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_http="https://github.com"
_ns="mintchaos"
url="${_http}/${_ns}/${_pkg}"
license=(
  'BSD'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
  "${_py}-smartypants"
)
makedepends=(
  "${_py}-setuptools"
)
_pypa="https://files.pythonhosted.org/packages/source"
source=(
  "${_pypa}/${_pyname:0:1}/${_pyname}/${_pyname}-${pkgver}.tar.gz"
  "jinja-3.1.patch"
)
sha256sums=(
  '8be4668cda434163ce229d87ca273a11922cb1614cb359970b7dc96eed13cb38'
  'bda1b57207e46d3d399b830e603493505bcbc1414342b823d81345a4ac8a4cfb'
)

prepare() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  patch \
    -Np1 \
    -i \
    "../jinja-3.1.patch"
}

package() {
  cd \
    "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" \
    "setup.py" \
    install \
    --root="${pkgdir}/" \
    --optimize=1
  install \
    -Dm644 \
    "LICENSE.txt" \
    "${pkgdir}/usr/share/licenses/${pkgbase}/LICENSE"
}

# vim:set ts=2 sw=2 et:
