clean:
  rm -rf requirements.lock
	rm -rf charts
	rm -rf ${NAME}*.tgz
  
build: clean
	helm init --client-only
	helm repo add activiti-cloud-helm-charts https://activiti.github.io/activiti-cloud-helm-charts/
	helm dependency build
	helm lint

install: clean build
	helm update .  --install --name ${HELM_RELEASE_NAME} --namespace jx-staging --debug --wait --timeout 3000
