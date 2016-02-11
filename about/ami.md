---
layout: default
title: NeuroData AMI
---

# Creating the NeuroData Analytics AMI

To begin, launch an instance with the following AMI:''ami-eec75e87''. Note, you may need to modify the partition of the instance in order to occupy the entire hard drive instead of a small subset (initially 5 GB). This can be done by unmounting the volume, mounting it as a secondary volume to another instance, creating a new partition at the same starting block using ''parted'', reattaching to the original instance, and expanding the file system using ''resize2fs /dev/sdba1''.

## Basic Setup

Once the instance has been launched, log in using your public key and run the following setup.

### Updates and Package Libraries

~~~
sudo su
sudo echo "ALL        ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# Manual step
vi /etc/ssh/sshd_config # replace "PasswordAuthentication no" with "PasswordAuthentication yes"

/etc/init.d/sshd restart
yum -y update
yum -y install epel-release

ulimit -c unlimited
~~~

### Basic Development Tools

~~~
sudo su
yum -y install wget gcc elfutils-libelf-devel libstdc++-devel glibc-devel libaio-devel gcc-c++
yum -y groupinstall "Development tools" "X Window System" "Fonts"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel xz-devel
yum -y install java-1.6.0-openjdk-devel cmake vim screen bc R openssl-devel libpng-devel ImageMagick
yum -y --enablerepo epel-testing install s3cmd
~~~

## VNC Setup


In order to have a valid vnc server, you need to install a desktop and configure vnc users appropriately.

### Desktop

~~~
yum -y groupinstall Desktop Xfce
yum -y install xorg-x11-fonts-Type1 xorg-x11-fonts-misc
#startxfce4 to launch
~~~

### VNC Server

~~~
yum -y install vnc-server tigervnc-server
yum -y install vnc tigervnc
yum -y install xterm
useradd neurodata
passwd neurodata #enter password
echo 'VNCSERVERS="1:neurodata"
VNCSERVERARGS[1]="-geometry 1180x700"' >> /etc/sysconfig/vncservers
su - neurodata
vncpasswd #enter diff password
exit
/sbin/service   vncserver start
/sbin/service   vncserver stop
/sbin/chkconfig vncserver on
/sbin/service   vncserver start
~~~

### S3 Credentials

To access the NeuroData S3 buckets, you need to configure S3 commandline utilities. This is shown using the credentials of the generic neurodata s3 user account, below. All lines starting with '#>' should be entered at the prompt.

~~~
s3cmd --configure
#>[IAM Public Key]
#>[IAM Secret Key]
#>[accept default]
#>neurodata
#>[accept default]
#>Yes
#>Y
#>y
~~~


## Installing Further Dependencies

Many other packages are necessary to use our analytics stack, install either all of the below or the subset which are required for your subset of the stack.

### Initial Positioning

~~~
export base=/share0
export m2g=${base}/m2g
export M2G_HOME=${m2g} #duplicate for legacy reasons
~~~

### Oracle Java

~~~
mkdir -p ${base}/src/java
cd ${base}/src/java
wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebac    kup-cookie" "http://download.oracle.com/otn-pub/java/jdk/7u71-b14/jdk-7u71-linux-x64.tar.gz"
tar xzf jdk-7u71-linux-x64.tar.gz
cd ${base}/src/java/jdk1.7.0_71/
alternatives --install /usr/bin/java java ${base}/src/java/jdk1.7.0_71/bin/java 2
alternatives --config java #MANUAL STEP:  type 1
alternatives --install /usr/bin/javac javac ${base}/src/java/jdk1.7.0_71/bin/javac 2
alternatives --set javac ${base}/src/java/jdk1.7.0_71/bin/javac
alternatives --install /usr/bin/jar jar ${base}/src/java/jdk1.7.0_71/bin/jar 2
alternatives --set jar ${base}/src/java/jdk1.7.0_71/bin/jar
export JAVA_HOME=${base}/src/java/jdk1.7.0_71
~~~

### LONI Pipeline

