# MyOwnVersionOfGCC_LXPLUS
how to use your own version of gcc compilers on a server like lxplus, where you do not have installation permissions.

<par>Simplification of READMEs in [wiki GFortranBinaries](https://gcc.gnu.org/wiki/GFortranBinaries) </par>

<par> To check glibc version you are using</par>

```bash
/lib/libc.so.6
```

<par></par>

```bash
wget http://gfortran.meteodat.ch/download/x86_64/snapshots/gcc-4.9-20160803.tar.xz
tar xvf gcc-4.9-20160803.tar.xz
NEWFORTRANPATH="$(pwd)"

cat <<EOT >> CONFIGNEWFORTRAN.sh 
#!/bin/sh

export PATH=$NEWFORTRANPATH/gcc-4.9/bin:$PATH

if [ -z "$LD_LIBRARY_PATH" ]; then
    LD_LIBRARY_PATH="$NEWFORTRANPATH/gcc-4.9/lib64"
  else
    LD_LIBRARY_PATH="$NEWFORTRANPATH/gcc-4.9/lib64:$LD_LIBRARY_PATH"
  fi
  export LD_LIBRARY_PATH


EOT
```
<par>And when you want to use it, just source the config script</par>


```bash
source PATH_TO_THE_FORTRAN_FOLDE/CONFIGNEWFORTRAN.sh 

```
