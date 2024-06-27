kind: ConfigMap
apiVersion: v1
metadata:
  name: nginx-configmap
  namespace: frontend
  uid: 3860c338-e879-4388-96da-2109f9c53f2a
  resourceVersion: '3557798240'
  creationTimestamp: '2024-06-27T13:27:58Z'
  managedFields:
    - manager: Mozilla
      operation: Update
      apiVersion: v1
      time: '2024-06-27T16:04:44Z'
      fieldsType: FieldsV1
      fieldsV1:
        'f:data':
          .: {}
          'f:default.conf': {}
data:
  default.conf: |
    server {
      listen 8080;
      server_name example.com;
      location / {
        proxy_pass  http://frontendapp-ss-0:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;        
        post_action @post_action; 
      }

      location @post_action {
        internal;
        proxy_pass  http://frontendapp-ss-1:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;        
      }


    }
