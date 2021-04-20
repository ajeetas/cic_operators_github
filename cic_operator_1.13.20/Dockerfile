# Build the manager binary
FROM quay.io/operator-framework/helm-operator:v1.5.1

LABEL name="Citrix Ingress Controller Operator" \
      vendor="Citrix" \
      version="v1.13.20" \
      release="1" \
      summary="This is an Citrix Ingress Controller helm operator." \
      description="This operator will deploy Citrix Ingress Controller to the cluster."

USER root
RUN microdnf install yum
RUN microdnf update -y
RUN yum  -y update-minimal --security --sec-severity=Important --sec-severity=Critical
RUN yum clean all
RUN microdnf remove yum
RUN microdnf clean all
USER helm

COPY licenses /licenses
ENV HOME=/opt/helm
COPY watches.yaml ${HOME}/watches.yaml
COPY helm-charts  ${HOME}/helm-charts
WORKDIR ${HOME}
