# Maintainer: Ahmad Hasan Mubashshir <ahmubashshir@gmail.com>

pkgname=bootsplash-theme-manjaro-green-git
_pkgname=bootsplash-manjaro-green
pkgver=r3.1ae68da
pkgrel=1
pkgdesc="Bootsplash Theme 'Manjaro green'"
arch=('any')
url="https://github.com/ahmubashshir/bootsplash-manjaro-green"
license=('GPL')
makedepends=('coreutils')
builddepends=('imagemagick')
options=(
	'!libtool'
	'!emptydirs'
)
source=("git+file://$PWD")
validpgpkeys=('B5AC9A5E093F60A29AA1692F4CC9A8013A65E7D4')
md5sums=('SKIP')

prepare()
{
	cd "${_pkgname}"
	git checkout master
}
build() {
	cd "${_pkgname}"
	sh ./bootsplash-manjaro-green.sh
}
pkgver()
{
	cd "${_pkgname}"
	( set -o pipefail
		git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
		printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
	)
	pkgrel=$(git diff --shortstat|cut -d' ' -f2)
}
package() {
	cd "${_pkgname}"
	install -Dm644 "bootsplash-manjaro-green" "$pkgdir/usr/lib/firmware/bootsplash-themes/manjaro-green/bootsplash"
	install -Dm644 "bootsplash-manjaro-green.initcpio_install" "$pkgdir/usr/lib/initcpio/install/bootsplash-manjaro-green"
}
