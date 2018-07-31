# Maintainer: Goutham Veeramachaneni <gouthamve[at]gmail.com>
# Contributor: Slashbunny <demodevil5[at]yahoo>

pkgname=prometheus-node-exporter-bin
pkgver=0.16.0
pkgrel=2
pkgdesc="Prometheus exporter for machine metrics (binary, not built from source)"
arch=('x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
url="https://github.com/prometheus/node_exporter"
license=('Apache')
depends=()
makedepends=()
provides=('prometheus-node-exporter')
conflicts=('prometheus-node-exporter')
source=('prometheus-node-exporter.service')
source_x86_64=("https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-amd64.tar.gz")
source_arm=("https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-armv5.tar.gz")
source_armv6h=("https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-armv6.tar.gz")
source_armv7h=("https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-armv7.tar.gz")
source_aarch64=("https://github.com/prometheus/node_exporter/releases/download/v${pkgver}/node_exporter-${pkgver}.linux-arm64.tar.gz")
sha256sums=('df4ef8a34999ac2acedead7a48e67da31e0b65a29e4570d3075cd8ca663cf1d0')
sha256sums_x86_64=('e92a601a5ef4f77cce967266b488a978711dabc527a720bea26505cba426c029')
sha256sums_arm=('18c91a0247f4bc97fb7cdd96502cd8a804a96f42a16357b39f43e28b3d2ac864')
sha256sums_armv6h=('f9518aea4fa7127122a6bf384ba8f70120deaaef75532749f1765cf6e25fd820')
sha256sums_armv7h=('b8bf44c025ec2c5210bdda185f8e72b29ccd3eb9be339b8dbf96835d4fc1965d')
sha256sums_aarch64=('c793e8278ec6a167a49518d72dd928361a045bd4c8b155a22d5b158dd3aea2ac')

package() {
    case "$CARCH" in
            'x86_64') ARCH='amd64';;
            'arm') ARCH='armv5';;
            'armv6h') ARCH='armv6';;
            'armv7h') ARCH='armv7';;
            'aarch64') ARCH='arm64';;
    esac
    cd "${srcdir}/node_exporter-${pkgver}.linux-${ARCH}"

    # Install Binary
    install -D -m0755 node_exporter \
        "${pkgdir}/usr/bin/prometheus_node_exporter"

    # Install SystemD Service File
    install -D -m0644 "${srcdir}/prometheus-node-exporter.service" \
        "${pkgdir}/usr/lib/systemd/system/prometheus-node-exporter.service"
}
