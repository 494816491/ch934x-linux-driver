ifeq ($(KERNELRELEASE), )
KERNELDIR := /lib/modules/$(shell uname -r)/build
PWD :=$(shell pwd)
default:
	$(MAKE) -C $(KERNELDIR)  M=$(PWD)  
clean:
	rm -rf *.mk .tmp_versions Module.symvers *.mod.c *.o *.ko .*.cmd Module.markers modules.order
load:
	insmod ch934x.ko
unload:
	rmmod ch934x
install: default
	mkdir -p /lib/modules/$(shell uname -r)/kernel/drivers/usb/serial/
	cp -f ./ch934x.ko /lib/modules/$(shell uname -r)/kernel/drivers/usb/serial/
	depmod -a
uninstall:
	rm -rf /lib/modules/$(shell uname -r)/kernel/drivers/usb/serial/ch934x.ko
	depmod -a
else
	obj-m := ch934x.o
endif
