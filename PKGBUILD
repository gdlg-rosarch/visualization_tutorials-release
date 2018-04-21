# Script generated with Bloom
pkgdesc="ROS - Metapackage referencing tutorials related to rviz and visualization."
url='http://ros.org/wiki/visualization_tutorials'

pkgname='ros-kinetic-visualization-tutorials'
pkgver='0.10.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-interactive-marker-tutorials'
'ros-kinetic-librviz-tutorial'
'ros-kinetic-rviz-plugin-tutorials'
'ros-kinetic-rviz-python-tutorial'
'ros-kinetic-visualization-marker-tutorials'
)

conflicts=()
replaces=()

_dir=visualization_tutorials
source=()
md5sums=()

prepare() {
    cp -R $startdir/visualization_tutorials $srcdir/visualization_tutorials
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
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

