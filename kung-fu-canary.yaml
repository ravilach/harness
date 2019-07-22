apiVersion: apps/v1
kind: Deployment
metadata:
  name: kung-fu-canary
  namespace: default
spec:
  replicas: 3
  strategy:
   type: RollingUpdate
   rollingUpdate:
    maxSurge: 1
    maxUnavailable: 1
  selector:
    matchLabels:
      app: kung-fu-canary
  template:
    metadata:
      labels:
        app: kung-fu-canary
    spec:
      containers:
      - image: nginx
        imagePullPolicy: Always
        name: nginx
        ports:
        - containerPort: 80
        readinessProbe:
          httpGet:
            path: /
            port: 80
          initialDelaySeconds: 10
          periodSeconds: 5
          successThreshold: 1
