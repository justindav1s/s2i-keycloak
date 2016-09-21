Openshift Keycloak S2i image

https://github.com/justindav1s/s2i-keycloak.git

git clone https://github.com/justindav1s/s2i-keycloak.git

Build a base image running Keycloak

Image built from Docker file

run :

make

or

docker build -t ib-keycloak .

oc --insecure-skip-tls-verify login https://ba.datr.eu:8443

oc whoami -t

get <registry_service_host:port> from registry pod in default project from console

docker login -u justin -e justin.davis@ba.com -p ........ 172.30.88.121:5000

docker tag ib-keycloak 172.30.88.121:5000/openshift/ib-keycloak
docker push 172.30.88.121:5000/openshift/ib-keycloak


oadm policy add-scc-to-user anyuid -z default
oc edit scc anyuid

docker pull jboss/keycloak-postgres
docker tag jboss/keycloak-postgres 172.30.88.121:5000/openshift/keycloak-postgres
docker push 172.30.88.121:5000/openshift/keycloak-postgres
oc new-app keycloak-postgres
oc deploy keycloak-postgres --cancel
oc deploy keycloak-postgres --latest
