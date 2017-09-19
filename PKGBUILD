# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-boot
pkgver=0.1.6
pkgrel=2
pkgdesc="Necessary files to boot under S6 supervision suite"
arch=(x86_64)
url="http://obarun.org/"
license=('BEERWARE')
depends=('s6-rc' 's6' 's6-linux-utils' 's6-portable-utils' 's6-linux-init' 'util-linux' 'bash' 's6opts')
groups=(s6-suite)
install=s6-boot.install
backup=('usr/bin/init' 'etc/s6/stage2' 'etc/s6/stage3' 'etc/s6/stage2.tini'
		'etc/s6/reboot' 'etc/s6/poweroff' 'etc/s6/s6.conf' 'etc/s6/shutdown' 'etc/s6/data/scripts/s6.local'
		'etc/s6/compiled/current' 'etc/s6/compiled/previous')
source=("$pkgname::git+https://github.com/Obarun/${pkgname}#branch=dev")
#_commit=776956629caf8eb608c85242a49aa6bf3bb4a278  # tag 0.1.5
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=s6-boot.install


package() {
  cd ${srcdir}/${pkgname}
  
  make DESTDIR="$pkgdir" install
}

# vim:ft=sh ts=2 sw=2 et:
