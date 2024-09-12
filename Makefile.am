AUTOMAKE_OPTIONS = dist-bzip2 no-dist-gzip
ACLOCAL_AMFLAGS = -I m4
SUBDIRS = libwdi

if BUILD_EXAMPLES
SUBDIRS += examples
ZADIG_VERSION = $(shell sed -n 's/^.*\"FileVersion\", \"\(.*\)\..*\"/\1/p' examples/zadig.rc)
endif

# This step produces the UPX compressed and signed releases that are made available for public download
# NB: UPX v3.09 or later is needed for LZMA compression (http://upx.sourceforge.net/)
zadig_release:
	@cp examples/"Vkinging DAQ Driver.exe" ./"Vkinging DAQ Driver"-$(ZADIG_VERSION).exe
	@upx --lzma "Vkinging DAQ Driver"-$(ZADIG_VERSION).exe
	@cmd.exe //c _sign.cmd "Vkinging DAQ Driver"-$(ZADIG_VERSION).exe
