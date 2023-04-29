# Maintainer: Zile995 <stefan.zivkovic995@gmail.com>

_pkgname=archlinux-desktop-tweaks
pkgname=${_pkgname}-git
pkgver=1.0.r12.gb71b45b
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
  install -Dm644 mglru.conf -t "${pkgdir}/etc/tmpfiles.d"
  install -Dm644 99-swappiness.conf -t "${pkgdir}/etc/sysctl.d"
  install -Dm644 zram-generator.conf -t "${pkgdir}/etc/systemd"
  install -Dm644 user.conf -t "${pkgdir}/etc/systemd/user.conf.d"
  install -Dm644 system.conf -t "${pkgdir}/etc/systemd/system.conf.d"
  install -Dm644 60-ioschedulers.rules -t "${pkgdir}/etc/udev/rules.d"
  install -Dm644 LICENSE -t "${pkgdir}/usr/share/licenses/${_pkgname}"
}
