# $Id: PKGBUILD 83746 2010-06-22 18:50:54Z jgc $
# Contributor: 
# Maintainer: 

pkgname=xournal-image-patched
pkgver=0.4.5
pkgrel=5
pkgdesc="Notetaking and sketching application patched for inserting images."
arch=('i686' 'x86_64')
url="http://math.mit.edu/~auroux/software/xournal/"
license=('GPL')
depends=('libgnomecanvas>=2.30.1' 'ghostscript' 'shared-mime-info' 'poppler-glib>=0.14.0' 'hicolor-icon-theme' 'desktop-file-utils')
conflicts=('xournal')
install=xournal.install
source=("http://math.mit.edu/~auroux/software/xournal/xournal-${pkgver}.tar.gz" 'applypatch' 'xournal-0.4.5-sjg-image-rev7.patch' 'pdf-export-64.patch' 'poppler-api.patch')

md5sums=('795e4396ded2b67766eb2926be1fb4a9'                                                                                                                    
         '9db34a33094d9a670849462c03f44a29'                                                                                                                    
         '7eacd642f9d656e4c0e670d0c1b2335a'                                                                                                                    
         'a46b4ad4e4adeef64ac7ee19ce5b70f3'                                                                                                                    
         '85bdcc610eaf3b4a004b058de52d7d5c')                                                                                                                   
sha1sums=('390cb275774469ed1b04b7268dd625bd456c895e'
          'bb08b81f37daad0abb592c73d94746f724ba71c7'
          'd2b547be65c59d94271a4f1a51b8b08c35f01156'
          'f23f53b9f69ba8a5773c53d7bca99abf9d8504f8'
          '5aedd5610b42df96e964bb889d4bf0831c2080bc')
build() {
  cd "${srcdir}/xournal-${pkgver}"

  cp "${srcdir}/applypatch" .
  cp "${srcdir}/xournal-0.4.5-sjg-image-rev7.patch" .
  ./applypatch xournal-0.4.5-sjg-image-rev7.patch
  cd "${srcdir}/xournal-${pkgver}"
  patch -p1 -i ../pdf-export-64.patch # from xournal CVS, see FS#21693
  patch -p1 -i ../poppler-api.patch
  ./configure --prefix=/usr LIBS="-lm -lX11 -lz"
  make
  make DESTDIR="${pkgdir}" install desktop-install
}
