DOCKER_REGISTORY = 921647845311.dkr.ecr.eu-west-1.amazonaws.com
APP = reverse-tunnel
IMAGE = $(DOCKER_REGISTORY)/$(APP)

build:
	docker build --build-arg GOARCH=arm64 --build-arg GOARM=7 -t $(APP):arm64v7 .

publish: build
	aws ecr get-login-password --region eu-west-1 --profile private | \
		docker login --username AWS --password-stdin $(DOCKER_REGISTORY)
	docker tag $(APP):arm64v7 $(IMAGE):arm64v7
	docker push $(IMAGE):arm64v7

docker-secret:
	@kubectl get secret ecr -n reverse-tunnel || \
	kubectl create secret docker-registry ecr \
		--namespace=reverse-tunnel \
		--docker-server=921647845311.dkr.ecr.eu-west-1.amazonaws.com \
		--docker-username=AWS \
		--docker-password=$(shell aws ecr get-login-password --profile private)

deploy:
	kubectl apply -n reverse-tunnel -f .
