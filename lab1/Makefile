.PHONY: tex watch full clean server-up server-down

full: render tex

tex:
	latexmk report.tex --shell-escape -pdf

watch:
	fd --type f --regex '(.*plantuml$$)|report.tex$$' . | entr -n -s "make full"

render:
	mkdir -p diagrams/output
	cd diagrams && find -name "*.plantuml" | xargs -I{} curl localhost:8080/png --data-binary @{} --output output/{}-rendered.png
clean:
	rm -r diagrams/output
	latexmk -c report.tex

server-up:
	docker run --rm -d -p 8080:8080 plantuml/plantuml-server:jetty
	sleep 2
server-down:
	docker stop $$(docker ps | grep plantuml/plantuml-server:jetty | cut -d' ' -f1)
