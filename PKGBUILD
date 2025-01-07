# Maintainer: Bodo Schulz <bodo@boone-schulz.de>

pkgname=icingadb
pkgver=1.2.1
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
  'ae9cf9cb3bac4e2c392c830e6d85c010ef06c8167bb759c2dc3502a59d055697dee0e497627c75e3dac0d981e68e088c637094c1a6a82538a2000511aaa13dcd'
  'SKIP'
  'SKIP'
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
