# gorocksdb, a Go wrapper for RocksDB

## Install

This fork exists mainly for compatiability with rocksdb v4.11.2 with lz4 compression.
Additionaly, it has an Unsafe Iterator.

### Install Rocksdb

```
sudo apt-get install -y build-essential checkinstall
sudo apt-get install libgflags-dev
sudo apt-get install libsnappy-dev zlib1g-dev libbz2-dev liblz4-1 liblz4-tool liblz4-dev

git clone https://github.com/facebook/rocksdb.git
cd rocksdb
git checkout v4.11.2
make shared_lib

# Optional step to add it to the default location
make install-shared INSTALL_PATH=/usr
```

```
mkdir -p $GOPATH/src/github.com/deep-compute && cd $_ && git clone https://github.com/deep-compute/gorocksdb.git
cd gorocksdb
git checkout v4.11.2-lz4-unsafe-iterator

# If rocksdb was installed at the /usr install path
CGO_CFLAGS="-I/usr/include/rocksdb" CGO_LDFLAGS="-L/usr/lib -lrocksdb -lstdc++ -lm -lz -lbz2 -lsnappy -llz4" go install
```
