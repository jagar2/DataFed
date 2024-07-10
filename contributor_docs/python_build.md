# Building the Python Library

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