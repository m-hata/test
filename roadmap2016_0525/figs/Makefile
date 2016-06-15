PDF_XBB := $(patsubst %.pdf,%.xbb,$(wildcard *.pdf))
PNG_XBB := $(patsubst %.png,%.xbb,$(wildcard *.png))
ALL = $(PDF_XBB) $(PNG_XBB)

.SUFFIXES: .png .pdf .xbb
.png.xbb:
	ebb -x $<

.pdf.xbb:
	extractbb $<

all: $(ALL)

clean:
	rm -rf *.xbb

