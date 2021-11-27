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

source=(

# https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_1.0.0~rc2-1.bullseye_amd64.deb
# https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_1.0.0~rc2-1.bullseye_amd64.deb
  "${pkgname}-${pkgver}-x86_64.deb::https://packages.icinga.com/debian/pool/main/i/icingadb/icingadb_${pkgver}~rc2-${pkgrel}.bullseye_amd64.deb",
  "${pkgname}-${pkgver}-Release::https://packages.icinga.com/debian/dists/icinga-bullseye-testing/Release"
  "${pkgname}-${pkgver}-Release.sig::https://packages.icinga.com/debian/dists/icinga-bullseye-testing/Release.gpg"
)

#0ddc38d01b7e84504c96361ea5041c32fab09893420cc516afd0b20cb501b25b46bb797f559f42f36464ba55c0cace5080fc1bd1f6671aa1127c091d7e416177  icingadb-1.0.0-Release
#9612db5509e18c2dbd0f03d8c07e3541f22f6f0c4e4369a2c5161d02a86dc2712ba08270900e3451ce10304a92cbca6c1459a3ba57dfdd8bd8462909d721ef8c  icingadb-1.0.0-Release.sig
#5a678140ee71875e04ee509c089b010a0dce6fdd21d748ed2b05cafee99972ee737481e7df829b26579ec40323591375f91e7f62076937f8e821f1d6d445c41f  icingadb-1.0.0-x86_64.deb


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

  install -D --mode=750 usr/sbin/icingadb "${pkgdir}/usr/sbin/icingadb"

#  install -D --mode=0750 "${pkgdir}/usr/sbin/icingadb" /usr/sbin/icingadb
#  install --direcory --mode=0750 "${pkgdir}/etc/icingadb" /etc/icingadb
}

_as_service() {
    cat << EOF

Start icingadb manually or enable the service:
  systemctl start icingadb'
  systemctl enable icingadb'

EOF
}

_stop_and_disable_service() {
  systemctl daemon-reload
  systemctl stop ckb-daemon
  systemctl disable ckb-daemon
}

# arg 1:  the new package version
post_install() {
  _as_service
}

# arg 1:  the new package version
# arg 2:  the old package version
pre_upgrade() {
  _stop_and_disable_service
}

# arg 1:  the new package version
# arg 2:  the old package version
post_upgrade() {
  systemctl daemon-reload
  _as_service
}

# arg 1:  the old package version
pre_remove() {
  _stop_and_disable_service
}

# arg 1:  the old package version
post_remove() {
  systemctl daemon-reload
}
