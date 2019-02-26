# Maintainer: surefire <surefire@cryptomile.net>

pkgname='pacman-hook-keep-modules'
pkgver=3
pkgrel=5
pkgdesc='Keep modules'
arch=('any')
license=('MIT')
source=(
	'10-keep-modules-pre.hook'
	'10-keep-modules-post.hook'
	'keep-modules-wipe.service'
	'keep-modules'
)
depends=('pacman')
sha1sums=('a9e4f9bb033a7f2eaef374717174b1aabd93c6ac'
          'ad0c642bbfb348567893357bd89f88d0399372a6'
          '602dd68a8ec2118405b4501c4fecda5b6ed358ed'
          'f596bff4e89d0d0f239b8b3a79d3f0aa578f1581')

package() {
	install -Dt "$pkgdir/usr/share/libalpm/scripts" -m755 keep-modules
	install -Dt "$pkgdir/usr/share/libalpm/hooks"   -m644 10-keep-modules-{pre,post}.hook
	install -Dt "$pkgdir/usr/lib/systemd/system"    -m644 keep-modules-wipe.service

	# #Enable service
	install -d "$pkgdir/usr/lib/systemd/system/basic.target.wants"
	ln -st "$pkgdir/usr/lib/systemd/system/basic.target.wants" ../keep-modules-wipe.service
}
