# Script generated with Bloom
pkgdesc="ROS - Tutorial showing how to compile your own C++ program with RViz displays and features."
url='http://ros.org/wiki/librviz_tutorial'

pkgname='ros-lunar-librviz-tutorial'
pkgver='0.10.2_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('qt5-base'
'ros-lunar-catkin'
'ros-lunar-roscpp'
'ros-lunar-rviz'
)

depends=('qt5-base'
'ros-lunar-roscpp'
'ros-lunar-rviz'
)

conflicts=()
replaces=()

_dir=librviz_tutorial
source=()
md5sums=()

prepare() {
    cp -R $startdir/librviz_tutorial $srcdir/librviz_tutorial
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

