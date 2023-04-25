# Maintainer: Zile995 <stefan.zivkovic995@gmail.com>

_pkgname=archlinux-system-config
pkgname=${_pkgname}-git
pkgver=1.0.r9.gc7472e2
pkgrel=1
pkgdesc="zRAM, virtual memory, IO scheduler and various Arch Linux system configurations"
url="https://github.com/Zile995/archlinux-system-config"
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
  install -Dm644 99-swappiness.conf -t "${pkgdir}/etc/sysctl.d"
  install -Dm644 zram-generator.conf -t "${pkgdir}/etc/systemd"
  install -Dm644 60-ioschedulers.rules -t "${pkgdir}/etc/udev/rules.d"
  install -Dm644 user.conf -t "${pkgdir}/etc/systemd/user.conf.d"
  install -Dm644 system.conf -t "${pkgdir}/etc/systemd/system.conf.d"
  install -Dm644 LICENSE -t "${pkgdir}/usr/share/licenses/${_pkgname}"
}
