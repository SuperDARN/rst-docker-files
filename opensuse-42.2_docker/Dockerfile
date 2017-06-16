FROM opensuse:42.2

RUN zypper ref

RUN zypper in -y git
RUN zypper in -y make
RUN zypper in -y gcc
RUN zypper in -y wget
RUN zypper in -y tar
RUN zypper in -y vim

RUN zypper in -y libX11-devel
RUN zypper in -y libXext6
RUN zypper in -y libXext-devel
RUN zypper in -y hdf5-devel
RUN zypper in -y zlib-devel
RUN zypper in -y netcdf
RUN zypper in -y netcdf-devel
RUN zypper in -y libpng16-devel
RUN zypper in -y ncurses-devel

RUN ln -s /usr/lib64/libncurses.so /usr/lib64/libcurses.so
RUN ln -s /usr/lib64/libncurses.a /usr/lib64/libcurses.a
RUN ln -s /usr/include/libpng16/png.h /usr/include/png.h
RUN ln -s /usr/include/libpng16/pnglibconf.h /usr/include/pnglibconf.h
RUN ln -s /usr/include/libpng16/pngconf.h /usr/include/pngconf.h
RUN ln -s /usr/lib64/libpng16.so /usr/lib64/libpng.so

RUN cd /root && wget https://spdf.sci.gsfc.nasa.gov/pub/software/cdf/dist/cdf36_3_1/linux/cdf36_3_1-dist-all.tar.gz
RUN cd /root && tar -xf cdf36_3_1-dist-all.tar.gz
RUN cd /root/cdf36_3-dist && make clean && make OS=linux ENV=gnu all && make INSTALLDIR=/usr/local/cdf install

RUN cd /root && git clone https://github.com/SuperDARN/rst.git
RUN printf "export RSTPATH=/root/rst\n. \$RSTPATH/.profile.bash" >> /root/.bashrc
#RUN rm -rf /root/rst/codebase/superdarn/src.lib/tk/idl

