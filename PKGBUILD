pkgname=mobalytics-desktop
pkgver=1.103.5
pkgrel=1
pkgdesc="Repackaged Mobalytics client. May break when new releases are pushed. Please open an issue if this is the case."
arch=('x86_64')
license=("MIT")
depends=("nodejs>=16 electron>=19")
makedepends=("yarn" "git")
source=(
    "git+https://github.com/sekwah41/mobalytics-repackager.git"
)
sha256sums=('SKIP')

build() {
    cd $srcdir/mobalytics-repackager
    yarn
}

package() {
    mkdir -p $pkgdir/usr/bin
    mkdir -p -m 0755 $pkgdir/opt/$pkgname/
    install -Dm0644 -t "$pkgdir/usr/share/applications/" "../mobalytics-desktop.desktop"
    for size in 24 32 48 64 128 256 512; do
        install -Dm644 "$srcdir/mobalytics-repackager/app/resources/icons/${size}x${size}.png" \
            "${pkgdir}/usr/share/icons/hicolor/${size}x${size}/apps/mobalytics-desktop.png"
    done
    mv $srcdir/mobalytics-repackager/app/* $pkgdir/opt/$pkgname/
}
