# Istio-complete

This is a useful resource for anyone interested in securing a Kubernetes cluster using Istio service mesh. It also includes a canary deployment demo along with all the necessary YAML files.

Prerequisites
---------------------------------------------
EKS cluster ready

kubectl and AWS CLI installed and configured

IAM permissions to install CRDs and Helm charts

---------------------------------------------
Install Istio CLI

curl -L https://istio.io/downloadIstio | sh -
cd istio-*
export PATH=$PWD/bin:$PATH

Install Istio Base and Control Plane

istioctl install --set profile=demo -y

Label Default Namespace for Istio Injection

kubectl label namespace default istio-injection=enabled


-------------------------------------------
Optional if enable mTls


cat <<EOF | kubectl apply -f -
apiVersion: security.istio.io/v1beta1
kind: PeerAuthentication
metadata:
  name: default
  namespace: istio-system
spec:
  mtls:
    mode: STRICT
EOF

-----------------------
Removing
rm -rf /home/ubuntu/istio-*

