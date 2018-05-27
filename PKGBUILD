# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-rc
pkgver=0.4.0.1
pkgrel=1
pkgdesc="A dependency-based init script management system"
arch=(x86_64)
url="http://skarnet.org/software/${pkgname}/"
license=('ISC')
install=s6-rc.install
depends=('skalibs' 'execline')
groups=('base' 's6-suite')
conflicts=('s6-rc-git')
source=("$pkgname::git+git://git.skarnet.org/s6-rc#tag=v${pkgver}")
#source=("$pkgname::git+git://git.skarnet.org/s6-rc#commit=$_commit")
#_commit=1821c6dda0ba20c92d47d5b57fe7f01cc1877151 # tag 0.3.0.1
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${srcdir}/${pkgname}
  ./configure --prefix=/usr \
			  --bindir=/usr/bin \
			  --sbindir=/usr/bin \
			  --datadir=/etc
  make
}

package() {
  cd ${srcdir}/${pkgname}

  DESTDIR=${pkgdir} make install
  
  # add doc
  install -dm 0755 $pkgdir/usr/share/doc/$pkgname/
  cp -R doc/* $pkgdir/usr/share/doc/$pkgname/
  
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:ft=sh ts=2 sw=2 et:
