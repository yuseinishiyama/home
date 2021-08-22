docker-secret:
	kubectl create secret docker-registry ecr \
		--docker-server=921647845311.dkr.ecr.eu-west-1.amazonaws.com \
		--docker-username=AWS \
		--docker-password=$(shell aws ecr get-login-password --profile private)
