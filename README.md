# FreeCAD-precompiled
This is a version of FreeCAD that has already been compiled for Raspberry Pi. Followed [Scruss's tutorial](https://scruss.com/blog/2020/02/16/freecad-on-raspberry-pi-4/) for FreeCAD version 0.18.4  
## To install:  
```function error {
  echo -e "\e[31m$1\e[39m"
  exit 1
}

# Get dependencies
DIRECTORY="$(dirname "$(dirname "$(dirname "$0")")")"

sudo apt install -y "cmake build-essential libtool lsb-release swig libboost-dev libboost-date-time-dev libboost-filesystem-dev libboost-graph-dev libboost-iostreams-dev libboost-program-options-dev libboost-python-dev libboost-regex-dev libboost-serialization-dev libboost-signals-dev libboost-thread-dev libcoin-dev libeigen3-dev libgts-bin libgts-dev libkdtree++-dev libmedc-dev libopencv-dev libproj-dev libvtk6-dev libx11-dev libxerces-c-dev libzipios++-dev qt4-dev-tools libqt4-dev libqt4-opengl-dev libqtwebkit-dev libshiboken-dev libpyside-dev pyside-tools python-dev python-matplotlib python-pivy python-ply python-pyside libocct*-dev occt-draw libocct-data-exchange-dev libocct-draw-dev libocct-visualization-dev libsimage-dev doxygen libcoin-doc dh-exec libspnav-dev" || exit 1

#download from google drive
wget --load-cookies /tmp/cookies.txt "https://docs.google.com/uc?export=download&confirm=$(wget --quiet --save-cookies /tmp/cookies.txt --keep-session-cookies --no-check-certificate 'https://docs.google.com/uc?export=download&id=10zsGG86z2iCN4bIfs4D4wg2hZJ4J5hGF' -O- | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1\n/p')&id=10zsGG86z2iCN4bIfs4D4wg2hZJ4J5hGF" -O freecad-precompiled.zip || error "failed to download archive from Google Drive!"

rm -f /tmp/cookies.txt  || echo "Warning: failed to remove cookies.txt."

rm -rf freecad-build FreeCAD-0.18.4 || error "Failed to delete freecad-build and FreeCAD-0.18.4 folders!"

unzip -q ~/freecad-precompiled.zip || error "Failed to extract archive!"
rm -f ~/freecad-precompiled.zip || error "Failed to delete archive!"

cd freecad-build || error "Failed to enter directory!"
sudo make install || error "sudo make install failed!"
```
## To uninstall:  
```sudo rm -f $(cat ~/freecad-build/install_manifest.txt)
rm -rf freecad-build FreeCAD-0.18.4```

This was compiled on a Raspberry Pi 4 on 9/21/2020.
