# Makefile for LaTeX compilation

MAIN = main
LATEX = pdflatex
BIBTEX = bibtex

all: $(MAIN).pdf

$(MAIN).pdf: $(MAIN).tex references.bib
	$(LATEX) $(MAIN).tex
	$(BIBTEX) $(MAIN)
	$(LATEX) $(MAIN).tex
	$(LATEX) $(MAIN).tex

clean:
	rm -f $(MAIN).aux $(MAIN).log $(MAIN).bbl $(MAIN).blg $(MAIN).out $(MAIN).toc $(MAIN).lof $(MAIN).lot

cleanall: clean
	rm -f $(MAIN).pdf

.PHONY: all clean cleanall
