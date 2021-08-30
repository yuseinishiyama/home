deploy:
	kubectl apply -n kube-system -f .

cert-manager:
	helm repo add jetstack https://charts.jetstack.io
	helm repo update
	# TODO: currently manual modification is needed because of a pod reachability issue inside LAN
	# use 'upgrade' instead once the issue is resolved
	helm template cert-manager jetstack/cert-manager \
		-n kube-system \
		--set installCRDs=true \
		--install --atomic --cleanup-on-fail > cert-manager.yaml
