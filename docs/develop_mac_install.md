# mac

## caffee
参考：https://www.jianshu.com/p/cc16e2977e27
```

brew tap brewsci/bio
brew tap brewsci/science

brew install -vd snappy leveldb gflags glog szip lmdb
brew tap brewsci/bio
brew tap homebrew/science
brew install hdf5 opencv

git clone https://github.com/BVLC/caffe.git
cd caffe
cp Makefile.config.example Makefile.config

mkdir build
cd build
export PATH=/Applications/CMake.app/Contents/bin:$PATH
#前面说了~CMake改Makefile没用，所以我们需要手动去CMakeCache.txt中搜索CPU_ONLY:BOOL＝，改成CPU_ONLY:BOOL＝ ON。打开CaffeConfig.cmake, 找到set(CPU_ONLY, OFF)，同样改成ON。

cmake ..

make all
make runtest
make pytest
mkdir ~/python
cd caffe
mv /python/caffe ~/python
export PYTHONPATH=~/python:$PYTHONPATH
```