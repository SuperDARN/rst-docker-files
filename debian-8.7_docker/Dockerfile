FROM debian:8.7
RUN apt-get -qq update

RUN apt-get -y install wget
RUN apt-get -y install make
RUN apt-get -y install vim
RUN apt-get -y install git
RUN apt-get -y install gcc

RUN apt-get -y install libx11-dev
RUN apt-get -y install libxext-dev
RUN apt-get -y install libhdf5-serial-dev
RUN apt-get -y install libnetcdf-dev
RUN apt-get -y install libncurses-dev
RUN apt-get -y install netpbm
RUN apt-get -y install libpng12-dev

RUN cd /root && wget https://spdf.sci.gsfc.nasa.gov/pub/software/cdf/dist/cdf36_3_1/linux/cdf36_3_1-dist-all.tar.gz
RUN cd /root && tar -xf cdf36_3_1-dist-all.tar.gz
RUN cd /root/cdf36_3-dist && make clean && make OS=linux ENV=gnu all && make INSTALLDIR=/usr/local/cdf install

RUN cd /root && git clone https://github.com/SuperDARN/rst.git
RUN printf "export RSTPATH=/root/rst\n. \$RSTPATH/.profile.bash\nexport CDF_PATH=/usr/local/cdf" >> /root/.bashrc
#RUN rm -rf /root/rst/codebase/superdarn/src.lib/tk/idl
