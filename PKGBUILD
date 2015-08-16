# Contributor: Maciej Sitarz <macieks@freesco.pl>

pkgname=hyphen-pl
pkgver=20060726
pkgrel=1
pkgdesc="Polish hyphenation rules"
arch=('any')
url="http://wiki.services.openoffice.org/wiki/Dictionaries"
license=('LGPL')
optdepends=('hyphen: offers hyphenation library functions')
source=(http://pl.openoffice.org/pliki/hyph_pl_PL.zip)
md5sums=('e015c046f60437d39223b1253b78a4e2')

build() {
	cd "$srcdir"
	bsdtar -xf hyph_pl_PL.zip
}

package() {
	cd "$srcdir"

	install -dm755 ${pkgdir}/usr/share/hyphen
	install -m644 hyph_pl_PL.dic ${pkgdir}/usr/share/hyphen

	# the symlinks
	install -dm755 ${pkgdir}/usr/share/myspell/dicts
	pushd $pkgdir/usr/share/myspell/dicts
	for file in $pkgdir/usr/share/hyphen/*; do
		ln -sv /usr/share/hyphen/$(basename $file) .
	done
	popd

	# docs
	install -dm755 ${pkgdir}/usr/share/doc/$pkgname
	install -m644 README_hyph_pl_PL.txt $pkgdir/usr/share/doc/$pkgname

}
