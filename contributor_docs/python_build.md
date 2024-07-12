# Building the Python Library

## Requirements CMake

```bash
./DataFed/scripts/install_core_dependencies.sh
```

```bash
test -f /usr/share/doc/kitware-archive-keyring/copyright ||
wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | sudo tee /usr/share/keyrings/kitware-archive-keyring.gpg >/dev/null
```

```bash
echo 'deb [signed-by=/usr/share/keyrings/kitware-archive-keyring.gpg] https://apt.kitware.com/ubuntu/ jammy main' | sudo tee /etc/apt/sources.list.d/kitware.list >/dev/null
sudo apt-get update
sudo snap install cmake --classic
```

## Requirements Protobuf

```bash
git clone https://github.com/protocolbuffers/protobuf.git
cd protobuf
git checkout v25.2
sudo apt-get install -y autoconf automake libtool curl make g++ unzip
git submodule update --init --recursive
cmake -B build
cmake --build build
```

## Build

### Build the generate datafed bash script

```bash
./scripts/generate_datafed.sh
```

ensure you are in the base directory of the project.

```bash
cmake -S . -B build -DBUILD_WEB_SERVER=FALSE -DBUILD_PYTHON_CLIENT=TRUE -DBUILD_COMMON=FALSE -DBUILD_FOXX=FALSE -DBUILD_CORE_SERVER=FALSE
```

```bash
cmake --build build -j8
```

```bash
cmake --build build --target pydatafed
```