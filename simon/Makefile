
# Makefile for building specific CV versions

TEX = xelatex
# Output filenames
# Output filenames
UK_EM_TARGET = Simon-Aquino-CV_EM_UK
EU_EM_TARGET = Simon-Aquino-CV_EM_EU
UK_IC_TARGET = Simon-Aquino-CV_IC_UK
EU_IC_TARGET = Simon-Aquino-CV_IC_EU
COVER_TARGET = Simon-Aquino-CoverLetter

# Source file
SOURCE = cv.tex
COVER_SOURCE = coverletter.tex

.PHONY: all uk-em eu-em uk-ic eu-ic cover clean

all: uk-em eu-em uk-ic eu-ic cover

# EM targets
uk-em:
	$(TEX) -jobname=$(UK_EM_TARGET) "\def\cvdir{cv-em}\input{$(SOURCE)}"

eu-em:
	$(TEX) -jobname=$(EU_EM_TARGET) "\def\showphoto{1}\def\cvdir{cv-em}\input{$(SOURCE)}"

# IC targets
uk-ic:
	$(TEX) -jobname=$(UK_IC_TARGET) "\def\cvdir{cv-ic}\input{$(SOURCE)}"

eu-ic:
	$(TEX) -jobname=$(EU_IC_TARGET) "\def\showphoto{1}\def\cvdir{cv-ic}\input{$(SOURCE)}"

cover:
	$(TEX) -jobname=$(COVER_TARGET) $(COVER_SOURCE)

clean:
	rm -f *.aux *.log *.out *.pdf
