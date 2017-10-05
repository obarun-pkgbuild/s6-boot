# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-boot
pkgver=0.1.8
pkgrel=3
pkgdesc="Necessary files to boot under S6 supervision suite"
arch=(x86_64)
url="http://obarun.org/"
license=('ISC')
depends=('s6-rc' 's6' 's6-linux-utils' 's6-portable-utils' 's6-linux-init' 'util-linux' 'bash' 's6opts' 'applysys')
groups=('s6-suite' 'base')
install=s6-boot.install
backup=('etc/s6/s6.conf' 'etc/s6/data/scripts/s6.local'
		'etc/s6/compiled/current' 'etc/s6/compiled/previous')
source=("$pkgname::git+https://github.com/Obarun/${pkgname}#commit=$_commit"
		'sysusers')
_commit=5153867c5c87aca34f5f15771a11ffd52f70d018  # tag 0.1.7
sha256sums=('SKIP'
            'f1212e1d121f75f349652d0a290305b70e69bf735ef7c1175e4d3ee5b2dd5e26')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=s6-boot.install

package() {
  cd "${pkgname}"
  
  make DESTDIR="$pkgdir" install
  
  install -Dm 0644 "$srcdir"/sysusers "$pkgdir"/usr/lib/sysusers.d/s6log.conf

}

# vim:ft=sh ts=2 sw=2 et:
