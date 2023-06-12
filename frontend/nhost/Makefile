install:
	yarn install

prepare-version:
	git fetch upstream --tags
	git checkout tags/$(VERSION)
	git checkout -b patch/$(VERSION)
	git cherry-pick $(COMMIT)


build: install
	cd ../ && \
		yarn nx build-server-assets console-ce


build-docker-image:
	docker buildx build \
		--push \
		--build-arg VERSION=$(VERSION) \
		--platform linux/amd64,linux/arm64 \
		-t nhost/graphql-engine:$(VERSION) \
		-f ./Dockerfile \
		../


build-images: build
	$(MAKE) build-docker-image VERSION=$(VERSION)
	$(MAKE) build-docker-image VERSION=$(VERSION).cli-migrations-v3


build-docker-image-local:
	docker build \
		--build-arg VERSION=$(VERSION) \
		-t nhost/graphql-engine:$(VERSION) \
		-f ./Dockerfile \
		../


build-images-local: build
	$(MAKE) build-docker-image-local VERSION=$(VERSION)
	$(MAKE) build-docker-image-local VERSION=$(VERSION).cli-migrations-v3
