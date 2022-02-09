# Maintainer: Bodo Schulz <bodo@boone-schulz.de>

pkgname=icingadb
pkgver=1.0.0
pkgdate=20211115
pkgid=1813
epoch=1
pkgrel=1
pkgdesc='Icinga configuration and state database'
arch=('x86_64')
license=('GPL-2.0')
url='https://icinga.com/docs/icinga-db'

install='icingadb.install'

source=(
  "${pkgname}-${pkgver}-x86_64.deb::https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_${pkgver}~rc2-${pkgrel}.bullseye_amd64.deb"
  "${pkgname}-${pkgver}-Release::https://packages.icinga.com/debian/dists/icinga-bullseye-testing/Release"
  "${pkgname}-${pkgver}-Release.sig::https://packages.icinga.com/debian/dists/icinga-bullseye-testing/Release.gpg"
)

sha512sums=(
  "5a678140ee71875e04ee509c089b010a0dce6fdd21d748ed2b05cafee99972ee737481e7df829b26579ec40323591375f91e7f62076937f8e821f1d6d445c41f"
  "4add7ab2456ed0ebf5605fc12501e1a5c39607eb9f94be77f32684ba871302fb89953d4ffb8dd960d11ebee99a735d47490dc348dc791d556041f9633d15ddaf"
  "5f1676ed92eeda51f3804b9d524bbadbe2a0e47e99a3ea0d2b2995cb2e4f1b849e0f380431df61a09b6f0c52a72c598ca674994321e367844861556c9192a8ac"
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
