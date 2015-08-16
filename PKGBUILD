# Contributor: Cyril Lashkevich <notorca at gmail dot com>

pkgname=kchmviewer-qt
pkgver=6.0
pkgrel=4
pkgdesc="A .chm files (MS HTML help file format) viewer"
arch=('i686' 'x86_64')
url="http://kchmviewer.sourceforge.net/"
license=('GPL')
depends=('chmlib' 'qtwebkit')
options=('libtool')
install=kchmviewer.install
source=(http://downloads.sourceforge.net/kchmviewer/kchmviewer-$pkgver.tar.gz 'kchmviewer.desktop')

md5sums=('940fdeeb5f50cdd0d0611f7a13e003f9'
         'b7dadf261aefee5c4bd90391ece0a5b9')

build() {
    cd ${srcdir}/kchmviewer-$pkgver

    qmake-qt4
    make || return 1
    install -D -m755 ${srcdir}/kchmviewer-$pkgver/bin/kchmviewer \
    ${pkgdir}/usr/bin/kchmviewer || return 1

    #icon file
    install -D -m644 ${srcdir}/kchmviewer-$pkgver/packages/kchmviewer.png \
    ${pkgdir}/usr/share/pixmaps/kchmviewer.png || return 1

    #desktop file
    install -D -m644 ${srcdir}/kchmviewer.desktop\
    ${pkgdir}/usr/share/applications/kchmviewer.desktop || return 1

    #msits.protocol file provided by kdegraphics package
    rm -rf ${pkgdir}/usr/share/kde4 || return 1
    #kio_msits.so file provided by kdegraphics package - FS#14376
    rm -rf ${pkgdir}/usr/lib || return 1
}
