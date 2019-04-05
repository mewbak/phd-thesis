PAPER = prelim_proposal

TEX = $(wildcard *.tex)

BIB =
FIGS =

.PHONY: all clean error-check

all: $(PAPER).pdf error-check

error-check: $(PAPER).pdf
	@echo ""
	@echo "++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"
	@echo "               ++++ ANY UNDEFINED REFERENCES ++++"
	-@grep -i undef $(PAPER).log |grep -v "Font Warning"  || echo "No undefined references."
	@echo "                 ++++ ANY EMPTY REFERENCES ++++"
	-@egrep -i -n -e 'cite{ *}' -e 'ref{ *}' $(TEX) || echo "No empty references."
	@echo "++++++++++++++++++++++++++++++++++++++++++++++++++++++++++"
	@echo ""

$(PAPER).pdf: $(TEX) $(BIB) $(FIGS)
	pdflatex $(PAPER)
	bibtex $(PAPER)
	pdflatex $(PAPER)
	pdflatex $(PAPER)

clean:
	rm -f *.aux  ${PAPER}.bbl ${PAPER}.blg ${PAPER}.log ${PAPER}.out ${PAPER}.pdf comment.cut ${PAPER}.lof ${PAPER}.lot ${PAPER}.toc
