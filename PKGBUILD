# Maintainer: Brian Wilson <brian@wiltech.org>
pkgname='wiltech-base'
pkgver=v0.1a
pkgrel=1
pkgdesc="System base for WT Linux systems"
arch=('any')
url="https://wiltech.org/linux"
license=('GPLv3')
groups=()

source=(
    'dialogrc'
    'mirupgr.pachook'
    'pacman.conf'
)

sha256sums=('SKIP'
            'SKIP'
            'SKIP'
)

package_fulgur-base() {
    provides=('vim' 'vi')
    conflicts=('vim' 'vi')

    depends=(
        'bash' 'bzip2' 'coreutils' 'cryptsetup' 'device-mapper' 'dhcpcd' 'diffutils'
        'e2fsprogs' 'file' 'filesystem' 'findutils' 'gawk' 'gcc-libs' 'gettext'
        'glibc' 'grep' 'gzip' 'inetutils' 'iproute2' 'iputils' 'jfsutils'
        'less' 'licenses' 'linux-lts' 'logrotate' 'lvm2' 'man-db' 'man-pages'
        'mdadm' 'nano' 'netctl' 'pacman' 'pciutils' 'perl' 'cups'
        'procps-ng' 'psmisc' 'reiserfsprogs' 's-nail' 'sed' 'shadow' 'sysfsutils'
        'systemd-sysvcompat' 'tar' 'texinfo' 'usbutils' 'util-linux' 'neovim' 'which'
        'xfsprogs' 'networkmanager' 'openssh' 'htop' 'zsh' 'zsh-syntax-highlighting'
        'fws-zsh-config-git' 'python-neovim' 'python2-neovim' 'ranger' 'dialog' 'openvpn'
        'ufw' 'p7zip' 'curl' 'wget' 'intel-ucode' 'reflector' 'sudo' 'ntp'
        'networkmanager-dispatcher-ntpd'
    )

    install -dm 0755 "${pkgdir}/usr/bin"
    ln -s /usr/bin/nvim "${pkgdir}/usr/bin/vim"
    ln -s /usr/bin/nvim "${pkgdir}/usr/bin/vi"

    install -Dm 0644 dialogrc "${pkgdir}/etc/dialogrc"
    install -Dm 0755 mirupgr.pachook "${pkgdir}/etc/pacman.d/hooks/mirror-upgrade.hook"
    install -Dm 0644 pacman.conf "${pkgdir}/etc/pacman.conf"
    install -Dm 0600 sudoers "${pkgdir}/etc/sudoers"
}

post_install() {
    systemctl enable NetworkManager.service
    systemctl enable ntpd.service
    systemctl enable cups-browsed.service
    ufw enable
}
