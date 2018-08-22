# Instructions


1. Build docker image at `fluentd/`

```
docker build -t <fluentd-image> .
```

2. Push it to repository

```
docker push <fluentd-image>
```

3. Change image from `fluentd-daemonset.yml`

4. Configure logstash to send the logs to elasticsearch servers (`logstash-configmaps.yml`)

5. Apply logstash configmap
```
kubectl apply -f logstash-configmap.yml
```

6. Apply logstash deployment and service (normally using public logstash image)

```
kubectl apply -f logstash-deployment.yml
```

7. Apply Fluentd DaemonSet, Service and ServiceAccount
```
kubectl apply -f fluentd-daemonset.yml
```

8. Configure Fluentd ServiceAccount grants from UCP admin

fluentd serviceaccount needs view permissions to all namespaces
