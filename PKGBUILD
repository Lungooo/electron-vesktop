# Maintainer: Sophie Langer <sophie@lungoo.dev>

pkgver=36
pkgrel=1
epoch=1
pkgname=electron-vesktop
pkgdesc='Meta package providing the latest available stable Electron build (Vesktop patched)'
arch=(any)
url='https://electronjs.org'
license=(MIT)
depends=("electron$pkgver-vesktop")

package() {
	mkdir -p "$pkgdir/usr/bin" "$pkgdir/usr/lib"
	ln -sf "${depends[0]}" "$pkgdir/usr/bin/$pkgname"
	ln -sf "${depends[0]}" "$pkgdir/usr/lib/$pkgname"
}
