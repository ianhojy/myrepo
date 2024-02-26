.PHONY: build-local run-local cleanup-local all-local

build-local:
	docker build --platform linux/amd64 -t workshop01-flask-app .

tag-push:
	docker tag workshop01-flask-app registry.heroku.com/cfdsa-test-app/web
	docker push registry.heroku.com/cfdsa-test-app/web

run-local:
	-docker run --rm -p 5000:5000 -e PORT=5000 workshop01-flask-app

cleanup-local:
	docker container prune -f
	docker image prune -f
	-docker rmi workshop01-flask-app

all-local: build-local
	$(MAKE) run-local || true
	$(MAKE) cleanup-local
