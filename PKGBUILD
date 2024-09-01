# Maintainer: Bodo Schulz <bodo@boone-schulz.de>

pkgname=icingadb
pkgver=1.1.1
pkgrel=1
pkgdesc='Icinga configuration and state database'
arch=('x86_64')
license=('GPL-2.0')
url='https://icinga.com/docs/icinga-db'

install='icingadb.install'

source=(
  # https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_1.0.0-1.bullseye_amd64.deb"
  # https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_1.1.0-1+debian11_amd64.deb
  "${pkgname}-${pkgver}-${CARCH}.deb::https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_${pkgver}-${pkgrel}+debian12_amd64.deb"
  "${pkgname}-${pkgver}-Release::https://packages.icinga.com/debian/dists/icinga-bullseye/Release"
  "${pkgname}-${pkgver}-Release.sig::https://packages.icinga.com/debian/dists/icinga-bullseye/Release.gpg"
)

sha512sums=(
  "df3579c44215a49a1efaf8938a1e46fbc5d3c907cca44999d9f9812fc4f0336d42731884e3af5610e72b836a057d431960e2a8ea33d757d66a3c4972311b581e"
  "SKIP"
  "SKIP"
)

validpgpkeys=(
  "F51A91A5EE001AA5D77D53C4C6E319C334410682"
)

package() {
  cd "${srcdir}"

  tar -xf data.tar.xz -C "${pkgdir}"

  install -D --mode=0755 "${pkgdir}/lib/systemd/system/icingadb.service"  "${pkgdir}/usr/lib/systemd/system/icingadb.service"
  install -D --mode=0755 "${pkgdir}/usr/sbin/icingadb" "${pkgdir}/usr/bin/icingadb"

  chmod 0750 ${pkgdir}/etc/icingadb

  rm --recursive --force "${pkgdir}/lib"
  rm --recursive --force "${pkgdir}/usr/sbin"
}
