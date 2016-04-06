#
_pkgname=exectime
pkgname=${_pkgname}-git
pkgver=r2.fc03c2a
pkgrel=1
pkgdesc="Simple time execution measurement written in Golang"
arch=('x86_64')
url="https://github.com/bvaudour/${_pkgname}"
license=('Public Domain')
makedepends=('git' 'go')
sha1sums=('SKIP')
source=(git://github.com/bvaudour/${_pkgname}.git)

pkgver() {
	cd "${srcdir}/${_pkgname}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "${srcdir}/${_pkgname}"
	_OLDGOPATH=$GOPATH
	export GOPATH=$(pwd)
	go build -o ${_pkgname} src/${_pkgname}/${_pkgname}.go
	export GOPATH=$_oldGOPATH
}

package() {
	cd "${srcdir}/${_pkgname}"
	install -Dm755 "${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
}
