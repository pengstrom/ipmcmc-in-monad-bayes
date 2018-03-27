LATEX=pdflatex
LATEXOPT=--shell-escape
NONSTOP=--interaction=batchmode

LATEXMK=latexmk
LATEXMKOPT=-pdf -bibtex	
CONTINUOUS=-pvc

MAIN=thesis
SOURCES=$(MAIN).tex Makefile references.bib 1-intro/introduction.tex 2-body/body.tex 3-conclusion/conclusion.tex appendix/appendix.tex
FIGURES := $(shell find figures/* images/* -type f)

all: $(MAIN).pdf

.refresh:
	touch .refresh

$(MAIN).pdf: $(MAIN).tex .refresh $(SOURCES) $(FIGURES)
	$(LATEXMK) $(LATEXMKOPT) $(CONTINUOUS) \
		-pdflatex="$(LATEX) $(LATEXOPT) $(NONSTOP) %O %S" $(MAIN)

force:
	touch .refresh
	rm $(MAIN).pdf
	$(LATEXMK) $(LATEXMKOPT) $(CONTINUOUS) \
		-pdflatex="$(LATEX) $(LATEXOPT) $(NONSTOP) %O %S" $(MAIN)

clean:
	$(LATEXMK) -C $(MAIN)
	rm -f $(MAIN).pdfsync
	rm -rf *~ *.tmp
	rm -f *.bbl *.blg *.aux *.end *.fls *.log *.out *.fdb_latexmk
	rm -rf _minted-$(MAIN)

once:
	$(LATEXMK) $(LATEXMKOPT) -pdflatex="$(LATEX) $(LATEXOPT) %O %S" $(MAIN)

debug:
	$(LATEX) $(LATEXOPT) $(MAIN)

.PHONY: clean force once all
