deploy: cert-manager

cert-manager:
	helm repo add jetstack https://charts.jetstack.io
	helm repo update
	helm upgrade cert-manager jetstack/cert-manager \
		-n kube-system \
		--set installCRDs=true \
		--install --atomic --cleanup-on-fail
