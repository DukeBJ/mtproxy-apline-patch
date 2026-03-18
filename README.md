# GetPageSpeed/MTProxy Patch for Alpine Linux

A patch for the GetPageSpeed/MTProxy repository (https://github.com/GetPageSpeed/MTProxy) to enable building the MTProxy application in Alpine Linux.

Fixes build errors:
- error: 'int32_t' undeclared (first use in this function)
- error: passing argument 2 of 'connect' from incompatible pointer type [-Wincompatible-pointer-types]

Tested on Alpine version 3.23.

## Installation Steps

1. **Install required packages**
   ```bash
   apk add git make gcc musl-dev linux-headers openssl-dev zlib-dev
   ```

2. **Clone the MTProxy repository**
   ```bash
   git clone --single-branch --depth 1 https://github.com/GetPageSpeed/MTProxy.git /mtproxy/sources
   ```

3. **Clone the patch repository**
   ```bash
   git clone --single-branch --depth 1 https://github.com/DukeBJ/mtproxy-apline-patch.git /mtproxy/patches
   ```

4. **Apply the patch**
   ```bash
   cd /mtproxy/sources
   patch -p0 -i /mtproxy/patches/randr_compat.patch
   ```

5. **Build the project**
   ```bash
   make -j$(getconf _NPROCESSORS_ONLN)
   ```
