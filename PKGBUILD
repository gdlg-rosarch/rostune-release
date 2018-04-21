# Script generated with Bloom
pkgdesc="ROS - rostune is a tool that helps ROS developers distribute their nodes in the most effective way. It collects statistics for topics and nodes, such as CPU and network usage."
url='http://wiki.ros.org/rostune'

pkgname='ros-kinetic-rostune'
pkgver='1.0.7_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-message-generation'
'ros-kinetic-std-msgs'
'ros-kinetic-topic-tools'
)

depends=('ros-kinetic-message-runtime'
'ros-kinetic-std-msgs'
'ros-kinetic-topic-tools'
)

conflicts=()
replaces=()

_dir=rostune
source=()
md5sums=()

prepare() {
    cp -R $startdir/rostune $srcdir/rostune
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

