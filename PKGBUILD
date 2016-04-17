# Maintainer: Nikita Zhukov <yacuken@gmail.com>
pkgname=scratchbox2-git
_pkgname=scratchbox2
pkgver=2.3.90+git2.r19.gc597127
pkgrel=1
pkgdesc='Transparent cross compiling environment'
arch=('i686' 'x86_64')
url='https://git.merproject.org/mer-core/scratchbox2'
license=('LGPL2')
source=('scratchbox2::git+https://git.merproject.org/mer-core/scratchbox2.git'
        'libc-lock.patch')
md5sums=('SKIP'
         'aaded2ff43f4b5c4259f803a52ea019d')

pkgver() {
    cd ${_pkgname}
    git describe --long | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
    cd ${srcdir}/${_pkgname}
    patch -p0 < ../libc-lock.patch
}

build() {
    cd ${srcdir}/${_pkgname}/${_pkgname}
    ./autogen.sh
    ./configure CFLAGS=-fPIC
    make
}

package() {
    cd ${srcdir}/${_pkgname}/${_pkgname}
    install -d -m 0755 ${pkgdir}/usr
    make install prefix=${pkgdir}/usr
}
