# Maintainer: Isaiah Inuwa <isaiah dot inuwa at gmail com>
pkgname='cinny-matrix-git'
_pkgname='cinny'
pkgver=1.1.0.93.gdaa0015
pkgrel=1
arch=('x86_64')
url='https://cinny.in'
pkgdesc='A Matrix client focusing primarily on simple, elegant and secure interface.'
license=('MIT')
depends=()
makedepends=('npm>=6.14.11' 'nodejs>=14.6.0')
provides=('cinny')
source=(
  "$_pkgname::git+https://github.com/ajbura/cinny"
)
sha256sums=('SKIP')

pkgver() {
	cd $_pkgname/
	echo "$(grep '\s*"version":' package.json | cut -d\" -f4).$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build(){
  cd "$_pkgname"
  npm install
  npm run build
}

package() {
  pwd
  cd $_pkgname/
  pwd
  ls
  install -d -m755 "$pkgdir/usr/share/webapps/cinny/"
  find dist -maxdepth 1 -type f -exec install -D -m644 {} "$pkgdir/usr/share/webapps/cinny/" \;
  install -d -m755 "$pkgdir/usr/share/webapps/cinny/assets/"
  find dist -maxdepth 1 -type f -exec install -D -m644 {} "$pkgdir/usr/share/webapps/cinny/assets/" \;
}
