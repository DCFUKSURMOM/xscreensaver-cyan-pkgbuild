# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>
# Contributor: Eric Bélanger <eric@archlinux.org>

pkgname=xscreensaver-cyan
pkgver=6.15
pkgrel=1
pkgdesc='Screen saver and locker for the X Window System'
url='https://www.jwz.org/xscreensaver/'
arch=(x86_64 i686)
license=(LicenseRef-XScreenSaver)
depends=(
  at-spi2-core
  gdk-pixbuf2
  glib2
  glibc
  glu
  gtk3
  libcrypt.so
  libglvnd
  libjpeg-turbo
  libjpeg.so
  libpam.so
 
  libx11
  libxcrypt
  libxext
  libxft
  libxi
  libxinerama
  libxml2
  libxmu
  libxrandr
  libxt
  libxxf86vm
  pam
  perl-libwww
  wayland
  xdg-utils
  xorg-appres
)
makedepends=(
  bc
#  gdm ???
  intltool
  libxpm
 
 
)
optdepends=(
  'fortune-mod: for fortune file support (can be replaced with eg misfortune)'
  'gdm: for login manager support'
  'perl-lwp-protocol-https: for https support on networked demos'
  'words: for Web Collage demo'
)
backup=(
  etc/pam.d/xscreensaver
)
source=(https://github.com/DCFUKSURMOM/XScreenSaver-Cyan/archive/refs/tags/${pkgver}.tar.gz
	xscreensaver)
sha512sums=('SKIP'
	    'SKIP')

build() {
  cd XScreenSaver-Cyan-${pkgver}
  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --libexecdir=/usr/lib \
    --without-setuid-hacks \
    --with-pam \
    --with-login-manager \
    --with-gtk \
    --with-gl \
    --without-gle \
    --with-pixbuf \
    --with-jpeg
  make
}

package() {
  cd XScreenSaver-Cyan-${pkgver}
  install -d "${pkgdir}/etc/pam.d"
  make DESTDIR="${pkgdir}" install
  install -Dm 644 debian/copyright -t "${pkgdir}/usr/share/licenses/${pkgname}"
  install -Dm 644 "${srcdir}/xscreensaver" "${pkgdir}/etc/pam.d/xscreensaver"
  echo "NotShowIn=KDE;GNOME;" >> "${pkgdir}/usr/share/applications/xscreensaver-settings.desktop"
}

# vim: ts=2 sw=2 et:
