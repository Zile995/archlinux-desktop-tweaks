# Maintainer: Zile995 <stefan.zivkovic995@gmail.com>

_pkgname=archlinux-pop_os-config
pkgname=${_pkgname}-git
pkgver=1.0.r1.g63f7910
pkgrel=1
pkgdesc="Pop!_OS zRAM, virtual memory and IO scheduler configuration for Arch Linux"
url="https://github.com/Zile995/archlinux-pop_os-config"
arch=('any')
license=('MIT')
install="${_pkgname}.install"
depends=('zram-generator')
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
  install -Dm644 LICENSE -t "${pkgdir}/usr/share/licenses/${_pkgname}"
}
