# cat nodedeploy.yaml 
apiVersion: apps/v1beta1
kind: Deployment
metadata:
 name: nodeplatform-deployment
spec:
 replicas: 2
 template:
 metadata:
 labels: # labels to select/identify the deployment
 app: hello-world 
 spec: # pod spec 
 containers: 
 - name: nodeplatform
 image: rampro/nodejs-helloworld
 ports:
 - containerPort: 3000
---
apiVersion: v1
kind: Service
metadata:
 name: nodeplatform-service
spec:
 selector:
 app: hello-world
# spec: # pod spec
 type: LoadBalancer
 ports: 
 - port: 8080
