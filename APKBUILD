# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>

pkgname="glibc"
pkgver="2.19"
_pkgrel="0"
pkgrel="1"
pkgdesc="GNU C Library compatibility layer"
arch="x86_64"
url="https://github.com/makorne/alpine-pkg-glibc"
license="GPL"
source="https://github.com/makorne/docker-glibc-builder/releases/download/$pkgver-r$_pkgrel/glibc-bin-$pkgver-$_pkgrel-x86_64.tar.gz
nsswitch.conf
ld.so.conf"
subpackages="$pkgname-bin $pkgname-dev $pkgname-i18n"
triggers="$pkgname-bin.trigger=/lib:/usr/lib:/usr/glibc-compat/lib"

package() {
  mkdir -p "$pkgdir/lib" "$pkgdir/lib64" "$pkgdir/usr/glibc-compat/lib/locale" "$pkgdir"/etc
  cp -a "$srcdir"/usr "$pkgdir"
  cp "$srcdir"/nsswitch.conf "$pkgdir"/etc/nsswitch.conf
  cp "$srcdir"/ld.so.conf "$pkgdir"/usr/glibc-compat/etc/ld.so.conf
  rm "$pkgdir"/usr/glibc-compat/etc/rpc
  rm -rf "$pkgdir"/usr/glibc-compat/bin
  rm -rf "$pkgdir"/usr/glibc-compat/sbin
  rm -rf "$pkgdir"/usr/glibc-compat/lib/gconv
  rm -rf "$pkgdir"/usr/glibc-compat/lib/getconf
  rm -rf "$pkgdir"/usr/glibc-compat/lib/audit
  rm -rf "$pkgdir"/usr/glibc-compat/share
  rm -rf "$pkgdir"/usr/glibc-compat/var
  ln -s /usr/glibc-compat/lib/ld-linux-x86-64.so.2 ${pkgdir}/lib/ld-linux-x86-64.so.2
  ln -s /usr/glibc-compat/lib/ld-linux-x86-64.so.2 ${pkgdir}/lib64/ld-linux-x86-64.so.2
  ln -s /usr/glibc-compat/etc/ld.so.cache ${pkgdir}/etc/ld.so.cache
}

bin() {
  depends="$pkgname libgcc"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/bin "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/sbin "$subpkgdir"/usr/glibc-compat
}

i18n() {
  depends="$pkgname-bin"
  arch="noarch"
  mkdir -p "$subpkgdir"/usr/glibc-compat
  cp -a "$srcdir"/usr/glibc-compat/share "$subpkgdir"/usr/glibc-compat
}

md5sums="1569c5b69400405bc898330a1db1631b  glibc-bin-2.19-0-x86_64.tar.gz
5be984273de4203318c9c3fb0d4e9d2b  nsswitch.conf
0484678534996fdddef848544bd1a12d  ld.so.conf"
sha256sums="8966cf0c8e4a5083c10ce876fcdd4c1c1c75ade8ac8b272043336fdebfa00acb  glibc-bin-2.19-0-x86_64.tar.gz
3be94785355b4b363d1268f133e198323441eafa6017b2b1fed32ae279d685c7  nsswitch.conf
f8eec838bace59c29a5dc04550f60e3c7ba9f3a9df7b14dae36349ad90152e00  ld.so.conf"
sha512sums="52454944bd48bc146431e6e1bb21cc7c4424f016ae19562322dbbd597bc124fa08116eeaa4225eac7bfb6b1bf9436a7840faaf6b91bc0c4ba998cdddfccaae36  glibc-bin-2.19-0-x86_64.tar.gz
478bdd9f7da9e6453cca91ce0bd20eec031e7424e967696eb3947e3f21aa86067aaf614784b89a117279d8a939174498210eaaa2f277d3942d1ca7b4809d4b7e  nsswitch.conf
2912f254f8eceed1f384a1035ad0f42f5506c609ec08c361e2c0093506724a6114732db1c67171c8561f25893c0dd5c0c1d62e8a726712216d9b45973585c9f7  ld.so.conf"
