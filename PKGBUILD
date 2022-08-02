# Maintainer: Bodo Schulz <bodo@boone-schulz.de>

pkgname=icingadb
pkgver=1.0.0
pkgrel=1
pkgdesc='Icinga configuration and state database'
arch=('x86_64')
license=('GPL-2.0')
url='https://icinga.com/docs/icinga-db'

install='icingadb.install'

source=(
  "${pkgname}-${pkgver}-x86_64.deb::https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_${pkgver}-${pkgrel}.bullseye_amd64.deb"
  "${pkgname}-${pkgver}-Release::https://packages.icinga.com/debian/dists/icinga-bullseye/Release"
  "${pkgname}-${pkgver}-Release.sig::https://packages.icinga.com/debian/dists/icinga-bullseye/Release.gpg"
)

sha512sums=(
  "9cd4f31f9db3ffabab7c4b170cbfa2d688f2c561e1970534767e1f99cd1ec5d2bc4a734a3881504dc9c91e2e1aa408263eca6f6780ac8a25ed867b4ad887825c"
  "aea51a5f12a0ab19c9348026b3e585faa5c56a0edf6a0538d7814f8681fe0e64ef3310b85ef4bd08e1ff31bcb98015ecfe822fc2d5e1bb38282f5cc0b0e7d8c0"
  "314970650520780e05e61e9034012287e024f797b1abdefff6bd97ed699e82f3a321fc9acf0241531d1d461209c1bfbdf46ce9aaa98091272a9cf3949c0137e7"
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
