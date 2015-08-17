#Maintainer: Alex Ferrando <alferpal@gmail.com>
#Contributor: Diego José <diegoxter1006@gmail.com>
pkgname=tyrs-git
pkgver=20120924
pkgrel=1
pkgdesc="Tyrs is a twitter and identi.ca client based on curse."
arch=('any')
url="https://github.com/Nic0/tyrs"
license=('GPL')
depends=('python2-twitter' 'python2-distribute' 'python2-distutils-extra'
'gettext' 'python2-oauth2' 'python2-urwid')
makedepends=('git')
conflicts=('tyrs')
replaces=('tyrs')
install='tyrs.install'

_gitroot="https://github.com/Nic0/tyrs.git"
_gitname="tyrs"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  python2 setup.py build

}

package() {
  cd "$srcdir/$_gitname-build"
  python2 setup.py install --prefix=/usr --root="$pkgdir"
} 
