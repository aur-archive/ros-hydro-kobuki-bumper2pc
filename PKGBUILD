# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Bumper/cliff to pointcloud nodelet: Publish bumpers and cliff sensors events as points in a pointcloud, so navistack can use them for poor-man navigation."
url='http://ros.org/wiki/kobuki_bumper2pc'

pkgname='ros-hydro-kobuki-bumper2pc'
pkgver='0.5.6'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-sensor-msgs
  ros-hydro-nodelet
  ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-kobuki-msgs
  ros-hydro-pluginlib)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-roscpp
  ros-hydro-sensor-msgs
  ros-hydro-kobuki-msgs
  ros-hydro-nodelet
  ros-hydro-pluginlib)
depends=(${ros_depends[@]})

_tag=release/hydro/kobuki_bumper2pc/${pkgver}-${_pkgver_patch}
_dir=kobuki_bumper2pc
source=("${_dir}"::"git+https://github.com/yujinrobot-release/kobuki-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
