all: container-image-built
TAG=debian

libpng: 
	mkdir -p libpng
	curl -LO https://snapshot.debian.org/archive/debian/20160413T160058Z/pool/main/libp/libpng/libpng12-0_1.2.54-6_amd64.deb
	mv libpng12-0_1.2.54-6_amd64.deb libpng/

container-image-built: libpng Dockerfile fpga
	@docker rmi fpga-base:$(TAG) &>/dev/null || true
	docker build -t fpga-base:$(TAG) .
	@touch $@

.PHONY: clean
clean:
	docker rmi fpga-base:$(TAG) &>/dev/null || true
	rm -f container-image-built