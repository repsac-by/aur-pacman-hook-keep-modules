pkgname='pacman-hook-keep-modules'
pkgver=5
pkgrel=2
pkgdesc='To keep the kernel modules after an update or removal until reboot'
arch=('any')
license=('MIT')
source=(
	'10-keep-modules-pre.hook'
	'10-keep-modules-post.hook'
	'keep-modules-wipe.service'
	'keep-modules'
)
sha1sums=('d40cca5954556af0f0b0f8cca34bd317894e5a55'
          'b1958cfdb16c461e94e7a8c4f538abc330dbcf6f'
          'c57711ba86954062197271178a22dda232642b9b'
          '7329183dd183c5c2dc119b249eeefb9bae5572bb')

package() {
	depends=(
		'pacman'
		'systemd'
		'coreutils'
	)

	install -Dt "$pkgdir/usr/share/libalpm/scripts" -m755 keep-modules
	install -Dt "$pkgdir/usr/share/libalpm/hooks"   -m644 10-keep-modules-{pre,post}.hook
	install -Dt "$pkgdir/usr/lib/systemd/system"    -m644 keep-modules-wipe.service

	# #Enable service
	install -d "$pkgdir/usr/lib/systemd/system/multi-user.target.wants"
	ln -st "$pkgdir/usr/lib/systemd/system/multi-user.target.wants" ../keep-modules-wipe.service
}
