## Ansible Operator Demo

1.Run pure Ansible
```bash
# run playbook
pipenv run ansible-playbook hw.yml -e '{"meta":{"namespace":"hwop","name":"hw-site"},"spec":{"message":"Hello world!"}}'
# check configmap
oc get cm hw-site -o json  | jq .data
```