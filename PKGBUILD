# Maintainer: ksj <podhorsky.ksj@gmail.com>
# Contributor: Cilyan Olowen <gaknar@gmail.com>

_gitname='lxterminal'
pkgname=lxterminal-gtk3-git
pkgver=20140128
pkgrel=1
pkgdesc="VTE-based terminal emulator (part of LXDE)"
arch=('i686' 'x86_64')
url="http://lxde.org/"
license=('GPL')
depends=('gtk3' 'fontconfig' 'libx11' 'glib2' 'vte3')
makedepends=('pkgconfig' 'intltool' 'git')
conflicts=('lxterminal')
provides=('lxterminal')
groups=('lxde-git')
source=('git://lxde.git.sourceforge.net/gitroot/lxde/lxterminal')
md5sums=(SKIP)

pkgver() {
    cd $_gitname
    git log -1 --format='%cd' --date=short | tr -d -- '-'
}

build() {
	cd $srcdir/$_gitname
  
	# Generating Makefile, etc
	./autogen.sh

	./configure --prefix=/usr \
				--sysconfdir=/etc \
				--localstatedir=/var \
				--enable-gtk3
}

package() {
	cd $srcdir/$_gitname
	
	make SUBDIRS="src data po"
	make SUBDIRS="src data po" DESTDIR="${pkgdir}" install
}
