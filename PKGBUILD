# Contributer: giacomogiorgianni@gmail.com

pkgname=downverter-deb
name=downverter
pkgver=2.1
pkgrel=1
pkgdesc="Downverter is a free YouTube downloader."
arch=('i686' 'x86_64')
url="http://www.downverter.com/"
license=('Gratis')
depends=('qt4' 'lib32-libgcrypt' 'lib32-zlib' 'lame' 'libjpeg6-turbo' 'libtheora' 'lib32-orc')
install="$name.install"
#makedepends=('')

if [ "${CARCH}" = 'x86_64' ]; then
    ARCH='64'
    md5sums=('f5c285770bff0a7cda2576e5859612cb')
elif [ "${CARCH}" = 'i686' ]; then
    ARCH='32' 
    md5sums=('d67b9407a2764242b8049b5cc3aa259f')
fi
source=("http://www.downverter.com/Download/DownloadUbubtu64/$name-$ARCH.deb")

build() {
	cd ${startdir}/src
	tar -zxf ${startdir}/src/data.tar.gz
	cp -r ${startdir}/src/usr/ ${pkgdir}
	cp -r ${startdir}/src/opt/ ${pkgdir}
	# not compatible qt
	rm -- ${pkgdir}/opt/$name/libQt*
	rm -- ${pkgdir}/opt/$name/liba*
	install -Dm644 "$srcdir/opt/$name/${name}_logo_32.png" "$pkgdir/usr/share/pixmaps/${name}_logo.png"
	install -D -m644 "${srcdir}/opt/$name/Downverter.desktop" "${pkgdir}/usr/share/applications/${name}.desktop"
	sed -i "4s|app-x-downverter|/usr/share/pixmaps/${name}_logo.png|" "${pkgdir}/usr/share/applications/${name}.desktop"
}