~~~
mkdir -p ${base}/src/loni
cd ${base}/src/loni
wget http://openconnecto.me/data/public/MR/m2g_v1_1_0/deps/...
mkdir loni_6.0.1
tar -xvf Pipeline-6.0.1-unix.tar.bz2 -C loni_6.0.1
wget http://openconnecto.me/data/public/MR/m2g_v1_1_0/deps/...
mkdir loni_6.1
tar -xvf Pipeline-6.1-unix.tar.bz2 -C loni_6.1
~~~

### Python 2.7

~~~
mkdir -p ${base}/src/python
cd ${base}/src/python
wget http://python.org/ftp/python/2.7.9/Python-2.7.9.tar.xz
tar xf Python-2.7.9.tar.xz
cd Python-2.7.9
./configure --prefix=/usr/local --enable-unicode=ucs4 --enable-shared LDFLAGS="-Wl,-rpath /usr/local/lib"
make && make altinstall
export PATH='/usr/local/bin':${PATH}
ln -s /usr/local/bin/python2.7 /usr/local/bin/python
cd ${base}/src/python
wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py
python ez_setup.py
easy_install pip
~~~

### Popular Python Packages

~~~
  easy_install argparse ipython
  pip install numpy nibabel cython
  pip install scipy
  pip install scikit-image
  easy_install -U distribute
~~~

## MATLAB for JHU Users

This is currently restricted to JHU students and faculty only for licensing reasons.  If you have a matlab license we can help provide instructions.

~~~
sudo mkdir ${base}/src/matlab
sudo mkdir ${base}/src/matlab/matlabinst
cd ${base}/src/matlab
scp <user>@braincloud1.cs.jhu.edu:/share0/transfer/matlab_r2015a_install.iso .
scp <user>@braincloud1.cs.jhu.edu:/share0/transfer/installer_input_neurodataAMI.txt .
scp <user>@braincloud1.cs.jhu.edu:/share0/transfer/AWS_network_license_20150901-rev1.dat .
sudo mount -o loop matlab_r2015a_install.iso matlabinst
sudo ${base}/src/matlab/matlabinst/install -mode silent -inputFile ${base}/src/matlab/installer_input_neurodataAMI.txt
~~~

To launch matlab, run the following command:

~~~
/usr/local/R2015a/bin/matlab -nodesktop
~~~

## Neurodata Analytics

~~~
cd ${base}
git clone https://github.com/openconnectome/vesicle
git clone https://github.com/openconnectome/cajal
git clone https://github.com/openconnectome/manno
git clone https://github.com/openconnectome/macho
~~~

### Gala

~~~
pip install scikit-learn
yum -y install hdf5 hdf5-devel
easy_install h5py
yum -y install python-imaging
pip install viridis
pip install gala
~~~

### ilastik

~~~
cd ${base}/src
wget http://openconnecto.me/data/public/misc/ilastik-master-no-tracking-Linux.tar.gz
tar -xvf ilastik-master-no-tracking-Linux.tar.gz
mv ilastik-master-no-tracking-Linux ilastik
mv ilastik-master-no-tracking-Linux.tar.gz ilastik
~~~

## FlashGraph

~~~
sudo yum install gcc-c++.x86_64 cmake.x86_64 git.x86_64
sudo yum install boost-devel.x86_64 boost-static.x86_64 numactl-devel.x86_64 libaio-devel.x86_64
sudo yum install zlib-devel.x86_64
sudo yum install centos-release-SCL.x86_64
sudo wget -O /etc/yum.repos.d/slc6-devtoolset.repo http://linuxsoft.cern.ch/cern/devtoolset/slc6-devtoolset.repo
sudo yum install devtoolset-2 --nogpgcheck
scl enable devtoolset-2 bash

cd ${base}/
git clone https://github.com/icoming/FlashGraph.git
cd FlashGraph
mkdir build
cd build
cmake ../ -DBoost_NO_BOOST_CMAKE=BOOL:ON
make
~~~

## m2g

### igraph

