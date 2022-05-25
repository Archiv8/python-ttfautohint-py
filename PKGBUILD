#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>

_langname="python"
_relname="ttfautohint-py"

pkgname="${_langname}-${_relname}"
pkgver=0.5.0
pkgrel=1
pkgdesc='A Python wrapper for ttfautohint, a free auto-hinter for TrueType fonts'
url="https://github.com/fonttools/ttfautohint-py"
arch=(
  "x86_64"
)
license=(
  "MIT"
)
depends=(
  "python"
)
makedepends=(
  "python-pip"
)
_py=py2.py3
_wheel="${_relname/-/_}-${pkgver}-${_py}-none-manylinux_2_17_$CARCH.manylinux2014_$CARCH.whl"
source=("https://files.pythonhosted.org/packages/${_py}/${_relname::1}/${_relname}/${_wheel}")
sha256sums=('f63b3944e279ceca056f77d1120c7bb6ef53a77b3bb8effb75f96be899900313')

package() {

  export PIP_CONFIG_FILE=/dev/null

  pip install --isolated --root="${pkgdir}" --ignore-installed --no-deps ${_wheel}

  python -O -m compileall "${pkgdir}"
}
