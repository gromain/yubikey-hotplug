pkgname=yubikey-hotplug
pkgver=1
pkgrel=2
pkgdesc="udev hotplug event for Yubikey devices"
arch=('any')
url="https://github.com/gromain/yubikey-hotplug"
license=('MIT')
depends=('bash' 'yubikey-manager')
source=('yubikey-hotplug' '95-yubikey-hotplug.rules')
install='yubikey-hotplug.install'
sha256sums=('db420421af4f8f047c652f7e5675844d29e00e8c4ff44c88544ca6ecf5eb9a72'
            '0b4e2d3260f443e2206e06c77f5cefaf10888174ef52a9529172443410041a19')
            
package() {
  install -d -m0755 "${pkgdir}/etc/udev/rules.d"
  install -m0644 "${srcdir}/95-yubikey-hotplug.rules" "${pkgdir}/etc/udev/rules.d/"
  install -d -m0755 "${pkgdir}/usr/bin"
  install -m0755 "${srcdir}/yubikey-hotplug" "${pkgdir}/usr/bin/"
}
