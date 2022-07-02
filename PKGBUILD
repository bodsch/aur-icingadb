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
  "${pkgname}-${pkgver}-x86_64.deb::https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_${pkgver}-${pkgrel}.bullseye_amd64.deb"
  "${pkgname}-${pkgver}-Release::https://packages.icinga.com/debian/dists/icinga-bullseye/Release"
  "${pkgname}-${pkgver}-Release.sig::https://packages.icinga.com/debian/dists/icinga-bullseye/Release.gpg"
)

sha512sums=(
  "5a678140ee71875e04ee509c089b010a0dce6fdd21d748ed2b05cafee99972ee737481e7df829b26579ec40323591375f91e7f62076937f8e821f1d6d445c41f"
  "a25db8942c2dedde67b77cc209d137a80df232c63e4760c47671062d2d097eec5aec93e8417612e97cf59b9be5d89c61b3bb4ac711d4819a755aff6d1a4e8b83"
  "981f0299c365723abbe5c6af422afbe33f94ca3478fb565a4f6e232b4a38b262a74ffe122692b535b00d0e816e7a773630c29bbf4ddb67514b3adcaa4b93ed38"
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
