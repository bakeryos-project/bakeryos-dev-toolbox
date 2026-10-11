# Maintainer: smtdfc <me.smtdfc@gmail.com>

pkgname=bakeryos-dev-toolbox
pkgver=1.0.1
pkgrel=1
pkgdesc="A post-installation setup wizard and developer environment installer for BakeryOS."
arch=('x86_64')
url="https://github.com/bakeryos-project/bakeryos-dev-toolbox"
license=('GPL-3.0-or-later')
depends=('gtk4' 'libadwaita' 'glib2' 'zenity')
makedepends=('base-devel' 'meson' 'rust' 'cargo' 'blueprint-compiler' 'clang' 'lld' 'gcc')
source=()
sha256sums=()
options=(!debug !strip)

build() {
    cd $startdir

    export CFLAGS=""
    export CXXFLAGS=""
    export LDFLAGS=""
    export RUSTFLAGS=""

    arch-meson . build
    meson compile -C build
}

package() {
    install -d "${pkgdir}/usr/local/bin"
    cp -a ${srcdir}/scripts/* ${pkgdir}/usr/local/bin
    cd $startdir
    meson install -C build --no-rebuild --destdir "$pkgdir"

    install -Dm644 "${startdir}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
