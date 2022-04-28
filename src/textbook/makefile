SHELL=/bin/bash

.PHONY: all clean prepare chapter-all

PDFLATEX_FLAGS = -shell-escape -halt-on-error -output-directory ../../build/textbook/

define make_pdf
  export max_print_line=$$(tput cols); \
  pdflatex $(PDFLATEX_FLAGS) chemistry.tex && cp chemistry.bib ../../build/textbook/chemistry.bib; \
  cd ../../build/textbook/ && bibtex chemistry; \
  cd - && pdflatex $(PDFLATEX_FLAGS) chemistry.tex && pdflatex $(PDFLATEX_FLAGS) chemistry.tex;
endef

all: prepare chapter-all

prepare:
	mkdir -p ../../build/textbook

chapter-all: ../../build/textbook/chemistry.pdf

../../build/textbook/chemistry.pdf: chemistry.tex chemistry.bib
	$(call make_pdf)

clean:
	rm -rf ../../build/textbook/
