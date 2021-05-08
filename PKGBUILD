# Maintainer: Ben Mather <bwhmather@bwhmather.com>

pkgname=bedit-git
pkgver=r12304.ddbc92d7c
pkgrel=1
pkgdesc="Ben's Text Editor"
url="https://github.com/bwhmather/bedit"
arch=(i686 x86_64 armv7h aarch64)
license=(GPL)
depends=(gtk3 gtksourceview4 gsettings-desktop-schemas libpeas gspell python-gobject dconf)
makedepends=(yelp-tools vala gobject-introspection git gtk-doc meson)
optdepends=(
  'libgit2-glib: for git integration'
  'nuspell: for generic spell checking'
  'hspell: for spell checking hebrew'
  'libvoikko: for spell checking finnish'
)
provides=(bedit)
conflicts=(bedit)
groups=()
source=("git+https://github.com/bwhmather/bedit.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/bedit"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  arch-meson bedit build -D gtk_doc=true
  ninja -C build
}

check() {
  meson test -C build --print-errorlogs
}

package() {
  DESTDIR="$pkgdir" meson install -C build
}

