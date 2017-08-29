# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=s6-rc
pkgver=0.2.1.2
pkgrel=1
pkgdesc="A dependency-based init script management system"
arch=(x86_64)
url="http://skarnet.org/software/${pkgname}/"
license=('ISC')
install=s6-rc.install
depends=('skalibs' 'execline')
groups=(s6-suite)
conflicts=('s6-rc-git')
source=("$pkgname::git+git://git.skarnet.org/s6-rc#commit=$_commit")
_commit=bc0746bebb7adcb18ed8e32aebef10ca8f555479 # tag 0.2.1.2
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
