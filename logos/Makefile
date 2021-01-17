SOURCES=$(wildcard src/*.svg)
TARGETS=$(patsubst src/%.svg,svg/%.svg,$(SOURCES)) \
	$(patsubst src/%.svg,png_1x/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_2x/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_256/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_128/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_64/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_32/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_16/%.png,$(SOURCES)) \
	boot_logo.ppm

all: $(TARGETS)

svg/%.svg : src/%.svg
	inkscape $< --vacuum-defs --export-plain-svg=$@

png_1x/%.png : src/%.svg
	inkscape $< --export-dpi 96 -o $@

png_2x/%.png : src/%.svg
	inkscape $< --export-dpi 192 -o $@

png_256/%.png : src/%.svg
	inkscape $< --export-width 256 -o $@

png_128/%.png : src/%.svg
	inkscape $< --export-width 128 -o $@

png_64/%.png : src/%.svg
	inkscape $< --export-width 64 -o $@

png_32/%.png : src/%.svg
	inkscape $< --export-width 32 -o $@

png_16/%.png : src/%.svg
	inkscape $< --export-width 16 -o $@

boot_logo.ppm: src/AsahiLinux_logomark.svg
	inkscape src/AsahiLinux_logomark.svg --export-area=24:24:550:550 \
		--export-width 80 --export-type=png \
		--export-background=black -o - | \
		pngtopnm | ppmquant 224 | pnmtoplainpnm > $@

