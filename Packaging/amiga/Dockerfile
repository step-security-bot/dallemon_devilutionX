FROM amigadev/crosstools:m68k-amigaos-gcc10@sha256:ab140f6e763a3b49e104b7125efafb6e5433a8931f955a41bced8ef0e3ab2d9c

RUN apt-get install --no-install-recommends -y smpq
RUN mkdir /devilutionx-deps-build
COPY Packaging/amiga/prep.sh /devilutionx-deps-build/prep.sh
RUN cd /devilutionx-deps-build && ./prep.sh

CMD cmake -S. -Bbuild-amiga -DCPACK=ON \
		-DCMAKE_BUILD_TYPE=Release \
		-DM68K_CPU=68040 \
		-DM68K_FPU=hard \
		-DM68K_COMMON="-s -fbbb=- -ffast-math" && \
	cmake --build build-amiga -j $(nproc)
