# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-boot
pkgver=0.1.6
pkgrel=1
pkgdesc="Necessary files to boot under S6 supervision suite"
arch=(x86_64)
url="http://obarun.org/"
license=('BEERWARE')
depends=('s6-rc' 's6' 's6-linux-utils' 's6-portable-utils' 's6-linux-init' 'util-linux' 'bash')
optdepends=('s6opts: Manager services helper')
groups=(s6-suite)
install=s6-boot.install
backup=('usr/bin/init' 'etc/s6/stage2' 'etc/s6/stage3' 'etc/s6/stage2.tini'
		'etc/s6/reboot' 'etc/s6/poweroff' 'etc/s6/s6.conf' 'etc/s6/shutdown' 'etc/s6/data/scripts/s6.local'
		'etc/s6/compiled/current' 'etc/s6/compiled/previous'
		'etc/s6-serv/enabled/rc/compiled/current' 'etc/s6-serv/enabled/rc/compiled/previous'
		'etc/s6-serv/enabled/rc/compiled/Default.src')
source=("$pkgname::git+https://github.com/Obarun/${pkgname}#commit=$_commit")
_commit=776956629caf8eb608c85242a49aa6bf3bb4a278  # tag 0.1.5
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal
install=s6-boot.install


package() {
  cd ${srcdir}/${pkgname}
  
  # install s6-serv/available directory
  for i in s6-serv/available/*;do
		install -dm 0755 "$pkgdir/etc/$i"
		unset i
  done
  
  # install s6-serv/enabled 
  install -dm 0755 "$pkgdir/etc/s6-serv/available/classic"
  install -dm 0755 "$pkgdir/etc/s6-serv/enabled/classic"
  install -dm 0755 "$pkgdir/etc/s6-serv/enabled/rc/compiled"
  cp -a s6-serv/enabled/rc/compiled/Default "$pkgdir/etc/s6-serv/enabled/rc/compiled/Default"
  ln -s /etc/s6-serv/enabled/rc/compiled/Default "$pkgdir/etc/s6-serv/enabled/rc/compiled/current"
  ln -s /etc/s6-serv/enabled/rc/compiled/Default "$pkgdir/etc/s6-serv/enabled/rc/compiled/previous"
  ln -s /etc/s6-serv/enabled/rc/source/default "$pkgdir/etc/s6-serv/enabled/rc/compiled/Default.src"
  
  install -dm 0755 "$pkgdir/etc/s6-serv/enabled/rc/source"
  
  for i in s6-serv/enabled/rc/source/default/*;do
		install -dm 0755 "$pkgdir/etc/$i"
		for j in $i/*; do
			install -Dm 0644 $j "$pkgdir/etc/$i"
			unset j
		done
		unset i
  done    
  
  # install script files for boot
  install -Dm 0755 "init" "$pkgdir/usr/bin/init"
  install -Dm 0755 "stage2" "$pkgdir/etc/s6/stage2"
  install -Dm 0755 "stage2.tini" "$pkgdir/etc/s6/stage2.tini"
  install -Dm 0755 "stage3" "$pkgdir/etc/s6/stage3"
  install -Dm 0644 "s6.conf" "$pkgdir/etc/s6/s6.conf"
  
  #install script for control the machine 
  install -Dm 0755 "poweroff" "$pkgdir/etc/s6/poweroff"
  ln -s /etc/s6/poweroff "$pkgdir/usr/bin/poweroff" 
  install -Dm 0755 "reboot" "$pkgdir/etc/s6/reboot"
  ln -s /etc/s6/reboot "$pkgdir/usr/bin/reboot"
  install -Dm 0755 "shutdown" "$pkgdir/etc/s6/shutdown"
  ln -s /etc/s6/shutdown "$pkgdir/usr/bin/shutdown"
  
  # install env directory
  for i in dev proc pts run shm sys; do
		install -dm 0755 "$pkgdir/etc/s6/filesystem-env/$i"
		for j in filesystem-env/$i/*; do
			install -Dm 0644 $j "$pkgdir/etc/s6/filesystem-env/$i"
			unset j
		done
		unset i
  done
  
  for i in DEST DESTRC DESTUSER PATH S6CONF SRC SRCRC TEMPLATE TERM; do
		install -Dm 0644 "env/${i}" "$pkgdir/etc/s6/env/${i}"
  done
   
  # make data/scripts directory
  install -Dm 0755 "data/scripts/s6.local" "$pkgdir/etc/s6/data/scripts/s6.local"
  ln -s /etc/s6/data/scripts/s6.local "$pkgdir/etc/s6.local"
  
  # install service directory for boot
  for i in rc/*; do
		install -dm 0755 "$pkgdir/etc/s6/$i"
		for j in $i/*; do
			install -Dm 0644 $j "$pkgdir/etc/s6/$i"
			unset j
		done
		unset i
  done
  
  # install service directory for init file
  install -dm 0755 "$pkgdir/etc/s6/classic/service"
  install -dm 0755 "$pkgdir/etc/s6/classic/uncaught-logs"
  
  for i in classic/service/*; do
		install -dm 0755 "$pkgdir/etc/s6/$i"
		for j in $i/*;do
			install -Dm 0755 $j "$pkgdir/etc/s6/$i"
			unset j
		done
		unset i
  done
  
  install -dm 0755 "$pkgdir/etc/s6/classic/service/.s6-svscan"
  for i in classic/service/.s6-svscan/*; do
		install -Dm 0755 $i "$pkgdir/etc/s6/$i"
  done
  
  # install default database
  install -dm 0755 "$pkgdir/etc/s6/compiled/"
  cp -a compiled/default "$pkgdir/etc/s6/compiled/default"
  
  # install needed link for s6opts
  ln -sf /etc/s6/compiled/default "$pkgdir/etc/s6/compiled/current"
  ln -sf /etc/s6/compiled/default "$pkgdir/etc/s6/compiled/previous"
  
  # zsh completion
  install -Dm 0644 "$srcdir/$pkgname/_s6-svc" "$pkgdir/usr/share/zsh/site-functions/_s6-svc"
  
  # create symlinks for s6.conf files
  ln -sf /etc/s6/s6.conf "$pkgdir/etc/s6.conf"
  
  install -Dm 0644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:ft=sh ts=2 sw=2 et:
