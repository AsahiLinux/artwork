SOURCES=$(wildcard src/*.svg)
TARGETS=$(patsubst src/%.svg,svg/%.svg,$(SOURCES)) \
	$(patsubst src/%.svg,png_1x/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_2x/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_512/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_256/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_128/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_64/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_48/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_32/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_16/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_16/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,icns/%.icns,$(SOURCES)) \
	boot_logo.ppm

all: $(TARGETS)

svg/%.svg : src/%.svg
	inkscape $< --vacuum-defs --export-plain-svg=$@

png_1x/%.png : src/%.svg
	inkscape $< --export-dpi 96 --export-png=$@

png_2x/%.png : src/%.svg
	inkscape $< --export-dpi 192 --export-png=$@

png_512/%.png : src/%.svg
	inkscape $< --export-width 512 -o $@

png_256/%.png : src/%.svg
	inkscape $< --export-width 256 --export-png=$@

png_128/%.png : src/%.svg
	inkscape $< --export-width 128 --export-png=$@

png_64/%.png : src/%.svg
	inkscape $< --export-width 64 --export-png=$@

png_48/%.png : src/%.svg
	inkscape $< --export-width 48 -o $@

png_32/%.png : src/%.svg
	inkscape $< --export-width 32 --export-png=$@

png_16/%.png : src/%.svg
	inkscape $< --export-width 16 --export-png=$@

icns/%.icns: png_16/%.png png_32/%.png png_48/%.png png_128/%.png png_256/%.png png_512/%.png
	png2icns $@ png_{16,32,48,128,256,512}/$(patsubst icns/%.icns,%.png,$@)

boot_logo.ppm: src/AsahiLinux_logomark.svg
	inkscape src/AsahiLinux_logomark.svg --export-area=24:24:550:550 \
		--export-width 80 --export-background=black \
		--export-png=- | \
		pngtopnm | ppmquant 224 | pnmtoplainpnm > $@