~~~
yum -y install xml2 libxml2-devel
mkdir -p ${base}/src/igraph
cd ${base}/src/igraph
wget http://igraph.org/nightly/get/c/igraph-0.7.1.tar.gz
tar xvfz igraph-0.7.1.tar.gz
cd igraph-0.7.1
./configure --prefix=${base}/src/igraph
make
make install
easy_install python-igraph
cd ${base}/src/igraph
git clone https://gist.github.com/15015a9485d87d8c22e6.git
cd 15015a9485d87d8c22e6
yum -y install freeglut-devel mesa-libGL-devel
Rscript installRigraph.R
~~~

### Camino

~~~
cd ${base}/src/
git clone git://git.code.sf.net/p/camino/code camino
cd camino
make
git checkout voxelSpaceStreamlines
make clean
make
~~~

Camino is developed in Java, which means that sometimes extra threads are unintentionally spun up when launching cluster jobs. Some modifications must then be made to the java calls in the camino executable directory. A gist has been created which should automate this process for you.

~~~
cd ${base}/src/camino
git clone https://gist.github.com/f76897351be151ec228e.git fix_java
chmod -R +x fix_java/
./fix_java/single_java.sh
~~~

### FSL

~~~
mkdir -p ${base}/src/fsl
cd ${base}/src/fsl
wget http://openconnecto.me/data/public/MR/m2g_v1_1_0/deps/fsl-5.0.8-centos6_64.tar.gz
tar zxvf fsl-5.0.8-centos6_64.tar.gz
mv fsl/* ./
rm -r fsl
~~~

### m2g

~~~
export m2g=${base}/m2g
export M2G_HOME=${m2g}
cd ${base}
git clone https://github.com/openconnectome/m2g.git m2g
cd ${m2g}/MR-OCP/mrcap
python setup.py install
cd ${m2g}
python ${m2g}/packages/utils/setup.py
cd ${base}
git clone https://github.com/openconnectome/FlashR.git
~~~

## bash files

/etc/profile.d/neurodata.sh

~~~
export base=/share0
export JAVA_HOME=${base}/src/java/jdk1.7.0_71
export PATH='/usr/local/bin':${PATH}
~~~

/etc/profile.d/m2g.sh

~~~
export base=/share0
# m2g
export m2g=${base}/m2g
export M2G_HOME=${m2g} #both exist for legacy reasons
export PATH=${PATH}:${m2g}/MR-OCP/mrcap
export PATH=${PATH}:${m2g}/packages/*
export PYTHONPATH=${m2g}/MR-OCP
export PYTHONPATH=${PYTHONPATH}:${m2g}/MR-OCP/MROCPdjango:${m2g}/MR-OCP/mrcap:${m2g}

# Camino
export PATH=${base}/src/camino/bin:$PATH
export CAMINO_HEAP_SIZE=16000

# FSL
FSLDIR=${base}/src/fsl
. ${FSLDIR}/etc/fslconf/fsl.sh
PATH=${FSLDIR}/bin:${PATH}
export FSLDIR PATH
~~~

## Publishing AMI

Prior to releasing the AMI on the AWS marketplace, a few housekeeping commands must be run to ensure security of both the developer and the users. Run the following as root.

~~~
groupadd nd-users
usermod -g nd-users neurodata
usermod -g nd-users ec2-user
chown -R neurodata:nd-users ${base}
rm -rf ~/.bash_history  ~/.viminfo
touch ~/.bash_history  ~/.viminfo
~~~

## Connecting to AMI

### Creating and Instance

Currently the AMI is only released in the US-East Community Marketplace on AWS. Enter the dialog to create a new EC2 instance, select Community AMIs, and then search for 'neurodata' and select the version of the AMI you wish to use. You can then proceed with EC2 setup as you would with any other instance type.

### SSH

The user should locate the instance in the Amazon Marketplace and create an instance based on the AMI. Then, when connecting, the following command should be used: ''ssh neurodata@${ip}''; the user will be prompted with the password for this user (default pass should be ''neurodata'').

### VNC through SSH Tunnel

To connect, from your machine type:

~~~
  ssh -L 5901:127.0.0.1:5901 -N -f -l neurodata ${ip}
~~~

Then in your VNC client connect to ''localhost:5901'' and enter the vnc password you set during setup.
