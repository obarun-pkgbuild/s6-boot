# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-boot
pkgver=0.1.8+4+g95e0747
pkgrel=1
pkgdesc="Necessary files to boot under S6 supervision suite"
arch=(x86_64)
url="http://obarun.org/"
license=('BEERWARE')
depends=('s6-rc' 's6' 's6-linux-utils' 's6-portable-utils' 's6-linux-init' 'util-linux' 'bash' 's6opts')
groups=(s6-suite)
install=s6-boot.install
backup=('etc/s6/s6.conf' 'etc/s6/data/scripts/s6.local'
		'etc/s6/compiled/current' 'etc/s6/compiled/previous')
#source=("$pkgname::git+https://github.com/Obarun/${pkgname}#commit=$_commit")
source=("$pkgname::git+https://github.com/Obarun/${pkgname}#branch=dev")
#_commit=5153867c5c87aca34f5f15771a11ffd52f70d018  # tag 0.1.7
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=s6-boot.install

pkgver() {
	cd "${pkgname}"
	
	git describe --tags | sed -e 's:-:+:g;s:^v::'
}

package() {
  cd "${pkgname}"
  
  make DESTDIR="$pkgdir" install
}

# vim:ft=sh ts=2 sw=2 et:
