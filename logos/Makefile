SOURCES=$(wildcard src/*.svg)
TARGETS=$(patsubst src/%.svg,svg/%.svg,$(SOURCES)) \
	$(patsubst src/%.svg,png_1x/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_2x/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_64/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_32/%.png,$(SOURCES)) \
	$(patsubst src/%.svg,png_16/%.png,$(SOURCES))

all: $(TARGETS)

svg/%.svg : src/%.svg
	inkscape $< --vacuum-defs --export-plain-svg=$@

png_1x/%.png : src/%.svg
	inkscape $< --export-dpi 96 -o $@

png_2x/%.png : src/%.svg
	inkscape $< --export-dpi 192 -o $@

png_64/%.png : src/%.svg
	inkscape $< --export-width 64 -o $@

png_32/%.png : src/%.svg
	inkscape $< --export-width 32 -o $@

png_16/%.png : src/%.svg
	inkscape $< --export-width 16 -o $@
