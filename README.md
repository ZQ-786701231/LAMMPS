# LAMMPS
Intsall Lammps On CentOS6
# 在官网下载FFTW、MPICH、LAMMPS
# 安装fftw
```
解压  tar -zxvf fftw-3.3.8.tar.gz

进入文件夹  cd fftw-3.3.8/

配置  ./configure

编译  make

安装  make install
```
# 安装mpich
在安装之前，要先安装C编译器，可以使用yum指令安装
```
yum install make  

yum install gcc   

yum isntall gcc-c++ 

后面步骤与安装fftw一样
```
在安装包中，官方还给出了一个例子供我们测试
```
cd mpich-3.2.1/examples

mpiexec -n 5 ./cpi
```
# 安装lammps
```
解压  tar -xvf lammps-stable.tar.gz
```
为了以后方便，我们把解压后的目录名改为lammps-install
```
进入文件  cd lammps-install/src/
```
执行make yes-all和make no-lib这两条命令，第一个命令的意思是编译lammps时安装所有包，第二条命令是取消需要外链的包
```
输入 make mpi -j 32就可以编译了
```
将lammps的主程序路径加入PATH，在命令行输入cd，然后回车进入用户根目录
```
vi .bashrc

最后一行进行输入export PATH=~/root/lammps-install/src:$PATH

source .bashrc
```
我们到lammps自带的例子中看一下
```
cd lammps-install/examples/melt/

mpirun -np 16 lmp_mpi < in.melt
```
完美运行则成功

