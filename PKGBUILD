# Maintainer: Ahmad Hasan Mubashshir <ahmubashshir@gmail.com>
pkgname=tldr-sh
pkgver=r71.6bd83e6
pkgrel=5
pkgdesc="A fully-functional POSIX shell client for tldr."
arch=(any)
url="https://github.com/raylee/tldr-sh-client"
license=('MIT')
depends=('curl')
provides=('tldr')
conflicts=(
	'tldr'
	'tldr++'
	'tldr-git'
	'tealdeer'
	'nodejs-tldr'
	'tealdeer-bin'
	'tealdeer-git'
	'tldr-bash-git'
	'nodejs-tldr-git'
	'tldr-cpp-client'
	'tldr-go-client-git'
	'tldr-python-client'
)
source=(
	'tldr-sh::git+https://github.com/raylee/tldr-sh-client'
	'tldr.zsh'
)
sha256sums=('SKIP'
            '9b187a7a8955c602694de859a65a60739784ccebbd04181bce22e0737d880eb5')

pkgver()
{
  	cd "$srcdir/$pkgname"
	(
		set -o pipefail
		git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
		printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
	)
	pkgrel=$(git diff --shortstat|cut -d' ' -f2)
}

package() {
	cd "$srcdir"
	install -Dm755 "$pkgname/tldr" "$pkgdir/usr/bin/tldr"
	install -Dm755 "tldr.zsh" "$pkgdir/usr/share/zsh/site-functions/_tldr"
}
