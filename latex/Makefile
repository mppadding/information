###
# Configuration
###
MAIN=main
SDIR=src
BDIR=build
OUT=report

# Latex tool to use
LATEXCC=pdflatex
LATEXARGS=--shell-escape

###
# Stages
###
all: clean_all build clean run

clean:
		@echo "=== Cleaning ==="
		rm main.aux -f
		rm main.log -f
		rm main.bbl -f
		rm main.bcf -f
		rm main.blg -f
		rm main.out -f
		rm main.run.xml -f

clean_all:
		@echo "=== Cleaning All ==="
		rm main.pdf -f
		rm main.aux -f
		rm main.log -f
		rm main.bbl -f
		rm main.bcf -f
		rm main.blg -f
		rm main.out -f
		rm main.run.xml -f

build:
		@echo "=== Building ==="
		$(LATEXCC) $(LATEXARGS) $(MAIN)
		biber main
		$(LATEXCC) $(LATEXARGS) $(MAIN)

run:
		@echo "=== Running ==="
		zathura main.pdf
