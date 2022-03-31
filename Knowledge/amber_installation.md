# AMBER Installation

```bash
# Unpack amber packages
tar jxvf Amber20.tar.bz2
tar jxvf AmberTools20.tar.bz2

# Prepare miniconda environments
module load miniconda3
conda create -n amber
conda install -c conda-forge AmberTools

# run on computing nodes
srun -N 1 -n 1 -p dgx2 --gres=gpu:1 --pty /bin/bash

# cmake
cd amber20_src/build
./run_cmake
make install

export PATH="/dssg/home/acct-stu/stu/software/amber20_src/build/CMakeFiles/miniconda/install/bin:$PATH"
source /dssg/home/acct-hpc/hpczbzt/software/amber20/amber.sh

```

## Used module

```bash
module load miniconda3

conda create -n amber
conda install -c conda-forge AmberTools
conda install numpy scipy matplotlib

module load cuda/10.1
module load openmpi
module load cmake
# all gcc version corresbond the the highest version: 12
```



## References

https://ambermd.org/doc12/Amber20.pdf page 24

https://ambermd.org/InstCentOS.php





`run_cmake` file

```cmake
#!/bin/bash

#  This file gives some sample cmake invocations.  You may wish to
#  edit some options that are chosen here.

#  For information on how to get cmake, visit this page:
#  https://ambermd.org/pmwiki/pmwiki.php/Main/CMake-Quick-Start

#  For information on common options for cmake, visit this page:
#  http://ambermd.org/pmwiki/pmwiki.php/Main/CMake-Common-Options

#  (Note that you can change the value of CMAKE_INSTALL_PREFIX from what
#  is suggested below, but it cannot coincide with the amber20_src
#  folder.)

AMBER_PREFIX=$(dirname $(dirname `pwd`))

if [ `uname -s|awk '{print $1}'` = "Darwin" ]; then

#  For macOS:

  if [ -x /Applications/CMake.app/Contents/bin/cmake ]; then
     cmake=/Applications/CMake.app/Contents/bin/cmake
  else
     cmake=cmake
  fi

  $cmake $AMBER_PREFIX/amber20_src \
    -DCMAKE_INSTALL_PREFIX=$AMBER_PREFIX/amber20 \
    -DCOMPILER=CLANG  -DBLA_VENDOR=Apple \
    -DMPI=FALSE -DCUDA=FALSE -DINSTALL_TESTS=TRUE \
    -DDOWNLOAD_MINICONDA=TRUE -DMINICONDA_USE_PY3=TRUE \
    2>&1 | tee cmake.log

else

#  Assume this is Linux:

  cmake $AMBER_PREFIX/amber20_src \
    -DCMAKE_INSTALL_PREFIX=$AMBER_PREFIX/amber20 \
    -DCOMPILER=GNU  \
    -DMPI=TRUE -DCUDA=TRUE -DINSTALL_TESTS=TRUE \
    -DDOWNLOAD_MINICONDA=FALSE -DMINICONDA_USE_PY3=TRUE \
    -DPYTHON_EXECUTABLE=/dssg/home/acct-stu/stu/.conda/envs/amber/bin/ \
    -DCUDA_TOOLKIT_ROOT_DIR=/dssg/opt/icelake/linux-centos8-icelake/gcc-11.2.0/cuda-10.1.243-aqldwfhcdkmzkkouvgyj3is4ha6kgf43 \
    2>&1 | tee  cmake.log

fi

if [ ! -s cmake.log ]; then
  echo ""
  echo "Error:  No cmake.log file created: you may need to edit run_cmake"
  exit 1
fi

echo ""
echo "If the cmake build report looks OK, you should now do the following:"
echo ""
echo "    make install"
echo "    source $AMBER_PREFIX/amber20/amber.sh"
echo ""
echo "Consider adding the last line to your login startup script, e.g. ~/.bashrc"
echo ""

```

