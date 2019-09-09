FROM quay.io/operator-framework/ansible-operator:v0.10.0 
RUN pip install requests google-auth
COPY watches.yaml  ${HOME}/watches.yaml
COPY key.json /tmp/key.json 
COPY roles/ ${HOME}/roles/
