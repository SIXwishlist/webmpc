# Maintainer: ushi <ushi@honkgong.info>
pkgname='webmpc-git'
pkgver='0.0.0'
pkgrel=1
pkgdesc='realtime mpd client running in the browser'
arch=('x86_64' 'i686' 'armv6h')
url='https://put.honkgong.info'
license=('MIT')
conflicts=('webmpc')
provides=('webmpc')
makedepends=('go' 'ruby')
options=(!strip)
source=('webmpc::git+https://github.com/ushis/webmpc#branch=master')
sha256sums=('SKIP')

pkgver() {
  cd webmpc
  echo "$(git rev-list --count master).$(git rev-parse --short master)"
}

build() {
  cd webmpc
  make
}

package() {
  cd webmpc
  install -Dm0755 'webmpcd'                 "${pkgdir}/usr/bin/webmpcd"
  install -Dm0644 'systemd/webmpcd.conf'    "${pkgdir}/usr/lib/tmpfiles.d/webmpcd.conf"
  install -Dm0644 'systemd/webmpcd.service' "${pkgdir}/usr/lib/systemd/system/webmpcd.service"

  cd html
  find . -type f ! -name '*.scss' -exec install -Dm0644 {} "${pkgdir}/usr/share/webmpc/"{} \;
}

# vim:set ts=2 sw=2 et:
