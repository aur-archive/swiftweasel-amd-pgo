# Contributor: tuxspirit <tuxspiritATarchlinuxDOTfr>

_pkgname=swiftweasel
_pkgproc=amd-pgo
pkgname=swiftweasel-amd-pgo
_pkgarch=x86-arch
pkgver=3.5.6
_xulver=1.9.1.7
pkgrel=2
pkgdesc="Mozilla Firefox optimized build for AMD processors on x86 architecturei (with xulrunner 1.9.1.7)."
arch=('i686')
url="http://swiftweasel.tuxfamily.org/"
license=('MPL' 'GPL' 'LGPL')
depends=('mozilla-common' 'desktop-file-utils' 'xulrunner>=1.9.1.5' 'nss' 'libidl2' 'libxcomposite' 'libjpeg7' 'libpng12')
provides=('firefox' 'swiftweasel')
replaces=('swiftweasel-athlon-xp' 'swiftweasel-athlon-tbird' 'swiftweasel-athlon64'
          'swiftweasel-k6' 'swiftweasel-k8')
conflicts=('swiftweasel' 'swiftweasel3' 'swiftweasel-amd' 'swiftweasel-intel')	  
install=swiftweasel.install
source=(http://download.tuxfamily.org/${_pkgname}/${_pkgname}-35/${pkgver}-tar.gz/${_pkgname}-${pkgver}_${_pkgproc}_${_pkgarch}.tar.gz
	swiftweasel.desktop
	swiftweasel-safe.desktop
        http://arm.konnichi.com/extra/os/${arch}/xulrunner-${_xulver}-1-${arch}.pkg.tar.gz)
	
md5sums=('f76655ee8328af578d4e49577dda13da'
         'e02fc1051ff31e05e45ec99eb38e16f6'
         'eef46b6617fb0dab69037c122793c6fb'
         '21f8d3168dd507fb0018f42d6a6b3a17')
		   
build() {

  # Software
  cd ${srcdir}/

  mkdir ${pkgdir}/opt/
  cp -r ${_pkgname} ${pkgdir}/opt/${_pkgname}

  ## Fix error install.rdf
  chmod -R 755 ${pkgdir}/opt/${_pkgname}/extensions/*

  ## Fix problem Xulrunner version
  mkdir -p ${pkgdir}/opt/${_pkgname}/xulrunner
  cp -R ${srcdir}/usr/lib/xulrunner-1.9.1/* ${pkgdir}/opt/${_pkgname}/xulrunner

  mkdir -p ${pkgdir}/usr/bin
  ln -s /opt/${_pkgname}/${_pkgname} ${pkgdir}/usr/bin/${_pkgname}

  install -d -m755 ${pkgdir}/usr/share/{applications,pixmaps}
  install -m644 -D ${srcdir}/swiftweasel/icons/mozicon128.png ${pkgdir}/usr/share/pixmaps/swiftweasel.png || return 1
  install -m644 ${srcdir}/swiftweasel.desktop ${pkgdir}/usr/share/applications/ || return 1
  install -m644 ${srcdir}/swiftweasel-safe.desktop ${pkgdir}/usr/share/applications/ || return 1 

}
