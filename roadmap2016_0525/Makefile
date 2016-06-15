LATEX = platex
BIBTEX = pbibtex
DVIPDF = dvipdfmx

MAIN = Roadmap

TEX_SRCS = $(MAIN).tex macro.tex \
          1-1.tex 1-2.tex 1-3.tex \
          2-1.tex 2-2.tex 2-3.tex 2-4.tex 2-5.tex 2-6.tex \
		  2-7.tex 2-8.tex 2-9.tex 2-10.tex 2-11.tex \
          3-1.tex 3-2.tex \
          4-1.tex 4-2.tex 4-3.tex 4-4.tex 4-5.tex 4-6.tex \
          4-7.tex 4-8.tex 4-9.tex 4-10.tex 4-11.tex \
	      authors.tex glossary.tex

BIB_SRCS = $(wildcard *.bib)

SRCS = $(TEX_SRCS) $(BIB_SRCS)

BBLS = $(patsubst %.bib,%.bbl,$(BIB_SRCS))

BIB_AUXS = $(patsubst %.bib,%.aux,$(BIB_SRCS))


.SUFFIXES: .aux .bbl
.aux.bbl:
	$(BIBTEX) $<


all: $(MAIN).pdf

$(BIB_AUXS): $(SRCS)
	$(MAKE) -C figs
	$(LATEX) $(MAIN)

$(BBLS): $(BIB_AUXS)

$(MAIN).dvi: $(BBLS)
	$(LATEX) $(MAIN)
	$(LATEX) $(MAIN)

$(MAIN).pdf: $(MAIN).dvi
	$(DVIPDF) -p a4 $(MAIN).dvi


clean:
	rm -f *.dvi *.out *.bbl *.aux *.log *.toc *.blg
	$(MAKE) -C figs clean

distclean: clean
	rm -rf *.pdf

