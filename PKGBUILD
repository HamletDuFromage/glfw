# Maintainer:  fincs <fincs.alt1@gmail.com>

pkgbasename=glfw
pkgname=switch-$pkgbasename
pkgver=3.3.2
pkgrel=2
pkgdesc='Open Source, multi-platform library for OpenGL, OpenGL ES and Vulkan development on the desktop'
arch=('any')
url='https://github.com/HamletDuFromage/glfw'
license=(MIT)
options=(!strip libtool staticlibs)
source=("$pkgbasename::git+$url.git")
sha256sums=('SKIP')

depends=('switch-mesa')
makedepends=('devkitpro-pkgbuild-helpers')

build() {

  cd ${pkgbasename}

  source /opt/devkitpro/switchvars.sh

  cmake -G"Unix Makefiles" -DCMAKE_TOOLCHAIN_FILE=/opt/devkitpro/switch.cmake \
    -DCMAKE_INSTALL_PREFIX=$PORTLIBS_PREFIX \
    -DCMAKE_C_FLAGS="$CFLAGS $CPPFLAGS" \
    -DSWITCH_LIBNX=ON \
    -DCMAKE_AR="/opt/devkitpro/devkitA64/bin/aarch64-none-elf-gcc-ar" \
    -DGLFW_BUILD_EXAMPLES:BOOL=OFF -DGLFW_BUILD_TESTS:BOOL=OFF -DGLFW_BUILD_DOCS:BOOL=OFF \
    -DGLFW_VULKAN_STATIC:BOOL=ON -DGLFW_EGL_STATIC:BOOL=ON \
    .

  make

}

package() {
  cd ${pkgbasename}

  make install DESTDIR="$pkgdir"
}
