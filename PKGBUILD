# Script generated with Bloom
pkgdesc="ROS - The interactive_marker_tutorials package"
url='http://ros.org/wiki/interactive_marker_tutorials'

pkgname='ros-lunar-interactive-marker-tutorials'
pkgver='0.10.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-lunar-catkin'
'ros-lunar-interactive-markers'
'ros-lunar-roscpp'
'ros-lunar-tf'
'ros-lunar-visualization-msgs'
)

depends=('ros-lunar-interactive-markers'
'ros-lunar-roscpp'
'ros-lunar-tf'
'ros-lunar-visualization-msgs'
)

conflicts=()
replaces=()

_dir=interactive_marker_tutorials
source=()
md5sums=()

prepare() {
    cp -R $startdir/interactive_marker_tutorials $srcdir/interactive_marker_tutorials
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

