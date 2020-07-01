# Maintainer: graysky <graysky AT archlinux DOT org>
# Maintainer: Armin K. <krejzi at email dot com>
# Contributor: Austin ( doorknob60 [at] gmail [dot] com )
# Contributor: Gaetan Bisson <bisson@archlinux.org>

_pkgname=broadcom-wl
pkgname=$_pkgname-bede-lts
pkgver=6.30.223.271
pkgrel=326
_pkgdesc='Broadcom 802.11abgn hybrid Linux networking device driver for linux-bede-lts'
_extramodules=5.4-BEDE-LTS-external
_current_linux_version=5.4.50
_next_linux_version=5.5
pkgdesc="${_pkgdesc}"
arch=('x86_64')
url='http://www.broadcom.com/support/802.11/linux_sta.php'
license=('custom')
makedepends=(
    "linux-bede-lts>=$_current_linux_version"
    "linux-bede-lts-headers>=$_current_linux_version"
    "linux-bede-lts<$_next_linux_version"
    "linux-bede-lts-headers<$_next_linux_version"
    "broadcom-wl-dkms>=$pkgver"
)
source=('modprobe.d')
sha512sums=('83502abcd1dbc04884b901cd09ffdbfe81131bcbc004d4d3751be53bc7e4416294ef501cd84e91457c10bf4f7c804841c80fbcf0aeda7f2183765cb2368995b5')

package() {
	depends=(
        "linux-bede-lts>=$_current_linux_version"
        "linux-bede-lts<$_next_linux_version"
    )

    local kernver=$(</usr/src/linux-bede-lts/version)
    local extradir="/usr/lib/modules/$kernver/extramodules"
    install -dm755 "${pkgdir}${extradir}/$_pkgname"
    cp -a "/var/lib/dkms/$_pkgname/kernel-$kernver-x86_64/module"/* \
        "${pkgdir}${extradir}/$_pkgname/"

	install -Dm644 "${srcdir}/modprobe.d" \
        "${pkgdir}/usr/lib/modprobe.d/broadcom-wl-bede.conf"
}
