pkgname='DOOM_BFA_LAUNCHER'
pkgver='1.0.1.5'
pkgrel=1
pkgdesc='DOOM BFA Launcher'
url="https://github.com/MadDeCoDeR/CRBDL"
arch=("x86_64")
groups=()
depends=("mono-git" "DOOM_BFA") #The existing mono on arch is broken. Require mono-git instead
makedepends=("git" "mono-msbuild" "mono-msbuild-sdkresolver" "nuget")
license=("MIT")
source=('CRBDL::git+https://github.com/MadDeCoDeR/CRBDL#branch=master')
md5sums=('SKIP')

build() {
     cd "${srcdir}/CRBDL/CRBDL"
     nuget install -OutputDirectory "${srcdir}/CRBDL/packages"
     cd "${srcdir}/CRBDL"
     msbuild /t:restore /p:Configuration=Release /p:Platform=x64
     msbuild /t:build /p:Configuration=Release /p:Platform=x64
}

package() {
    mkdir -p "${pkgdir}/usr/share/monoapps/CRBDL"
    cp "${srcdir}/CRBDL/CRBDL/bin/x64/Release/CDL.exe" "${pkgdir}/usr/share/monoapps/CRBDL/CDL.exe"
    cp "${srcdir}/CRBDL/packages/DesktopBridge.Helpers.1.2.2/lib/net45/DesktopBridge.Helpers.dll" "${pkgdir}/usr/share/monoapps/CRBDL/DesktopBridge.Helpers.dll"
    mkdir -p "${pkgdir}/usr/share/pixmaps"
    cp "${srcdir}/CRBDL/CRBDL/1.png" "${pkgdir}/usr/share/pixmaps/CRBDL.png"
    mkdir -p "${pkgdir}/usr/share/applications"
    cp "${srcdir}/assets/CRBDL.desktop" "${pkgdir}/usr/share/applications/CRBDL.desktop"
}
