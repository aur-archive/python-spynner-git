# Maintainer: Allen Li <darkfeline@abagofapples.com>

pkgname=python-spynner-git
pkgver=20120723
pkgrel=1
pkgdesc="Programmatic web browsing module with AJAX support for Python 3"
arch=('any')
url="http://pypi.python.org/pypi/spynner/1.10"
license=('GPL3')
depends=('python3' 'libxml2' 'pyqt')
makedepends=('git')

_gitname=spynner
_gitroot='git://github.com/darkfeline/spynner.git'

build() {
    cd "$srcdir"
    msg "Connecting to GIT server..."
    if [ -d $_gitname ] ; then
        cd $_gitname && git pull origin
        msg "The local files are updated."
    else
        git clone -b devel --depth=1 $_gitroot
    fi
    msg "GIT checkout done or server timeout"

    cd $srcdir/spynner
    python3 setup.py build
}

package() {
    cd "$srcdir/spynner"
    python3 setup.py install --root="$pkgdir"
}
