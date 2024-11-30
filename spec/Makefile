.PHONY: tex watch

tex:
	@latexmk main.tex --shell-escape -pdf

watch:
	@echo "main.tex" | entr -n -s "make tex"
