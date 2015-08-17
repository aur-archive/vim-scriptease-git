# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-scriptease-git
pkgver=20140531
pkgrel=1
pkgdesc="A Vim plugin for Vim plugins, by tpope"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/tpope/vim-scriptease"
license=('custom:vim')
source=(${pkgname%-git}::git+https://github.com/tpope/vim-scriptease)
sha256sums=('SKIP')
provides=('vim-scriptease')
conflicts=('vim-scriptease')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing documentation...'
  install -Dm 644 README.markdown "$pkgdir/usr/share/doc/vim-scriptease/README.markdown"

  msg 'Installing appdirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _appdir in doc plugin; do
    cp -dpr --no-preserve=ownership $_appdir "$pkgdir/usr/share/vim/vimfiles/$_appdir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
  find "$pkgdir" -type f -name .gitignore -exec rm -r '{}' +
}
