LATEX=xelatex
LATEXOPT=--shell-escape
NONSTOP=--interaction=batchmode

LATEXMK=latexmk
LATEXMKOPT=-pdfxe
CONTINUOUS=-pvc

MAIN=presentation
SOURCES=$(MAIN).tex Makefile 
FIGURES := $(shell find images/* -type f)

all: $(MAIN).pdf

.refresh:
	touch .refresh

$(MAIN).pdf: $(MAIN).tex .refresh $(SOURCES) $(FIGURES)
	$(LATEXMK) $(LATEXMKOPT) $(CONTINUOUS) $(LATEXOPT) $(NONSTOP)

force:
	touch .refresh
	rm $(MAIN).pdf
	$(LATEXMK) $(LATEXMKOPT) $(CONTINUOUS) $(MAIN)

clean:
	$(LATEXMK) -C $(MAIN)
	rm -f $(MAIN).pdfsync
	rm -rf *~ *.tmp _minted-*
	rm -f *.bbl *.blg *.aux *.end *.fls *.log *.out *.fdb_latexmk *.nav *.snm *.vrb

once:
	$(LATEXMK) $(LATEXMKOPT) $(MAIN)

debug:
	$(LATEX) $(LATEXOPT) $(MAIN)

.PHONY: clean force once all
