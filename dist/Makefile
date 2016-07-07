#!/usr/bin/make -f
# -*- makefile -*-

VERSION=0.0.1~beta20160630

DEBIAN_DIR=tidb-$(VERSION)
DEBIAN_TEMPLATE=debian

build-deb: update
	cd $(DEBIAN_DIR); fakeroot dpkg-buildpackage -F

publish-deb: update
	cd $(DEBIAN_DIR); fakeroot dpkg-buildpackage -S

update:
	mkdir -m 755 -p $(DEBIAN_DIR)
	cp -R $(DEBIAN_TEMPLATE) $(DEBIAN_DIR)
	cp ../tidb-server/tidb-server $(DEBIAN_DIR)/tidb
	cp ../interpreter/interpreter $(DEBIAN_DIR)/ticl
	tar -cvzf tidb_$(VERSION).orig.tar.gz $(DEBIAN_DIR)

clean-deb:
	-rm *.deb
	-rm *.tar.gz
	-rm *.changes
	-rm *.dsc
	-rm -rf $(DEBIAN_DIR)
