# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.
#Maintainer: Abouzakaria <zkariakov@gmail.com>
pkgname=quefm
pkgver=0.2.1
pkgrel=1
epoch=
pkgdesc="A lightweight file manager for Linux desktops built in Qt."
arch=('x86_64')
url="https://github.com/git-fal7/$pkgname"
license=('GPL')
groups=()
depends=('qt5-svg' 'file' 'udisks2' 'imagemagick' 'ffmpeg')
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
#source=("$pkgname-$pkgver.tar.gz")
source=("$pkgname::git+$url.git")
md5sums=("SKIP")
validpgpkeys=()

prepare() {
	cd "$pkgname"
	
}

build() {
	cd "$srcdir/$pkgname"
	qmake "elokab-files-manager.pro" \
    PREFIX=/usr \
    QMAKE_CFLAGS_RELEASE="${CFLAGS}"\
    QMAKE_CXXFLAGS_RELEASE="${CXXFLAGS}"
	make
}

check() {
	cd "$pkgname"
	make -k check
}

package() {
	cd "$pkgname"
	make DESTDIR="$pkgdir/" install

    
    make INSTALL_ROOT="${pkgdir}"/ install || return 1
    find "$pkgdir" -type d -print0 | xargs -0 chmod -R 755
    find "$pkgdir" -type f -print0 | xargs -0 chmod -R 644
    chmod 755 "$pkgdir/usr/bin/elokab-fm"
    chmod 755 "$pkgdir/usr/bin/elokab-fa"

}
