# This is a multi-stage Dockerfile.

# The first stage builds Spot.
FROM gcc:14.2-bookworm AS build
ADD spot-2.13.0.dev.tar.gz /
RUN cd /spot-2.13.0.dev && \
    ./configure --disable-devel --disable-shared --enable-optimizations --disable-python --prefix /usr && \
    make -j8 && \
    make install-strip

# The second stage installs the result of that build in a smaller Debian image.
FROM debian:12.10-slim
COPY --from=build /usr/local/lib64/libstdc++.so* /usr/local/lib64/libgcc_s.so* /usr/local/lib64/
COPY --from=build /usr/bin/ltl*synt /usr/bin/
COPY binaries/* /usr/bin/
CMD ["/bin/bash"]
