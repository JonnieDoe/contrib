VERSION := $(shell ./scripts/get-version.sh)
REPOSITORY := openpolicyagent/demo-kafka

clean:
	rm -fr target

build: jar image

image:
	sed s/VERSION/$(VERSION)/g Dockerfile.in > Dockerfile
	docker build -t openpolicyagent/demo-kafka:$(VERSION) -t openpolicyagent/demo-kafka:latest .

jar:
	./scripts/build.sh

push: build
	docker push $(REPOSITORY):$(VERSION)
	docker push $(REPOSITORY):latest
