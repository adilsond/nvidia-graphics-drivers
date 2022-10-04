This is a fork from https://salsa.debian.org/nvidia-team/nvidia-graphics-drivers

I made a few modifications for building Debian packages for version 515.76 
that is not available from Debian sources and even their Gitlab.

Instructions for building.

git clone this repository

tar -Jcvvf nvidia-graphics-drivers_515.76.orig.tar.xz nvidia-graphics-drivers


Download the installer from https://www.nvidia.com/Download/driverResults.aspx/193095/en-us/
and https://www.nvidia.com/Download/driverResults.aspx/193096/en-us/

Enter the repository and do 

mkdir amd64 arm64 

And put each installer inside them.

Now prepare more two packages

Leve the repo folder and do this.

mkdir nvidia-graphics-drivers_515.76.orig-amd64
cp nvidia-graphics-drivers/amd64/NVIDIA-Linux-x86_64-515.76.run nvidia-graphics-drivers_515.76.orig-amd64
tar -zcvvf nvidia-graphics-drivers_515.76.orig-amd64.tar.gz nvidia-graphics-drivers_515.76.orig-amd64
rm -rf nvidia-graphics-drivers_515.76.orig-amd64

mkdir nvidia-graphics-drivers_515.76.orig-arm64
cp nvidia-graphics-drivers/arm64/NVIDIA-Linux-aarch64-515.76.run nvidia-graphics-drivers_515.76.orig-arm64
tar -zcvvf nvidia-graphics-drivers_515.76.orig-arm64.tar.gz nvidia-graphics-drivers_515.76.orig-arm64
rm -rf nvidia-graphics-drivers_515.76.orig-arm64

cd nvidia-graphics-drivers

debuild -d

or/and

debuild -ai386 -d

And wait a few minutes until all packages are done.
