# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Common code for working with audio in ROS."
url='https://wiki.ros.org/audio_common'

pkgname='ros-melodic-audio-common'
pkgver='0.3.8'
arch=('any')
pkgrel=2
license=('BSD')

ros_makedepends=(ros-melodic-catkin)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-melodic-sound-play
  ros-melodic-audio-capture
  ros-melodic-audio-play
  ros-melodic-audio-common-msgs)
depends=(${ros_depends[@]})

_dir="audio_common-${pkgver}/audio_common"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-drivers/audio_common/archive/${pkgver}.tar.gz")
sha256sums=('f0c552e06e211998981c7204d479b7c5130503812fbba28324d1cb52b3454d21')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
        -DPYTHON_EXECUTABLE=/usr/bin/python3 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
