# README-NG

## BUILD

`cp .devcontainer/devcontainer.example.jsonc .devcontainer/devcontainer.json`

- PROXY 方面，当前我在机器的 7890 开了个梯子 (HTTP+SOCKS5)，简单做了分流，可直接使用，有时候会不稳定。
- 需要修改路径，具体见 json 文件

Open command palette in VSCode and run `Dev Containers: Open Folder in Container`

Then

``` bash
# make sure you are at project root

# configure
CC=clang-12 CXX=clang++-12 cmake -B $PWD/build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=$PWD/install

# build
CC=clang-12 CXX=clang++-12 cmake --build $PWD/build
CC=clang-12 CXX=clang++-12 cmake --install $PWD/build

# test
pip install lit
cd build
lit --verbose tests
```
