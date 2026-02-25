packages=clementine.deb
repo=tp-dj

GIT_COMMIT := $(shell git rev-parse HEAD)

all: $(packages)
	aptly repo remove $(repo) clementine
	aptly repo add $(repo) clementine.deb

clementine.deb:
	mkdir -p scratch/usr/bin
	rsync -av src/ scratch/
	rsync -av ../bin/clementine scratch/usr/bin
	rsync -av ../bin/clementine-tagreader scratch/usr/bin
	m4 control.m4 > src/DEBIAN/control
	dpkg-deb --build scratch clementine.deb

clean:
	rm -f $(packages)
	rm -fr scratch


