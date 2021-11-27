# Maintainer: Bodo Schulz <bodo@boone-schulz.de>

pkgname=icingadb
pkgver=1.0.0-rc2
pkgdate=20211115
pkgid=1813
epoch=1
pkgrel=1
pkgdesc='Icinga configuration and state database'
arch=('x86_64')
license=('GPL-2.0')
url='https://icinga.com/docs/icinga-db'

source=(
  "${pkgname}-${pkgver}-x86_64.deb::https://packages.icinga.com/debian/pool/main/i/${pkgname}/${pkgname}_${pkgver}+rc2.${pkgdate}.${pkgid}+bullseye-0_amd64.deb",
  "${pkgname}-${pkgver}-Release::https://packages.icinga.com/debian/dists/icinga-bullseye-testing/Release"
  "${pkgname}-${pkgver}-Release.sig::https://packages.icinga.com/debian/dists/icinga-bullseye-testing/Release.gpg"
) 

sha512sums=('')

package() {
    cd "${srcdir}"

    tar -xzf data.tar.gz -C "${pkgdir}"

}



