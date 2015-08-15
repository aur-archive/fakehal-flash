# Maintainer: Cedric Staub <cs+aur {at} cssx.cc>

pkgname=fakehal-flash
pkgver=0.5.14
pkgrel=7
pkgdesc="A stripped-down version of HAL to allow playing of DRM-protected Flash content, created by Warren Togami."
arch=('i686', 'x86_64')
url="http://wtogami.blogspot.ch/2012/12/amazon-instant-video-on-fedora-16.html"
license=('GPL')
depends=()
makedepends=('rpmextract')
options=('emptydirs')
install=fakehal-flash.install

source=(
    "http://wtogami.fedorapeople.org/fakehal/Fedora/18/${CARCH}/fakehal-${pkgver}-${pkgrel}.fc18.${CARCH}.rpm"
    "http://wtogami.fedorapeople.org/fakehal/Fedora/18/${CARCH}/fakehal-libs-${pkgver}-${pkgrel}.fc18.${CARCH}.rpm"
    )

if [[ "$CARCH" == "i686" ]]; then
    sha256sums=(
        'b1e1a9621688175966c5d3b36d24b757658f7a69a590d428a772b20f2f7be203'
        '6c9792790b5404303160aa3b8c4459c5c3901999b462080a0c283d70e7553a31'
        )
elif [[ "$CARCH" == "x86_64" ]]; then
    sha256sums=(
        '9578e3471415af3fb8b24fd3848e06141971907bad6f56d15613550551fc893f'
        '8c6d7df5b4bd2f88a539c00d3a0c8bb875d66b12cb3bcbcb0c43f96971657ada'
        )
fi

build() {
    rpmextract.sh fakehal-${pkgver}-${pkgrel}.fc18.${CARCH}.rpm
    rpmextract.sh fakehal-libs-${pkgver}-${pkgrel}.fc18.${CARCH}.rpm
}

package() {
    cp -Rp "$srcdir"/{var,etc} "$pkgdir"/
    mkdir -p "$pkgdir"/usr
    cp -Rp "$srcdir"/usr/bin "$pkgdir"/usr
    cp -Rp "$srcdir"/usr/sbin/* "$pkgdir"/usr/bin
    cp -Rp "$srcdir"/usr/libexec "$pkgdir"/usr
    cp -Rp "$srcdir"/usr/share "$pkgdir"/usr
    cp -Rp "$srcdir"/lib "$pkgdir"/usr/lib
    chmod 755 "$pkgdir"/var/cache/hald
    mkdir -p "$pkgdir"/usr/share/hal/fdi/preprobe
    mkdir -p "$pkgdir"/etc/hal/fdi/preprobe
    mkdir -p "$pkgdir"/usr/share/hal/fdi/information
    mkdir -p "$pkgdir"/etc/hal/fdi/information
    mkdir -p "$pkgdir"/usr/share/hal/fdi/policy
    mkdir -p "$pkgdir"/etc/hal/fdi/policy
}
