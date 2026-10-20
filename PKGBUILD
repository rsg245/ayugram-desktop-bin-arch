# Maintainer: Maxim Balashov <me@rsg.su>

pkgname=ayugram-desktop-bin
pkgver=7.2.9
pkgrel=2
pkgdesc="Desktop Telegram client with good customization and Ghost mode"
arch=(x86_64)
url="https://github.com/AyuGram/AyuGramDesktop"
license=('GPL-3.0-or-later')
depends=(
    'abseil-cpp' 'ada' 'ffmpeg' 'glib2' 'glibc' 'hicolor-icon-theme'
    'hunspell' 'kcoreaddons' 'libavif' 'libfido2' 'libgcc' 'libheif'
    'libjpeg-turbo' 'libjxl' 'libpipewire' 'libsrtp' 'libstdc++'
    'libvpx' 'libxcb' 'libxcomposite' 'libxdamage' 'libxext'
    'libxfixes' 'libxkbcommon' 'libxrandr' 'libxtst' 'lz4'
    'minizip' 'openal' 'openh264' 'openssl' 'opus' 'pipewire'
    'qt6-base' 'qt6-declarative' 'qt6-imageformats' 'qt6-svg'
    'qt6-wayland' 'rnnoise' 'tlottie' 'xxhash' 'zlib'
)

optdepends=(
    'geoclue: geoinformation support'
    'crow-translate: translation provider'
    'webkit2gtk-4.1: embedded browser features provided by webkit2gtk-4.1 (GTK3)'
    'webkitgtk-6.0: embedded browser features provided by webkitgtk-6.0 (GTK4)'
    'xdg-desktop-portal: desktop integration'
)
provides=('ayugram-desktop')
conflicts=('ayugram-desktop')
options=('!debug')

source=("https://cdn77.cachyos.org/repo/${CARCH}/cachyos/ayugram-desktop-${pkgver}-${pkgrel}-${CARCH}.pkg.tar.zst")
sha256sums=('4933e7105f5802543a700eeea17438d715923b6543118bdd163b46c1d50954dc')

package() {
    # Binary
    install -Dm755 "$srcdir/usr/bin/AyuGram" "$pkgdir/usr/bin/AyuGram"

    # Desktop entry
    install -Dm644 "$srcdir/usr/share/applications/com.ayugram.desktop.desktop" \
        "$pkgdir/usr/share/applications/com.ayugram.desktop.desktop"

    # DBus service
    install -Dm644 "$srcdir/usr/share/dbus-1/services/com.ayugram.desktop.service" \
        "$pkgdir/usr/share/dbus-1/services/com.ayugram.desktop.service"

    # Metainfo
    install -Dm644 "$srcdir/usr/share/metainfo/com.ayugram.desktop.metainfo.xml" \
        "$pkgdir/usr/share/metainfo/com.ayugram.desktop.metainfo.xml"

    # Standard icons
    local icon_size
    for icon_size in 16 32 48 64 128 256 512; do
        install -Dm644 "$srcdir/usr/share/icons/hicolor/${icon_size}x${icon_size}/apps/com.ayugram.desktop.png" \
            "$pkgdir/usr/share/icons/hicolor/${icon_size}x${icon_size}/apps/com.ayugram.desktop.png"
    done

    # HiDPI (@2x) icons
    for icon_size in 16 32 48 64 128 256 512; do
        install -Dm644 "$srcdir/usr/share/icons/hicolor/${icon_size}x${icon_size}@2/apps/com.ayugram.desktop.png" \
            "$pkgdir/usr/share/icons/hicolor/${icon_size}x${icon_size}@2/apps/com.ayugram.desktop.png"
    done

    # Symbolic icons
    local sym_icon
    for sym_icon in com.ayugram.desktop-attention-symbolic.svg \
                    com.ayugram.desktop-mute-symbolic.svg \
                    com.ayugram.desktop-symbolic.svg; do
        install -Dm644 "$srcdir/usr/share/icons/hicolor/symbolic/apps/${sym_icon}" \
            "$pkgdir/usr/share/icons/hicolor/symbolic/apps/${sym_icon}"
    done
}
