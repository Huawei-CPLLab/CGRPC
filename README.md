# CGRPC

CGRPC is a Swift 3.0 wrapper for the C core library of [GRPC](https://github.com/grpc/grpc). A working installation of GRPC is required; `pkg-config` should be able to generate the correct CFLAGS and LDFLAGS for using the library.

## Caveat

The Swift front-end currently does not allow an imported module to include `pthread.h`; it will complain about symbol redefinition, because libpthread symbols are automatically imported by default. We work around this by modifying the GRPC headers to remove references to `pthread.h`. You can do this during installation by applying the patch `grpc-header-hack.diff` to the GRPC installation:

```bash
cd /usr/local/include
sudo patch -p1 < ~/CGRPC/grpc-header-hack.diff
```
