CC=gcc
CFLAGS=-O2 -Wall -s
lanauthbin=lanauth
RANLIB=ranlib
md5lib=crypto/md5/lib
ripemdlib=crypto/ripemd/lib

all: lanauth

$(lanauthbin): libcrypto.a
	$(CC) $(CFLAGS) -I./include -L./ -o $(lanauthbin) lanauth.c -lcrypto 

libcrypto.a: $(md5lib) $(ripemdlib)

$(md5lib):
	$(MAKE) CFLAGS='${CFLAGS} -I.. -I../.. -I../../include' RANLIB='${RANLIB}' AR='${AR} r' -C crypto/md5 lib

$(ripemdlib):
	$(MAKE) CFLAGS='${CFLAGS} -I.. -I../.. -I../../include' RANLIB='${RANLIB}' AR='${AR} r' -C crypto/ripemd lib

clean:
	$(MAKE) -C crypto/md5 clean
	$(MAKE) -C crypto/ripemd clean
	rm -f *.a $(lanauthbin)

.PHONY: 
