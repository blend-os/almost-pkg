# Maintainer: Rudra Saraswat <rs2009@ubuntu.com>

pkgname=almost
pkgver=1.2.9
pkgrel=1
pkgdesc='On-demand immutability for blendOS'
url='https://github.com/blend-os/almost'
source=("git+https://github.com/blend-os/almost.git")
sha256sums=('SKIP')
arch=('x86_64')
license=('GPL-3.0-or-later')
makedepends=('go')

build() {
  cd almost
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
  go build -o almost main.go
}

check() {
  cd almost
  go test main.go
}

package() {
  cd almost
  install -Dm755 almost "$pkgdir"/usr/bin/almost
  install -Dm644 debian/almost.service "$pkgdir"/usr/lib/systemd/system/almost.service
}
