# linuxcnc-ethercat
LinuxCNC EtherCAT HAL driver
*******************************

linuxcnc-ethercat驱动编译:
1,先编译通过:https://github.com/synapticon/Etherlab_EtherCAT_Master和https://github.com/LinuxCNC/linuxcnc
2,下载:$git clone https://github.com/sittner/linuxcnc-ethercat.git linuxcnc-ethercat
3,在.bashrc的$PATH中加入halcompile这个命令的路径（linuxcnc-dev/bin），让shell命令which能找到halcompile命令，
  $vim ~/.bashrc,加入:
   ...
   PATH=~/linuxcnc-dev/bin:$PATH
   ...
4,$cd ~/linuxcnc-ethercat 
5,修改src/realtime.mk第19行: 
LDFLAGS += -Wl,-rpath,$(LIBDIR) -L$(LIBDIR) -llinuxcnchal -lethercat
为:LDFLAGS += -Wl,-rpath,$(LIBDIR) -L$(LIBDIR) -llinuxcnchal -lethercat -L/opt/etherlab/lib
6,$make
  $sudo make install
  就能编译了
