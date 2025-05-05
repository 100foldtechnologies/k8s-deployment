Running our k8s on minikube

- Deploy your manifest - deployment, service, ingress
- For ingress to work, you need an ingress controller and the popular option is the 
ingress nginx controller.
- For minikube, you must run minikube tunnel

`ConfigMaps and Secret`
- Two way to passing either configmap and secret
- 1. environmental variable
#        env:
#          - name: DB-PORT
#            valueFrom:
#              configMapKeyRef:
#                name: test-cm
#                key: db-port
#          - name: secret
#            valueFrom:
#              secretKeyRef:
#                name: dotfile-secret
#                key: password

2. Passing it in as a volume which is recommended
  2a.       volumes:
   - name: db-port
   configMap:
   name: test-cm
   - name: password
   secret:
   secretName: dotfile-secret
- 
2b.         volumeMounts:
- name: db-port
mountPath: /data
- name: password
mountPath: /opt



- Namespace!