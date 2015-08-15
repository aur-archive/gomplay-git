# Maintainer: Daniel Wallace daniel.wallace@gatech.edu
pkgname=gomplay-git
pkgver=20120628
pkgrel=2
pkgdesc="handels the gomstreamer.py"
arch=('i686' 'x86_64')
url="https://github.com/danielwallace/gomplay"
license=('GPL')
depends=(gomstreamer-git)
makedepends=('git')
provides=(gomplay)
install=$pkgname.install
source=($pkgname.install)
md5sums=('4de0a22bd47e8c5b1496fc43223019a6')

_gitroot=git://code.gtmanfred.com/gomplay.git
_gitname=gomplay

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone -b gomplay "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"
  #mkdir ${pkgdir}/usr/share/gomrc
  install -D -m755 "${srcdir}/${_gitname}/${_gitname}" "${pkgdir}/usr/bin/${_gitname}"
  install -D -m644 "${srcdir}/${_gitname}/gomrc" "${pkgdir}/usr/share/gomplay/gomrc"
}

# vim:set ts=2 sw=2 et:
