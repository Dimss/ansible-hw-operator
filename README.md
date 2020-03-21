## Ansible Operator Demo

1.Run pure Ansible
```bash
# run playbook
pipenv run ansible-playbook hw.yml -e '{"meta":{"namespace":"hwop","name":"hw-site"},"message":"Hello world!}'
```
2.Run playbook as Operator
```bash
operator-sdk up local --namespace=hwop --watches-file=watches-dev.yaml
```
3.Build image locally
```bash
operator-sdk build test
```
4.Build image remotely with OCP Custom build
```bash
oc create -f ocp/bc.yaml
oc start-build -F ansible-operatorsdk-builder
```
5.Deploy Operator on OCP
```bash
oc create -f deploy/role.yaml
oc create -f deploy/service_account.yaml
oc create -f deploy/role_binding.yaml
oc create -f deploy/operator.yaml
```