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
  "0ddc38d01b7e84504c96361ea5041c32fab09893420cc516afd0b20cb501b25b46bb797f559f42f36464ba55c0cace5080fc1bd1f6671aa1127c091d7e416177"
  "9612db5509e18c2dbd0f03d8c07e3541f22f6f0c4e4369a2c5161d02a86dc2712ba08270900e3451ce10304a92cbca6c1459a3ba57dfdd8bd8462909d721ef8c"
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
