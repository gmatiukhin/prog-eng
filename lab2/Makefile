.PHONY: tex watch

tex:
	latexmk spec.tex --shell-escape -pdf

watch:
	echo "spec.tex" | entr -n -s "make tex"

clean:
	latexmk -c spec.tex
