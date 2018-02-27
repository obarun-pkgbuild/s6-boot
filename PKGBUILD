# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-boot
pkgver=0.2.1
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
_commit=a9e36c549b8ba973f1631f15f59eea0bcce72d0c  # tag 0.2.1 database compilation with s6-rc 0.4.0.0
#source=("$pkgname::git+https://github.com/Obarun/${pkgname}#tag=v${pkgver}"
#		'sysusers')
sha256sums=('SKIP'
            'a9f226bfe8e80428eca71c4ef8b369467e20ad716fcf12f0779f7ddd6bc4a473')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=s6-boot.install

package() {
  cd "${pkgname}"
  
  make DESTDIR="$pkgdir" install
  
  install -Dm 0644 "$srcdir"/sysusers "$pkgdir"/usr/lib/sysusers.d/s6log.conf

}

