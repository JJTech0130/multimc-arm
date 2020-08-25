# Building
To build MultiMC5 for architectures other than x86 and x64, you need to follow the normal building instructions for MultiMC, but specify a different meta repo to cmake.
## Condensed build instructions
### Build Dependencies
* A C++ compiler capable of building C++11 code.
> Note: On Raspbian, GCC is out-of-date. You will need to install another compiler (for example, `clang`)
* Qt 5.6+ Development tools (for example, `qt5-default`)
* cmake 3.1 or newer (for example, `cmake`)
* zlib (for example, `zlib1g-dev`)
* Java JDK 8 (for example, `openjdk-8-jdk`)
> Note: On Raspian, `openjdk-8-jdk` is not included. You will need to download it from [AdoptOpenJDK](https://adoptopenjdk.net/releases.html?variant=openjdk8&jvmVariant=hotspot)
* GL headers (for example, `libgl1-mesa-dev`)

### Building from command line
You need a source folder, a build folder and an install folder.

Let's say you want everything in `~/MultiMC/`:

```
# make all the folders
mkdir ~/MultiMC && cd ~/MultiMC
mkdir build
mkdir install
# clone the complete source
git clone --recursive https://github.com/MultiMC/MultiMC5.git src # You can clone from MultiMC's main repo, no need to use a fork.
# configure the project
cd build
cmake -DCMAKE_INSTALL_PREFIX=../install -DMultiMC_META_URL:STRING="https://jjtech0130.github.io/meta-multimc/" ../src
# build & install (use -j with the number of cores your CPU has)
make -j4 install
```

The cmake line has one difference from the normal build: `-DMultiMC_META_URL:STRING="https://jjtech0130.github.io/meta-multimc/"`. You can replace that URL with your own meta repo if you want to make changes.

Another thing to consider is the C++ compiler. If you use clang (because your gcc is outdated) you need to add `-DCMAKE_CXX_COMPILER=clang++` and `-DCMAKE_C_COMPILER=clang`

### Packaging, using, etc.
MultiMC should now be built for your architecture with whatever meta repo you specified. If you kept the install location the default, it will be located in `~/MultiMC/install`.
You can move it somewhere else or use it there. See the [install page](install) for instructions on running it and common errors.
