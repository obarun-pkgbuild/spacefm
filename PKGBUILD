# Maintainer: Eric Vidal <eric@obarun.org>
# Contributor: Danial (bytn) Spruce <bit@teknik.io>

pkgname=spacefm
pkgver=1.0.6
pkgrel=1
pkgdesc='Multi-panel tabbed file manager'
arch=('x86_64')
url="https://github.com/IgnorantGuru/spacefm"
license=('GPL3')
#install=$pkgname.install
depends=('libwebp' 'shared-mime-info' 'hicolor-icon-theme' 'desktop-file-utils' 'udevil' 'ffmpegthumbnailer' 'gtk3')
makedepends=('intltool' 'gettext')
optdepends=('lsof: device processes'
            'eject: eject media'
            'wget: plugin download'
            'gksu: perform as root functionality'
            'pmount: mount as non-root user'
            'udisks2: mount as non-root user'
            'spacefm-plugin-clamav')
source=("git+https://github.com/IgnorantGuru/spacefm.git#tag=$pkgver")
md5sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

prepare() {
    cd "$srcdir/$pkgname"
	./autogen.sh --prefix=/usr \
				 --sysconfdir=/etc \
				 --enable-fast-install=no \
                 --disable-startup-notification \
				 --with-gtk3 	
}

build() {
  cd "$srcdir/$pkgname"
  make 
}

package() {
  cd "$srcdir/$pkgname"
  make DESTDIR="$pkgdir" install
  install -Dm644 "COPYING" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

