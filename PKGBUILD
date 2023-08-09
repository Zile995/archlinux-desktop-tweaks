# Maintainer: Zile995 <stefan.zivkovic995@gmail.com>

pkgname=archlinux-desktop-tweaks-git
pkgver=1.0.r14.g5d4a4ea
pkgrel=1
pkgdesc="zRAM, virtual memory, IO scheduler and various Arch Linux desktop tweaks"
url="https://github.com/Zile995/archlinux-desktop-tweaks"
arch=('any')
license=('GPL3')
install="${pkgname}.install"
depends=('systemd' 'zram-generator')
makedepends=('git')
source=("${pkgname}::git+$url")
md5sums=('SKIP')

pkgver() {
  cd "$pkgname"
  git describe --long --tags --abbrev=7 | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

package() {
  cd "$pkgname"

  # Install the configuration
  install -Dm0644 config/mglru.conf              -t "${pkgdir}/usr/lib/tmpfiles.d"
  install -Dm0644 config/99-swappiness.conf      -t "${pkgdir}/usr/lib/sysctl.d"
  install -Dm0644 config/zram-generator.conf     -t "${pkgdir}/usr/lib/systemd"
  install -Dm0644 config/60-ioschedulers.rules   -t "${pkgdir}/usr/lib/udev/rules.d"
  install -Dm0644 config/10-default-timeout.conf -t "${pkgdir}/usr/lib/systemd/user.conf.d"
  install -Dm0644 config/10-default-timeout.conf -t "${pkgdir}/usr/lib/systemd/system.conf.d"

  # Install the LICENSE
  install -Dm0644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
