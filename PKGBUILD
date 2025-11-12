# Maintainer: RSG245 <rsg245@yandex.com>
# PKGBUILD source: https://github.com/rsg245/ayugram-desktop-bin-arch
# PKGBUILD source: https://gitlab.archlinux.org/rsg245/ayugram-desktop-bin
pkgname=ayugram-desktop-bin
pkgver=6.2.4
pkgrel=1
pkgdesc="Desktop Telegram client with good customization and Ghost mode"
arch=(x86_64)
url="https://github.com/AyuGram/AyuGramDesktop"
license=(GPL3)
depends=('hunspell' 'ffmpeg' 'hicolor-icon-theme' 'lz4' 'minizip' 'openal' 'qt6-imageformats' 'qt6-svg' 'qt6-wayland' 'xxhash' 'rnnoise' 'pipewire' 'libxtst' 'libxrandr' 'libxcomposite' 'libxdamage' 'abseil-cpp' 'libdispatch' 'openssl' 'protobuf' 'glib2' 'libsigc++-3.0' 'kcoreaddons' 'ada' 'openh264' 'jemalloc' 'libavif' 'libheif')
makedepends=('chrpath')
optdepends=('webkit2gtk: embedded browser features' 'xdg-desktop-portal: desktop integration')
provides=('ayugram-desktop')
conflicts=('ayugram-desktop')

pkgrel_upstream=1

# Archive source
source=(
  #https://aur.andontie.net/x86_64/ayugram-desktop-${pkgver}-${pkgrel_upstream}-x86_64.pkg.tar.zst
  https://github.com/rsg245/ayugram-desktop-bin-arch/releases/download/${pkgver}-${pkgrel_upstream}/ayugram-desktop-${pkgver}-${pkgrel_upstream}-x86_64.pkg.tar.zst  
)

# Checksums
sha256sums=('bdcfa1f1dbdd03b766b63ac6c4ec4ba17275c0468934460556c11236b2bb0c0d')

package() {
	cd "$srcdir/"

	# Creating needed directories
	install -dm755 "$pkgdir/usr/bin"
	install -dm755 "$pkgdir/usr/share"
	install -dm755 "$pkgdir/usr/share/applications"
	install -dm755 "$pkgdir/usr/share/dbus-1"
	install -dm755 "$pkgdir/usr/share/icons"
	install -dm755 "$pkgdir/usr/share/pixmaps"
	install -dm755 "$pkgdir/usr/share/metainfo"

	# Application executable
	install -Dm755 "$srcdir/usr/bin/AyuGram" "$pkgdir/usr/bin/AyuGram"

	# Remove RPATH informations
	chrpath --delete "$pkgdir/usr/bin/AyuGram"

	# Desktop launcher
	install -Dm644 "$srcdir/usr/share/icons/hicolor/256x256/apps/com.ayugram.desktop.png" "$pkgdir/usr/share/pixmaps/ayugram.png"
	install -Dm644 "$srcdir/usr/share/applications/com.ayugram.desktop.desktop" "$pkgdir/usr/share/applications/com.ayugram.desktop.desktop"

	# DBus service
	install -Dm644 "$srcdir/usr/share/dbus-1/services/com.ayugram.desktop.service" "$pkgdir/usr/share/dbus-1/services/com.ayugram.desktop.service"

	# Metainfo
	install -Dm644 "$srcdir/usr/share/metainfo/com.ayugram.desktop.metainfo.xml" "$pkgdir/usr/share/metainfo/com.ayugram.desktop.metainfo.xml"

	# Icons
	local icon_size icon_dir
	for icon_size in 16 32 48 64 128 256 512; do
		icon_dir="$pkgdir/usr/share/icons/hicolor/${icon_size}x${icon_size}/apps"
		install -d "$icon_dir"
		install -m644 "$srcdir/usr/share/icons/hicolor/${icon_size}x${icon_size}/apps/com.ayugram.desktop.png" "$icon_dir/com.ayugram.desktop.png"
	done
}
