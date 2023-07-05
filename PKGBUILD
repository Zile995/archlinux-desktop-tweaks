# Maintainer: Zile995 <stefan.zivkovic995@gmail.com>

_pkgname=archlinux-desktop-tweaks
pkgname=${_pkgname}-git
pkgver=1.0.r12.gd143442
pkgrel=1
pkgdesc="zRAM, virtual memory, IO scheduler and various Arch Linux desktop tweaks"
url="https://github.com/Zile995/archlinux-desktop-tweaks"
arch=('any')
license=('GPL3')
install="${_pkgname}.install"
depends=('systemd' 'zram-generator')
makedepends=('git')
source=("${_pkgname%"-git"}::git+$url")
md5sums=('SKIP')

pkgver() {
    cd "${_pkgname%"-git"}"
    git describe --long --tags --abbrev=7 | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

package() {
  cd "${_pkgname%"-git"}"
  install -Dm0644 mglru.conf              -t "${pkgdir}/usr/lib/tmpfiles.d"
  install -Dm0644 99-swappiness.conf      -t "${pkgdir}/usr/lib/sysctl.d"
  install -Dm0644 zram-generator.conf     -t "${pkgdir}/usr/lib/systemd"
  install -Dm0644 60-ioschedulers.rules   -t "${pkgdir}/usr/lib/udev/rules.d"
  install -Dm0644 10-default-timeout.conf -t "${pkgdir}/usr/lib/systemd/user.conf.d"
  install -Dm0644 10-default-timeout.conf -t "${pkgdir}/usr/lib/systemd/system.conf.d"
  install -Dm0644 LICENSE                 -t "${pkgdir}/usr/share/licenses/${_pkgname}"
}
